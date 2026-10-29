# 03. SQLD AI Tutor — 교사형 학습 챗봇

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 프로젝트  
**기술:** Python · Streamlit · LangChain · Chroma · OpenAI API  
**코드:** [streamlitchatbot](https://github.com/sukwon2000k/streamlitchatbot) · [초기 개발판 chatbot](https://github.com/sukwon2000k/chatbot)

## 한눈에 보기

SQLD 자격증 학습을 돕기 위한 질의응답·개념 검색·연습문제 출제 및 채점 서비스입니다.

## 프로젝트의 목표

SQLD 학습에서 개념 검색, 문제 풀이, 채점, 약점 확인을 하나의 흐름으로 연결하는 것이 목표입니다. 검색 근거를 활용하는 설명과 학습 기록을 연결해, 다음에 복습할 단원을 확인할 수 있도록 구성했습니다.

## 코드로 확인한 기능

- RAG 자료를 Chroma에 임베딩하고 유사도 검색
- 벡터 검색이 어려울 때 키워드 검색으로 폴백
- 과목·단원·난이도별 문제 추출과 답안 채점
- 문제 풀이 기록, 중복 채점 방지, 약점 단원 집계
- LangChain Agent와 기능별 Tool 호출
- 방문자별 학습 상태 파일 분리 및 세션별 LLM 사용량 제한
- unittest 기반 로직 테스트

## 확인할 코드

- [RAG 서비스](https://github.com/sukwon2000k/streamlitchatbot/blob/main/src/rag_service.py)
- [문제 출제·채점](https://github.com/sukwon2000k/streamlitchatbot/blob/main/src/quiz_service.py)
- [학습 상태 기록](https://github.com/sukwon2000k/streamlitchatbot/blob/main/src/memory_service.py)
- [Agent 연동](https://github.com/sukwon2000k/streamlitchatbot/blob/main/src/agent_service.py)
- [단위 테스트](https://github.com/sukwon2000k/streamlitchatbot/blob/main/tests/test_core.py)

## 향후 개선 계획

- **검색 평가:** 고정된 질문과 기대 근거를 마련해 검색 결과 및 키워드 폴백 품질 평가
- **학습 기록:** JSON 파일 기반 저장을 보완해 재시작·동시 저장 시의 기록 유지와 일관성 강화
- **구조·검증:** UI와 제어 흐름의 역할 분리 및 검색→문제→채점 흐름의 통합 테스트 보강
- **자료 관리:** 문제은행의 공개 범위와 정답 접근 경계 점검

후속 개선 과제이며 업데이트 일정은 미정입니다. 초기 버전과 클라우드 배포용 버전은 하나의 프로젝트로 정리했습니다.
