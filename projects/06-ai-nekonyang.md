# 06. AI 네코냥봇 — OpenAI API 연동 실습

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 학습 프로젝트  
**기술:** Python · Streamlit · OpenAI API  
**원본:** [sukwon2000k/ai-chatbot](https://github.com/sukwon2000k/ai-chatbot)

Streamlit 채팅 UI에 OpenAI API 호출을 연결하고, 캐릭터 역할 지침 및 세션별 채팅 기록을 구현한 학습 프로젝트입니다.

세션의 대화는 화면에 누적 표시하지만, 현재 API 호출에는 사용자의 최신 질문만 전달합니다. 이전 대화 전체를 이해하는 대화 메모리로 표현하지 않습니다.

핵심 코드: [ai_chatbot.py](https://github.com/sukwon2000k/ai-chatbot/blob/main/ai_chatbot.py)

> 단일 파일에 기능이 집중된 기본 API 연동 실습으로, 대표 백엔드 프로젝트보다는 학습 이력으로 소개합니다.
