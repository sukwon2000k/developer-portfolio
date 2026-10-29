# 02. ReturnCheck — 환불·취소 판단 지원 웹앱

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 프로젝트  
**기술:** JavaScript · Netlify Functions · OpenAI API · Netlify Database  
**원본:** [mbca_academy_ALL/과제/returncheck-production](https://github.com/sukwon2000k/mbca_academy_ALL/tree/main/%EA%B3%BC%EC%A0%9C/returncheck-production)

## 한눈에 보기

예약·구매 정보와 환불정책을 분석해 예상 환불액, 시점별 변화, 준비물과 공식 절차를 정리하는 웹앱입니다.

## 구현 내용

- 영수증·예약확인서 등 이미지/PDF의 예약정보 추출 흐름
- 공식 환불정책 검색·구조화 및 출처 URL 처리
- **AI가 구조화한 정책과 별개로 동작하는 JavaScript 환불 계산 엔진**
- 정책 캐시, API 요청 제한, 사용량 기록 및 예외 처리
- 입력값·첨부파일 형식·날짜·URL 검증
- Node.js 테스트 코드

## 핵심 코드

- [환불액 계산 엔진](https://github.com/sukwon2000k/mbca_academy_ALL/blob/main/%EA%B3%BC%EC%A0%9C/returncheck-production/shared/refund-engine.mjs)
- [서버리스 분석 API](https://github.com/sukwon2000k/mbca_academy_ALL/blob/main/%EA%B3%BC%EC%A0%9C/returncheck-production/netlify/functions/analyze-refund.mjs)
- [입력값 검증](https://github.com/sukwon2000k/mbca_academy_ALL/blob/main/%EA%B3%BC%EC%A0%9C/returncheck-production/shared/validation.mjs)
- [환불 계산 테스트](https://github.com/sukwon2000k/mbca_academy_ALL/blob/main/%EA%B3%BC%EC%A0%9C/returncheck-production/tests/refund-engine.test.mjs)
- [프로젝트 README](https://github.com/sukwon2000k/mbca_academy_ALL/blob/main/%EA%B3%BC%EC%A0%9C/returncheck-production/README.md)

## 기술적으로 강조할 점

| 처리 단계 | 책임 |
|---|---|
| 입력·검증 | 금액, 날짜, 정책 URL, 첨부파일 형식·크기 검증 |
| 문서 추출·정책 처리 | OpenAI API로 입력 정보를 추출하고 정책을 구조화 |
| 정규화·계산 | 정책 구조를 정리한 뒤 `buildRefundResult`에서 규칙별 예상액 계산 |
| 응답 | 현재 예상액, 시점별 금액, 다음 감소 시점과 출처·주의 문구 제공 |

`analyze-refund.mjs`는 POST 요청을 받아 검증 → 캐시 조회 또는 AI 분석 → 정규화 → 금액 계산 → JSON 응답 순서로 처리합니다. AI 분석에 실패하면 조건에 맞는 이전 캐시를 찾아 대체 응답하고, 오래된 정책을 사용했다는 안내를 포함합니다.

요청 제한 설정과 일일 사용량 기록도 구성했습니다. 배포 플랫폼·DB 설정에 따라 적용 여부가 달라지므로 실제 운영에서 제한이 보장된다고 단정하지 않습니다.

자연어로 된 정책을 AI가 정리하더라도, 실제 금액 계산은 별도의 규칙 기반 함수에서 수행하도록 분리했습니다. 날짜 구간·환불 비율·고정 수수료·환불불가 금액을 계산하고 환불액이 줄어드는 다음 시점을 탐색합니다.

### 원본 테스트가 다루는 사례

환불 엔진 테스트에는 날짜 구간별 현재 환불액, 다음 감소 시점, 고정 수수료, 적용할 정책이 없는 경우가 포함돼 있습니다. 테스트 코드의 존재와 내용을 확인했으며, 이번 문서 정리에서 원본 앱의 전체 테스트나 외부 API를 실행한 것은 아닙니다.

## 한계와 향후 개선

- 정책 구조화 결과의 정확성은 공식 출처 확인 필요
- 정책 URL 보안, SSRF 방어, 장애 시 사용자 고지 방식 추가 점검
- 배포 환경에서 실제 API·DB 연동 E2E 검증 필요
- 독립 저장소로 분리하면 채용 담당자가 탐색하기 쉬움

> 실제 환불 가능 여부와 최종 금액을 보장하는 서비스로 표현하지 않습니다.
