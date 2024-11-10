# PROJECT INTRODUCTION

Web CHATTY 프로젝트는 웹소켓 및 메시지 브로커 기술 스택을 활용하여 슬랙과 디스코드 등의 웹 메신저 기능을 모방한 웹 서비스를 만들고자 시작한 프로젝트 입니다. 워크 스페이스 생성, 채널 생성, 채널 내 그룹 채팅, 프로필 관리 등의 서비스 구현을 본 프로젝트의 주 목표로 하였습니다.

# PROFILE

| 이름       | 역할         | GitHub                                      | 주요 기여 내용            |
|------------|--------------|---------------------------------------------|---------------------------|
| 오수현     | BACKEND  | [github.com/ohsuhyeon0119](https://github.com/ohsuhyeon0119) | 주요 API 개발, CICD 자동화 구축  |
| 김정한     | BACKEND | [github.com/Han-Jeong](https://github.com/Han-Jeong) |  주요 API 개발, DB 설계, 웹소켓 채팅 기능 주도 개발 |
| 김승현     | FRONTEND  | [github.com/ksh200070](https://github.com/ksh200070) | 리액트를 이용한 웹 프론트 개발 |
| 오세영     | PM & DESIGN       |[github.com/driffe](https://github.com/driffe) |  피그마 디자인 및 개발 일정 관리 주도   |



# 개발 과정

### 1. FIGMA FLOW CHART 1차 고안
SLACK과 DISCORD의 디자인을 차용하여 WEB CHATTY 웹 서비스의 구성을 일차적으로 설계해보았습니다.


| LANDING PAGE DESIGN                                       |  CHANNEL DESIGN                                         | USER PROFILE PAGE DESIGN                                          |
|---------------------------------------------------|---------------------------------------------------|---------------------------------------------------|
| <img src="https://github.com/user-attachments/assets/10a12a6c-08ce-4429-9960-a4643482f171" alt="LANDING PAGE DESIGN" width="350"/><br>회원가입 및 로그인 기능을 담은 랜딩 페이지 디자인 | <img src="https://github.com/user-attachments/assets/03994d19-1af3-4fa3-b390-9df26b227a34" alt="CHANNEL DESIGN" width="350"/><br> 채널 생성 및 채널 내 메신저 기능 디자인 | <img src="https://github.com/user-attachments/assets/9dc2a447-b439-438a-82a1-ebae88a41089" alt="PROFILE DESIGN" width="350"/><br>회원 프로필 기능 디자인 |


### 2. 세부 기능 선정
1차 피그마 디자인 이후 회의를 거쳐 세부 기능을 선정하였습니다. 

#### 워크스페이스 관리
워크스페이스의 생성 및 관리 : 유저는 워크스페이스를 생성할 수 있으며, 각 워크스페이스는 독립된 채널 및 다른 유저들의 관리 기능을 포함합니다. 여러 유저들은 하나의 워크스페이스 내에서 협업할 수 있습니다.

워크스페이스 초대 : 워크스페이스 소유자가 초대 링크를 통해 다른 유저를 초대할 수 있습니다. 초대 링크는 소유자가 갱신할 수 있습니다.

계층별 권한 : 워크스페이스의 소유자인 OWNER와 워크스페이스의 단순 참여자 USER를 분리하여 API에 대한 권한을 분리하고자 하였습니다.

#### 채널  관리
채널 생성 및 관리: 워크스페이스 내에서 다양한 용도의 채널을 생성할 수 있습니다. 각 채널은 주제를 기반으로 한 그룹 채팅이 가능합니다.

#### 웹 메신저 기능
실시간 메시지 전달: 웹소켓을 통해 채널에서 실시간으로 메시지를 주고 받을 수 있습니다.

메시지 저장 및 조회: 이전 대화 내역을 저장하고 채팅 내용은 추후에도 확인할 수 있습니다.

#### 회원 기능 및 유저 프로필
회원 가입 및 로그인: 사용자 계정 생성 및 인증을 통해 각 사용자가 독립된 프로필과 권한을 유지할 수 있습니다. 깃허브 및 구글 소셜 로그인 기능을 포함하였습니다.

프로필 관리: 사용자가 자신의 프로필을 업데이트하고, 워크스페이스 내에서 보여지는 이름, 소개글 등의 정보들을 수정할 수 있는 기능을 제공합니다.




### 3. 최종 FLOW CHART 완성
세부 기능을 선정한 이후 최종적인 웹서비스 디자인을 완성하였습니다.


| LANDING PAGE DESIGN                                       | WORKSPACE HOME DESIGN                                       | WORKSPACE AND CHANEL SETTING DESIGN                                       | USER PROFILE DESIGN                                       |
|-----------------------------------------------------------|--------------------------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|
| <img src="https://github.com/user-attachments/assets/47170205-cdfe-4b17-9e94-f5ee95ebdb92" alt="LANDING PAGE DESIGN" width="400"/><br>회원가입 및 로그인 기능을 담은 랜딩 페이지 디자인 | <img src="https://github.com/user-attachments/assets/3c50b6a5-6fd0-470b-ab9c-171097537c97" alt="WORKSPACE HOME DESIGN" width="400"/><br>워크스페이스 입장 시 디자인 | <img src="https://github.com/user-attachments/assets/8b26c71d-2a20-4d78-918d-e94aa103c8be" alt="WORKSPACE AND CHANEL SETTING DESIGN" width="400"/><br>워크스페이스 및 채널 SETTING 디자인 | <img src="https://github.com/user-attachments/assets/f123ae37-7a8b-453f-8b19-01864ce8a683" alt="SETTINGS DESIGN" width="400"/><br>사용자 설정 페이지 디자인 |


### 4. 기능 개발
FRONTEND 와 BACKEND가 협업하여 주요 기능 개발을 완료하였습니다. 기본적인 CRUD를 우선적으로 구현하였으며, 이후 소셜 로그인, 계층별 권한 기능을 추가하였습니다. 마지막으로 채팅 기능 개발을 위해 FRONTEND는 SockJS 등의 라이브러리, BACKEND는 RABBITMQ, STOMP PROTOCOL 등의 기술 스택을 학습한 뒤 개발을 진행하였습니다. FRONTEND와 BACKEND의 기술 스택 및 세부 개발 내용에 대해 궁금하다면 다음을 참조해주세요.

[chatty-server repo](https://github.com/project-web-chatty/chatty-server)

[chatty-front rep](https://github.com/project-web-chatty/chatty-web)

