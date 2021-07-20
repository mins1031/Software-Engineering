# Software-Engineering
## 클린코드
좋은 코드는 그냥 돌아가기만 하는것이 아닌 코드 그 자체로 설명이 다되는 코드이다.
팀원들과 프로젝트를 진행한다면 내가 구현한 코드를 보기만해도 어떤기능이 어떻게 동작하는지 읽기만해도 이해가 되고 또 혼자 프로젝트를 진행한다면 3,4개월, 그보다 더 늦게 코드를 다시 봤을때도 코드에 대해 이해가 되는 이런 것들이 이상적인 코드이고 이상적 클린코드라고 할 수 있다. 협업에서 큰 효과와 의미를 가질 것으로 생각한다.
> 클린코드의 대표적 규칙
 * 1) 검색 가능한 네이밍 사용 : 예를들어 서버의 토큰을 위한 시크릿코드나 24시간을 초로 환산한 값등을 그냥 raw값으로 사용하면 다른 사람이 봤을때 이 숫자가 무엇을 의미하는지 모를수 있고 개인적인 생각으로는 value가 safe하지도 않기 때문에 항상 value에 대한 이름을 적용하는것이 좋다
 * 2) 함수(메서드)명은 동사를 사용 : 오랜 관습이기도 한 내용이다. 함수명이 userData 와 loadUserData를 비교했을때 딱 보아도 loadUserData가 훨씬 직관적이고 알기쉽다.그리고 이렇게 네이밍하다보면 함수가 하는 역할에 선을 긋는 기준을 만들어 준다.
 * 3) 함수가 가지는 파라미터 수 : 함수의 파라미터가 너무 많다면 팀원이 봤을때 어떤 인수가 어떤 역할을 하는지 혼란스러울 수 있기에 함수가 많은 파라미터를 요구한다면 하나의 Dto로 묶는것이 효울적이다.
 * 4) boolean 값을 파라미터로 하는것을 지양하자 : 파라미터가 boolean값이라는 것은 함수내에 if분기문이 있다는 것을 의미하고 이것은 함수가 두가지 역할을 할 수 있다는 것을 의미한다. 다만 이건 함수의 역할에 따라 달라질것 같기도 하다.
 * 5) 짧은 변수명이나 축약어 쓰는것을 피하자 : user를 u로 eamil을 e로 하는 등의 행위를 말한다.
## 리펙토링 
프로그램의 결과는 그대로 유지한채 내부의 코드를 정리하며 개선하는 것을 '리팩토링'이라고 한다.
더 안정적이고 튼튼한 구조로 만들려는 노력으로 이해하면 되는데 코드의 가독성을 높히고 향후의 유지보수에 큰 도움이 된다.
> 리펙토링이 필요한 요소
 * 중복 코드
 * 긴 메서드
 * 거대한 클래스
 * Switch-case문 지양
## 클린코드와 리펙토링 정리
클린코드는 어찌보면 협업을 하는 데에 친절한? 코드라고 할 수 있을것 같다. 개인적으로는 클린코드의 규칙들을 숙지하고 대표적인 것들만 지키면서 코딩하는것이 나중에 바꾸는것 보다 훨씬 효율적이라고 생각한다.(경험담..)
리펙토링의 경우 결과를 만들고 개선해나가는 것이 지만 클린코드는 뭔가 관습하면 유용한 편? 이라는 생각이든다.
+ 수정과 추가 예정.

