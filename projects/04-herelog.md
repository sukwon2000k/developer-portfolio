# 04. HereLog — 위치 기반 기록 공유

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 프로젝트  
**기술:** PHP · MySQL · JavaScript · Kakao Maps API  
**코드:** [herelog_solution](https://github.com/sukwon2000k/herelog_solution) · [초기 화면 HereLog](https://github.com/sukwon2000k/HereLog)

## 한눈에 보기

방을 생성·초대하고 방별 게시글과 위치 정보를 공유하는 웹 프로젝트입니다.

## 프로젝트의 목표

함께하는 사람들의 기록을 방 단위로 모으고, 게시글을 위치 정보와 연결해 지도에서도 살펴볼 수 있도록 구성한 프로젝트입니다. 기록과 장소의 연결을 방별 멤버 권한 및 관계 데이터 저장으로 구현했습니다.

## 코드로 확인한 기능

- 회원가입·로그인과 비밀번호 해시 검증
- 방 코드로 참여, 방 소유자/멤버 역할과 접근 제어
- 방별 게시글·위치 마커의 연관 데이터 저장
- MySQL Prepared Statement를 이용한 다수 데이터 처리
- 게시글과 지도 마커를 함께 저장할 때 트랜잭션 사용
- Kakao Maps 역지오코딩 및 가까운 장소 탐색

## 코드 확인

- [회원가입](https://github.com/sukwon2000k/herelog_solution/blob/main/board/signup.php)
- [로그인](https://github.com/sukwon2000k/herelog_solution/blob/main/board/login.php)
- [방 권한 및 멤버 처리](https://github.com/sukwon2000k/herelog_solution/blob/main/config/room.php)
- [게시글·위치 저장](https://github.com/sukwon2000k/herelog_solution/blob/main/board/create_post.php)
- [지도 연동](https://github.com/sukwon2000k/herelog_solution/blob/main/js/post.js)

## 현재 검토 범위

인증·방 권한·게시글 저장 코드를 검토했습니다. 앱 전체의 실행 및 채팅 기능의 동작 검증은 별도 과제입니다.

## 향후 개선 계획

- **업로드 검증:** 프로필 이미지의 파일 형식·크기 검증과 안전한 저장 방식 보강
- **인증·권한:** 로그인 후 세션 갱신, 요청 위조 방어, 다른 방의 기록 접근 차단 점검
- **실패 처리:** 파일 저장 후 DB 저장이 실패하는 상황에서 파일 정리 및 일관성 확보
- **실행 검증:** 가입→방 참여→기록·마커 저장의 핵심 흐름과 채팅 기능 확인

후속 개선 과제이며 업데이트 일정은 미정입니다. 구현·검증을 완료한 항목부터 반영할 예정입니다.
