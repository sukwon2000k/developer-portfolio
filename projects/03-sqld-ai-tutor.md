# 03. SQLD AI Tutor — 교사형 학습 챗봇

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 프로젝트  
**기술:** Python · Streamlit · LangChain · Chroma · OpenAI API  
**코드:** [streamlitchatbot](https://github.com/sukwon2000k/streamlitchatbot) · [초기 개발판 chatbot](https://github.com/sukwon2000k/chatbot)

## 한눈에 보기

SQLD 자격증 학습을 돕기 위한 질의응답·개념 검색·연습문제 출제 및 채점 서비스입니다.

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

## 보완점

- Streamlit 앱에 UI와 제어 흐름이 집중된 구조 개선
- 검색 정확도 및 종단 간 테스트 보강
- JSON 파일 기반 상태 관리의 내구성·동시성 한계
- 문제·정답을 앱 내부에서 나누는 구조와 공개 저장소의 자료 접근 권한은 별개이므로, 문제은행 공개 범위 점검 필요

> 초기 버전과 클라우드 배포용 버전은 별도 작품으로 부풀리지 않고 하나의 프로젝트로 소개합니다.
