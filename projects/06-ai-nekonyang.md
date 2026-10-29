# 06. AI 네코냥봇 — OpenAI API 연동 실습

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 학습 프로젝트  
**기술:** Python · Streamlit · OpenAI API  
**원본:** [sukwon2000k/ai-chatbot](https://github.com/sukwon2000k/ai-chatbot)

Streamlit 채팅 UI에 OpenAI API 호출을 연결하고, 캐릭터 역할 지침 및 세션별 채팅 기록을 구현한 학습 프로젝트입니다.

## 학습 목표와 현재 범위

캐릭터 역할 지침을 가진 AI를 채팅 화면과 연결하고, 입력→API 요청→응답 표시의 기본 흐름을 익히는 실습입니다. 세션의 대화는 화면에 누적 표시하지만, 현재 API 호출에는 사용자의 최신 질문만 전달합니다.

핵심 코드: [ai_chatbot.py](https://github.com/sukwon2000k/ai-chatbot/blob/main/ai_chatbot.py)

## 향후 개선 계획

- 이전 대화를 API 요청에 전달하고 대화 길이에 따른 토큰 관리 방식 추가
- API 키 미설정·연결 실패·요청 제한 상황에 대한 예외 처리와 화면 안내 보강

학습 확장 과제이며 업데이트 일정은 미정입니다. 기본 API 연동 실습으로 소개합니다.
