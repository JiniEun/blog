---
title: "Projects"
date: 2022-03-26T00:49:03+09:00
aliases : ["projects"] 
---

[Molog](#molog) (2022.02-) <br>

[MovieShelf](#movieshelf) (2022.02-) <br>

[Dongne](#dongne) (2021.11-12) <br>

[Shopping](#shopping) (2021.10) <br>

[Dipex](#dipex) (2019.09-11) <br>

---

## Molog

Kotlin, JPA, MySQL 기반 웹 프로젝트.

개인 블로그 주제의 웹 페이지입니다.


## MovieShelf

Java Spring Boot, Spring JPA, Oracle Cloud DB, React 기반 웹 프로젝트.
사용자들간에 영화 정보와 리뷰를 공유하는 웹 페이지입니다.

### Stack

Java, Spring Boot, Spring JPA, Oracle Cloud DB, React JS, AWS

### 구현 기능

- 회원 JPA를 이용한 CRUD
- 소셜 로그인 (구글, 카카오) 구현
- Swagger 적용
REST API 문서화 작업.
- TDD
- AWS 배포 경험


<br><br>

**Spring Boot와 JPA, Oracle Cloud DB로 구성한 백엔드와, React JS를 이용한 프론트엔드로 분리하여 개발한 팀 프로젝트를 통해 RESTful API 설계 및 개발 경험을 습득하고, TDD를 작성하며 TDD에 대한 학습과 단위 테스트 개발의 장점을 습득했습니다.**

<br><br>

---

## Shopping

쇼핑몰 형태의 웹페이지 제작 개인 프로젝트
Java Spring Boot, Bootstrap, Oracle Cloud DB 기반 웹 프로젝트

간단한 쇼핑몰 형태의 웹 페이지를 직접 구현해보는 개인 프로젝트를 진행했습니다. 
국비교육 시간에 진행된 스프링 교육 내용을 가지고 직접 실습하고 응용해보는 시간을 가지는 것에 의의를 두었습니다.

### 구현 기능

- 웹페이지 내의 로그인, 회원가입 기능
- 공지사항, 상품 게시판 CRUD
- 주문, 장바구니 기능 구현
- Oracle Cloud DB를 연결 운용 경험

### Issue

#### Oracle Cloud DB 연동

교육 내에서 Oracle DB 환경을 권장했으나, M1 Mac에서는 native 에서도, docker를 사용해도 2021년 당시 현재 오라클 데이터베이스를 m1 맥북에서 사용할 방법은 전혀 없는 Issue가 발생했습니다. ARM 64 칩셋으로 된 CPU에 Mac OS 사용이라는 특이한 상황에 오라클의 폐쇄성까지 겹쳐져 직접 오라클을 설치해 실행할 수 있는 방법이 없었습니다. 
따라서 Oracle Cloud Database를 직접 Oracle Cloud FreeTier 이용해 웹 어플리케이션에 연동하고 오라클 전자지갑 사용해 
프로젝트와 연결하는 작업을 수행하며 Issue를 해결했습니다.
필요 라이브러리 ojdbc8, ucp, oraclepki, osdt_cert, osdt_core 등의 jar 파일을 다운 받고 연동에 성공할 수 있었습니다.

#### 관리자 권한 제공

관리자 권한을 제공하기 위해 interceptor를 구현하고 grade로 권한을 구분하여 설정했습니다.
쇼핑몰 형태의 웹 페이지의 경우 블로그 형태의 웹과 다르게 다른 권한을 가지고 접근하여 다른 기능을 수행해야 하는 경우가 있기 때문에 (쇼핑몰 관리자와 방문자 간의 다른 접근 필요) 관리자 권한 기능을 제공할 수 있도록 구현했습니다.
상품 페이지 (등록, 수정, 삭제) / 공지 페이지 (등록, 수정, 삭제) / 회원 목록의 경우 admin 경로를 통해서만 들어갈 수 있도록 합니다.

#### Chatbot API

Naver에서 제공하는 (국비교육 내에서 사용할 수 있도록 제공) CLOVA Chatbot Custom API를 이용해 받아오는 형식으로
간단한 형태의 문의 화면을 구성했습니다.
네이버 챗봇 및 게이트웨이 API설정을 완료한 후 간단한 챗봇 질문들을 구성하고 연동해낼 수 있었습니다.

<br>

**Spring Boot와 jsp, Oracle Cloud DB기반의 개인 웹 프로젝트를 통해 Spring Framework를 이용한 백엔드 기초 역량을 습득했습니다.**

<br><br>

---

## Dongne

Java Spring Boot, JSP, Bootstrap, CSS, 
Naver Map API, AWS RDS 기반 웹 프로젝트입니다.


### 프로젝트 주제 및 목적

동네의 정보를 제공, 주민 간 정보를 공유할 수 있는 
종합 커뮤니티 웹을 제작했습니다.

내가 살고 있는 동네의 정보를 한 번에 확인하고,
사용자 간 동네의 실시간 정보를 빠르게 주고받을 수 있도록 합니다.
흩어져 있는 동네의 여러 정보들을 해당 종합 커뮤니티 웹 서비스를 통해 편리하게 접근하고,
같은 지역내의 사용자 간의 자유로운 정보 공유를 가능하도록 합니다.

### Stack

Java, Spring Boot, Oracle DB, JSP, Bootstrap, AWS

### 구현 기능

- 웹페이지 내의 로그인, 회원가입 기능
- 공지사항 게시판 CRUD
- Naver Map API를 이용한 지도 서비스 연결 및 위·경도, 주소 변환 작업
- Naver Clova Chatbot을 이용한 챗봇 서비스 연결
- AWS RDS Oracle DB 연동
- AWS EC2를 이용해 배포 진행 경험 (Naver Open API Issue 해결을 위해 현재 중단) 

➡️ 팀 내의 수석 프로그래머로, 전체적인 기능 수정, 디자인 수정, git 병합 등 총괄 역할 수행

### Issue

#### Map API

어떤 컴퓨터에서는 동작하고, 다른 컴퓨터에서는 작동하지 않는 경우 발생.
코드 구조가 정리되지 않아 간헐적으로 에러가 발생하는 문제

프로젝트 내의 구조에서 Java -> JSTL -> HTML -> Javascript 순서로 구동되는데, 
팀원분의 코드에서 JSTL 코드를 확인하고 동작하는 방향으로 수정했습니다.
기존에는 로딩 순서 때문에 지도 관련 함수가 제일 나중에 실행될 수 있도록 window.onload함수를 사용하고 있었으나, 
구동이 느리고 간헐적으로 동작하는 문제가 발생하여 제가 확인하고 JSTL의 c tag 안에서 모든 함수가 순서대로 동작할 수 있도록 처리하는 방향으로 변경했습니다. 제가 맡은 부분이 아니었으나 논의 끝에 성공적으로 코드를 수정했고,
코드 리뷰와 협업을 통해 프로젝트가 더 나은 방향으로 진행되는 것을 체감할 기회를 가지게 되었습니다.

#### 지역 정보 기능 제공

실시간으로 위치 정보를 가져오며 날씨 정보를 제공하는 부분을 Javascript에서 바로 위도와 경도, 그에 따라 날씨를 가져오는 방식으로 팀원분이 구현했습니다. 그런데 Dongne 프로젝트의 경우 위치 기반 서비스를 제공하기 위해 프로젝트 전반적으로 위치 정보가 필요했습니다.

따라서 이 부분을 인계받아, Javascript에서 java로 구현된 실시간 위치 정보 데이터를 전달받고, Naver ReverseGeocoding API를 이용해 이 위도, 경도를 행정 주소로 변환하였습니다. 이것을 지역 코드로 변환하고 session을 이용해 지역 정보를 다른 페이지들에서도 알 수 있도록 구현하는 방식으로 진행했습니다.

당시, 쿠키와 session 중에서 session을 선택했던 이유는 세션은 클라이언트별로 서버에 저장되는 정보이며, 사용자 컴퓨터에 저장되던 쿠키와 다르게 서버에 저장되므로, 비교적 보안이 필요한 데이터는 쿠키보다 세션에 저장한다는 것을 권장한다고 공부하기도 했고 세션도 서버가 종료되거나 유효시간이 지나면 사라지기 때문에 웹 페이지가 열려있는 동안 주소를 저장해도 된다고 판단했기 때문입니다.

<br>

**Spring Boot와 jsp, Naver Map API, AWS RDS를 이용한 팀 프로젝트를 통해 Open API 이용 경험과 AWS 배포를 통한 클라우드 개발 경험을 갖추었습니다.**

---


## Dipex 

2019-2 Capstone-Design

ReactJs와 Python의 Django, MySQL 기반의 웹 프로젝트입니다.
환자들의 질병 극복 사례 공유를 위한 비디오 플레이어를 포함한 웹 페이지를 제작했습니다.
지원 중단하게 된 Adobe flash 기반의 웹페이지를 최근 많이 사용되는 기술로 refactoring하여 페이지 구조를 개편하는 프로젝트였습니다.대용량의 DB 구조를 공부 하고 다뤄보는 경험을 하고, 실제 있던 웹 페이지의 구조를 파악하고 이것을 다른 프레 임워크를 이용해 개발해보며 웹 개발 능력을 갖추었습니다.

### Stack
HTML, CSS, Javascript, ReactJs, plyr, Python, Django, NGINX, MySQL, Amazon AWS

### Development Environment

![Environment](/images/Dipex2.png)

### 구현 기능

- 대용량의 Database를 인계받아 새로운 DB 설계 경험
- ReactJS를 통해 page 구성을 Component 단위로 분리하여 구현 
- 비디오 플레이어를 포함한 페이지 구현
- Semantic UI를 적용해 웹 프런트 style 구현

### Issue

#### Front-End Service 구조화

최근 현업에서 많이 사용 중인 ReactJS를 Front-End 개발환경으로 채택하였으며, 
이는 페이스북에서 개발한 것으로 사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JavaScript 라이브러리입니다.

기존 웹 개발은 HTML, CSS, JavaScript로 분리하여 작업했지만, 현대 웹에선 범위가 방대하며, 구조도 복잡하여 작은 단위로 분리하여 개발하게 되었습니다.

Webpack을 통해 Component 형태로 캡슐화하여 확장성, 결합성, 재사용성을 극대화하였고 Babel을 이용하여 JavaScript 확장 문법인 JSX 방식으로 
JavaScript 문법과 HTML 태그를 혼용하여 작성되어 졌으며, Virtual DOM을 통해 새로운 이벤트에 대한 업데이트를 보다 간결하고 쉽게 접근할 수 있게 해줍니다. 
ReactJS를 통해 Page 구성을 다음과 같이 Component 단위로 분리하여 이전보다 더 간편화 된 구조로 개편하였습니다.

**frontend 구현 담당이었지만, 의료 정보를 제공 하는 기능의 웹페이지를 제작하면서 사용자의 접근이 쉽고 직관적이어야 한다는 것을 깨닫는 시간을 가졌습니다.**
**그 후 백엔드 개발 시에도 프로젝트를 진행할 때마다 개발하고 있는 기능이 사용자에게 꼭 필요한 서비스인지, 접근성, 이용 가능성이 높은지, 사용자의 관점에서 생각하며 개발하려 노력합니다**

<br>

### React 장단점

<br>

### Final Result

- 개인정보 (환자 정보) 보호를 위한 데이터베이스 연동 해제로 내용은 확인 불가 
- 프런트 페이지 디자인만 조회 가능

https://roamgom.github.io/front_dipex/

---