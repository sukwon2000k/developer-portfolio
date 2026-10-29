# 04. HereLog — 위치 기반 기록 공유

[← 포트폴리오](../README.md) · [원본 저장소 안내](../REPOSITORIES.md)

**형태:** 개인 프로젝트  
**기술:** PHP · MySQL · JavaScript · Kakao Maps API  
**코드:** [herelog_solution](https://github.com/sukwon2000k/herelog_solution) · [초기 화면 HereLog](https://github.com/sukwon2000k/HereLog)

## 한눈에 보기

방을 생성·초대하고 방별 게시글과 위치 정보를 공유하는 웹 프로젝트입니다.

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

## 개선 필요 사항

회원가입의 프로필 이미지 업로드는 파일 형식·크기 검증을 보강할 여지가 있습니다. 세션 갱신, 요청 위조 방어, 파일 업로드와 DB 저장 실패 시 정리 방식도 추가 점검 대상입니다. 이번 문서에서는 인증·방 권한·게시글 저장 코드를 검토했으며 앱 전체의 실행 검증은 하지 않았습니다.

> 채팅 기능까지 안정적으로 완성되었다고 단정하지 않습니다.