## 서버사이드 렌더링
 * static sites : 서버에서 html파일을 응답받는 형식. 이벤트 하나하나 마다 서버에서 html파일을 받아와야 해서 실용성이 굉장히 떨어짐.
 * SPA(single page application) : 사용자는 하나의 페이지에만 머물며 비동기 통신을 활용해 이벤트를 업데이트하는 형식의 페이지 
 * CSR(client side rendering) : 비동기 통신이 발달하고 javascrpit가 널리,견고히 쓰이게 되면서 React,vue와 같은 프레임워크가 출현했다. 
   * CSR은 처음 사용자가 접근하면 html파일 하나만 응답하는데 이 파일안에 필요한 js파일이 명시되어있고 이 js 파일을 다시 서버에서 응답 받아야 하는데 이 js파일에 어플리케이션에서 필요한 로직뿐만 아니라 어플을 구동하는 프레임워크나 라이브러리의 소스코드도 있어 파일의 크기가 크다. 데이터가 필요한 경우 서버에서 전달받아 원하는 기능을 구현했다. 
   * 다만 CSR의 단점은 1) 사용자가 첫 화면을 보기까지 시간이 오래 걸릴수 있다는 점과 2) 낮은 SEO 꼽을 수 있다. 낮은 SEO는 검색엔진으로 조회시 CSR페이지의 경우 바디가 비어있기떄문에 좋은 검색이 되지 않는 문제라고 한다.
 * SSR(server side rendering) : 웹 사이트에 접속하면 서버에서 필요한 데이터를 모두 가져와 html파일을 만들게 되고 이 html을 동적으로 만들어주는 js소스 코드를 같이 응답해주게 된다
   * SSR은 CSR보다 빠르게 첫 페이지를 사용자에게 보여줄수 있고
   * 모든 컨탠츠가 html에 담겨 있기 때문에 높은 SEO를 자랑한다.
   * 다만 SSR은 1) static sites에서의 문제인 정적인 요소가 많아 실용성이 떨어지고, 2) 서버에 과부하가 걸리기 쉽다는 단점과, 3)사용자가 빠르게 html파일을 확인 할 수 있지만 js파일을 아직 다운받지 못해서 이벤트가 발생하지 않는경우도 생긴다고 한다.
     * + TTV,TTI

## CI/CD
> CI/CD란
  * CI/CD란 각각의 개발자들이 개발을 하는 개발 환경을 사용자가 사용 가능한 서비스로 전달하는 모든 과정을 지속 가능한 형태로 또 가능하다면 자동으로해서 개발자와 사용자 사이의 격차를 없애는 것이다. 
  * 이러한 과정엔 코드를 빌드하고 -> 테스트하고 -> 배포하는 과정이 있다.
  * CI/CD 적용시 테스트과정이 있기 떄문에 코드가 CI에 성공하면 테스트를 거친 코드라는 신뢰가 있다. 
 
 ### Jenkins
 > Jenkins란?
  * Jenkins는 java Runtime위에서 동작하는 자동화 서버이다. 빌드,테스트,배포 등 모든 것을 자동화 해주는 자동화 서버이다.
 > Jenkins의 특징
  * JRE 환경에서 동작한다
  * 다양한 플러그 인들을 활용해서 각종 자동화 작업을 처리할 수 있다
  * 일련의 자동화 작업의 순서들의 집합인 Pipeline을 통해 CI/CD 파이프라인을 구축한다
 > Jenkins의 플러그인
  * 많은 플러그인이 존재하는데 대표적인 플러그인은 아래와 같다
    * Credentials Plugin
     * Jenkins는 그냥 단지 서버일 뿐이기에 배포에 필요한 각종 리소스(클라우드 리소스,ssh접근등)에 접근하기 위해서는 여러가지 중요 정보들을 저장하고 있어야 한다. 
     * AWS token, Git access token등 과 같은 중요한 정보를 저장해주는 플러그인.
    * Git Plugin
    * Pipeline : 젠킨스의 핵심기능인 파이프라인을 관리할 수 있게 해주는 플러그인이다.
    * Docker plugin and Docker Pipeline : 도커 agent를 사용하고 젠킨스에서 도커를 사용하기 위한 플러그인이다.
   > Pipeline
     * 파이프라인이란 CI/CD 파이프라인을 젠킨스에 구현하기 위한 일련의 플러그인들의 집합이자 구성. 
  
        
