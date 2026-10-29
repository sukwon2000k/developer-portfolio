<div align="center">

# 이석원

### Backend Developer Portfolio

**Python · FastAPI · JavaScript · SQL**

사용자의 요청을 API, 업무 규칙, 데이터 흐름으로 연결하는 신입 백엔드 개발자입니다.

[대표 프로젝트](#대표-프로젝트) · [기술 경험](#기술-경험) · [GitHub](https://github.com/sukwon2000k) · [원본 저장소 안내](REPOSITORIES.md)

</div>

---

## 소개

Python/FastAPI를 중심으로 백엔드 개발을 준비하고 있습니다. 팀 프로젝트에서는 경기 매칭과 커뮤니티 API를 개발하고 화면에 연결했으며, 개인 프로젝트에서는 외부 AI API 처리와 규칙 기반 계산 로직을 분리했습니다.

제가 프로젝트에서 중요하게 보는 것은 **사용자가 다음 행동까지 이어갈 수 있는가**입니다. PlayBridge에서는 동호회 가입보다 실제 경기 성사를 먼저 생각했고, ReturnCheck는 직접 겪은 환불 과정의 불편을 해결하려는 데서 출발했습니다. 이런 문제의식을 경기 신청·승인 흐름과 환불 판단을 돕는 기능으로 구체화했습니다.

- **관심 분야:** REST API, 권한·상태 검증, 데이터 처리, 외부 서비스 연동
- **교육:** MBCA AI+X 6개월 과정 수료
- **개발 경험:** 팀 기능 구현과 API 연동, 서버리스 API, SQL 기반 데이터 처리

## 대표 프로젝트

### 01 · PlayBridge

**생활체육 매칭 플랫폼 · 4인 팀 프로젝트**

경기를 함께할 상대팀을 찾고, 신청부터 운영진 승인·경기 확정까지 이어주는 서비스입니다.

| 구분 | 내용 |
|---|---|
| 주요 기술 | Python, FastAPI, React, Supabase / PostgreSQL |
| 본인 담당 | 팀 매칭·경기 후기·커뮤니티 백엔드와 화면 API 연동, 동호회 추천 입력·결과 흐름 연결 |
| 구현 포인트 | 운영진 권한과 신청·모집 상태 검증, 승인 후 일정 생성·상태 변경 연결 |
| 다음 개선 과제 | 동시 승인·중간 실패 상황의 데이터 정합성 및 자동화 테스트 강화 |

**[프로젝트 상세 →](projects/01-playbridge.md)** · [팀 원본 코드](https://github.com/mi2o2im8/DebugNet) · [본인 커밋](https://github.com/mi2o2im8/DebugNet/commits?author=sukwon2000k)

### 02 · ReturnCheck

**환불·취소 판단 지원 웹앱 · 개인 프로젝트**

예약·구매 정보와 환불 정책을 정리해 현재 예상 환불액, 금액이 줄어드는 시점, 준비물과 공식 절차를 안내합니다.

| 구분 | 내용 |
|---|---|
| 주요 기술 | JavaScript, Netlify Functions, OpenAI API, Netlify Database |
| 본인 담당 | 입력·문서 추출 흐름, 정책 분석 API, 환불 계산 엔진, 검증·캐시·테스트 구성 |
| 구현 포인트 | AI의 정책 구조화 결과를 정규화하고, 별도 JavaScript 함수로 금액 계산 |
| 함께 살펴볼 부분 | 입력 검증, API 요청 제한, 정책 캐시와 장애 시 대체 응답 |

**[프로젝트 상세 →](projects/02-returncheck.md)** · [원본 코드](https://github.com/sukwon2000k/mbca_academy_ALL/tree/main/%EA%B3%BC%EC%A0%9C/returncheck-production)

## 그 밖의 프로젝트

| 프로젝트 | 유형 | 주요 경험 | 상세 |
|---|---|---|---|
| **SQLD AI Tutor** | 개인 | RAG 검색, 문제 출제·채점, 학습 상태 관리 | [보기](projects/03-sqld-ai-tutor.md) |
| **HereLog** | 개인 | PHP/MySQL 인증, 방별 접근 권한, 게시글·위치 저장 | [보기](projects/04-herelog.md) |
| **부산 관광·상권 데이터 분석** | 팀 | 관광·상권 자료 전처리, 개인 분석 산출물 | [보기](projects/05-busan-analysis.md) |

<details>
<summary>학습·실습 프로젝트 보기</summary>

- [AI 네코냥봇](projects/06-ai-nekonyang.md): Streamlit 채팅 UI, OpenAI API 호출, 세션 기록
- [React 자유게시판](projects/07-react-board.md): React Router와 메모리 상태를 이용한 게시글·댓글 CRUD

</details>

## 기술 경험

숙련도 점수 대신 프로젝트에서 사용한 맥락을 정리했습니다.

| 영역 | 기술 | 사용 맥락 |
|---|---|---|
| Backend | Python, FastAPI | PlayBridge의 Router–Service–Repository 구성과 API 연동 |
| Serverless | JavaScript, Netlify Functions | ReturnCheck 분석 API와 외부 AI 서비스 호출 |
| Database | Supabase / PostgreSQL, MySQL | 경기·커뮤니티 데이터 접근, HereLog 관계 데이터 저장 |
| AI / Data | OpenAI API, LangChain, Chroma, Streamlit | 정책 구조화, SQLD 검색·학습 챗봇 |
| Frontend | React, Vite, JavaScript | API 요청·결과 표시, 추천 화면, CRUD 실습 |
| Collaboration / Deployment | Git, GitHub, AWS EC2, Nginx, Capacitor | 팀 협업, 배포 오류 대응, Android 패키징 참여 |

## 코드 탐색 가이드

| 확인하고 싶은 경험 | 추천 문서 |
|---|---|
| API의 권한·상태 검증과 업무 로직 | [PlayBridge](projects/01-playbridge.md) |
| AI 응답과 계산 로직의 분리 | [ReturnCheck](projects/02-returncheck.md) |
| 검색 폴백과 학습 상태 관리 | [SQLD AI Tutor](projects/03-sqld-ai-tutor.md) |
| 관계 데이터와 SQL 트랜잭션 | [HereLog](projects/04-herelog.md) |

---

이 저장소에는 소개 문서와 원본 코드 링크만 담았습니다. 팀 전체 기능과 개인 기여를 구분하고, 확인되지 않은 운영·성능 수치 및 수상 실적은 기재하지 않았습니다. 코드 검토 범위와 원본 위치는 [저장소 안내](REPOSITORIES.md)에서 확인할 수 있습니다.

각 상세 문서의 **향후 개선 계획**은 현재 구현과 구분한 후속 과제입니다. 업데이트 일정은 미정이며, 실제 반영과 검증을 마친 항목부터 문서에 갱신할 예정입니다.
