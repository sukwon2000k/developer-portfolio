# 01. PlayBridge — 생활체육 매칭 플랫폼

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 4인 팀 프로젝트  
**기술:** Python · FastAPI · React · Supabase · PostgreSQL · Capacitor  
**원본:** [mi2o2im8/DebugNet](https://github.com/mi2o2im8/DebugNet)

## 한눈에 보기

생활체육 이용자와 동호회가 상대팀을 탐색하고 경기 신청·승인, 커뮤니티 활동 등을 수행할 수 있도록 만든 팀 프로젝트입니다.

## 프로젝트를 만든 이유와 나의 관점

**동호회에 소속되는 것보다 실제로 운동하고 경기를 성사시키는 일을 먼저 돕고 싶었습니다.** 운동하려는 사람의 진입 장벽과 회원·경기 일정을 관리하는 운영진의 어려움을 나눠 살펴보고, 양쪽의 조건이 만나는 흐름을 서비스로 연결하고자 했습니다.

이 관점에서 제가 맡은 팀 매칭도 상대팀 목록을 보여주는 데서 끝내지 않고, 신청·운영진 승인·경기 일정 확정·후기로 이어지도록 구현했습니다. 가입이나 추천 결과가 실제 활동으로 이어지는 과정에 초점을 둔 프로젝트입니다.

## 내가 작업한 내용

| 범위 | 역할 |
|---|---|
| 팀 전체 서비스 | 회원·동호회 운영, 스포츠·동호회·경기 추천, 시설 탐색, 매칭, 커뮤니티 등 |
| 본인 중심 작업 | 팀 매칭·경기 후기·커뮤니티 API와 화면 연동, 동호회 추천 흐름 연결 |
| 협업·참여 | 모바일 화면 보정, Capacitor 패키징 및 배포 연동 대응 |

아래는 본인 작업 범위이며, 추천 모델·공공데이터·공통 인프라는 팀 전체 역할과 구분했습니다.

- **팀 매칭 백엔드:** 경기 가능 일정 등록, 팀 매칭 신청·승인/거절·취소, 경기 기록 및 후기 API 개발·연동
- **커뮤니티:** 게시글, 댓글, 차단 등 Router–Service–Repository–Schema 흐름과 화면 연동
- **추천 연결:** 조건 기반 Match Fit 추천을 API·화면 흐름과 연동; Club Fit 동호회 추천 입력·결과 화면 및 백엔드 연결
- **모바일·배포 연동:** React 화면·내비게이션 보정 및 Capacitor 안드로이드 패키징 작업 참여

개인 기여의 근거는 [내 계정의 팀 저장소 커밋](https://github.com/mi2o2im8/DebugNet/commits?author=sukwon2000k)과 해당 파일에서 확인할 수 있습니다.

## 핵심 구현 근거

- [매칭 API](https://github.com/mi2o2im8/DebugNet/blob/main/backend/app/routers/matches.py)
- [매칭 서비스/업무 규칙](https://github.com/mi2o2im8/DebugNet/blob/main/backend/app/services/match_service.py)
- [매칭 DB 접근](https://github.com/mi2o2im8/DebugNet/blob/main/backend/app/repositories/match_repository.py)
- [커뮤니티 게시글 서비스](https://github.com/mi2o2im8/DebugNet/blob/main/backend/app/services/post_service.py)
- [조건 기반 매칭 점수 계산](https://github.com/mi2o2im8/DebugNet/blob/main/backend/app/ml/match_fit.py)
- [팀 매칭 기능 초기 커밋](https://github.com/mi2o2im8/DebugNet/commit/299838e9344a)
- [커뮤니티 백엔드 연동 커밋](https://github.com/mi2o2im8/DebugNet/commit/87911f938b33)
- [Club Fit 추천/모바일 앱 연결 커밋](https://github.com/mi2o2im8/DebugNet/commit/db22c093c0fe)

## 설명 포인트

### 경기 승인을 처리하는 흐름

1. 요청자가 해당 동호회의 `owner` 또는 `manager`인지 검증합니다.
2. 신청을 받은 동호회인지, 신청이 `pending`인지, 경기 모집이 `open`인지 확인합니다.
3. 확정 경기 일정을 만들고 매칭 신청을 `approved`, 모집을 `matched`로 변경합니다.
4. 같은 모집에 남아 있는 다른 대기 신청을 거절하고 운영진 알림으로 연결합니다.

| 계층 | 담당 책임 |
|---|---|
| Router / Schema | API 경로, 인증 의존성, 요청·응답 데이터 형태 |
| Service | 권한·상태 검증, 경기 승인·취소·결과·후기 업무 흐름 |
| Repository | Supabase를 통한 조회·저장 |

### 실패 처리와 설계 한계

매칭 승인 시 운영진 권한·요청 상태·모집 상태 등을 검증하며, 승인 뒤 경기 일정 생성과 상태 변경 흐름을 연결했습니다. 현재는 Supabase에 여러 요청을 순차 수행하고 오류 시 일부 보상 처리를 시도하는 구조입니다. 여러 변경을 하나의 DB 트랜잭션으로 묶지 않아 중간 실패와 동시 요청에 대한 정합성 강화가 후속 과제입니다.

## 향후 개선 계획

- **데이터 정합성:** 매칭 승인에 필요한 여러 데이터 변경을 DB 트랜잭션으로 묶는 방안을 검토하고, 동일 모집에 대한 동시 승인·중복 요청 방어 강화
- **자동화 테스트:** 운영진 권한, 신청·모집 상태, 승인 중간 실패에 대한 테스트 보강
- **구조 개선:** 큰 매칭 서비스 파일을 신청·승인·결과·후기 등의 책임에 맞게 분리
- **시연 자료:** 이용자·운영자 흐름의 화면과 시연영상 정리 및 배포 상태 확인

후속 개선 과제이며 업데이트 일정은 미정입니다. 구현·검증을 완료한 항목부터 반영할 예정입니다.
