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
   * 파이프라인이란 CI/CD 파이프라인을 젠킨스에 구현하기 위한 일련의 플러그인들의 집합이자 구성이다.
   * 즉 여러 플러그인들을 이 파이프라인에서 용도에 맞게 사용하고 정의함으로써 파이프라인을 통해 서비스가 배포된다
   * 두가지 형태의 Pipeline syntax가 존재한다(Declarative, Scripted Pipeline).
   * Declarative가 더 최신이고 가독성이 좋다
   * Pipeline syntax는 아래의 Section으로 구성된다
      1) Agent section    
        * 젠킨스는 많은 일들을 해야 하기 때문에 혼자 하기 버겁다
        * 여러 slave node를 두고 일을 시킬수 있는데 이처럼 어떤 젠킨스가 일을 하게 할 것인지를 지정한다
        * 젠킨스의 노드 관리에서 새로 노드를 띄우거나 docker 이미지등을 통해서 처리할 수 있다
      2) Post section
        * 스테이지(밑의 3번)가 끈난 이후의 결과에 따라서 후속 조치를 취할 수 있다
        * ex) 성공시 성공 이메일전송, 실패하면 중단 등등
      3) Stages section
        * 어떤 일들을 처리할 건지 일련의 stage를 정의한다(yml파일의 형태와 비슷)
      4) Steps section
        * 한 스테이지 안에서의 단계로 일련의 스텝을 보여준다
        ```
        stages {
           stage('Prepare') {
              steps {
                 git url: "http://github.com/minair",
                     branch: 'master',
                     credentialsId: 'jenkinsgit'
                 sh 'ls'
                 dir ('./docs'){
                     sh '''
                     aws s3 sync ./ s3://namhoontest
                     '''
                 }
              }

              post {
                  success {
                     echo 'success'
                  }
              }
           }
           stage('Build') {
              steps {
                 echo 'Building...'
              }
           }
        }
        ```
        * Declaratives
         * Environment, stage, options, parameters, triggers, When 등의 Declarative가 있다.
         * Environment -> 어떤 pipeline이나 stage scope의 환경변수 설정
         * Parameter -> 파이프라인 실행시 파라미터 받음
         * Triggers -> 어떤 형태로 트리거 되는가
         * When -> 언제 실행되는가
     (잠시보류)


## 보안
 ### CIA
 > 보안의 3요소 기밀성, 무결성, 가용성의 첫글자를 딴 것이 CIA이다.
 * 기밀성 
   * 정보를 오직 인가된 사용자에게만 허가
   * 개인정보나 지적 재산권등 가치있는 정보
   * 기밀정보로 생각하면 된다고 한다.
 * 무결성
   * 부적절한 정보 변경이나 파기 없이 정확하고 완전하게 보존
 * 가용성
   * 시기적절하면서 신뢰할 수 있는 정보로 접근과 사용.
   * 구매한 아이폰을 1년 365일 그 언제라도 수리받고 사용할 수 있다면 가용성이 좋은 것이다.   
 
 만약 A,B,C나라가 있다고 하고 A는 B에게 C에겐 들켜선 안되는 기밀 문서를 보낸다.
 
 => 문서전달중 C에게 잡혀 문서를 보여버린다면 이것은 '기밀성'이 깨진것이고, C가 새로운 문서를 만들어서 B에 전달하면 이것은 '무결성'(문서에 변화가 생긴것)이 깨진것이다.그리고 B나라로 문서가 전달되는 순간 '가용성'이 깨진것이다.(원하는 문서에 접근을 하지 못해서) 위에선 열쇠를 어떻게 안전하게 전달할지에 대한 문제와 수신자가 누군지에 대한 인증문제가 남아있다.
 
 => 간단하게 A에서 문서를 보낼때 a열쇠로만 열리게 암호화 해서 보내더라도 상대도 a열쇠가 있어야 문서를 볼수 있는데 이 열쇠를 문서와 같이 전달하면 C에게 탈취될 가능성이 있기에 열쇠전달의 문제가있다. 또한 C가 문서를 탈취해 문서를 볼수는 없어도 새로운 문서를 B에게 보낼수 있기에 수신자에 대한 인증문제가 있다 
 
 ### RSA
 위의 두 문제를 해결할 수 있는 방안이 RSA이다.
 > RSA전 대칭키(Symmetric key)에 대해 조금 살펴보면 '암호화와 복호화에 같은 암호키(대칭키)를 사용하는 알고리즘'이다. 동일한 키를 주고받기 때문에 빠르다는 장점이 있지만 키 전달 과정에서 해킹 위험에 노출되는 단점이 있다.위의 내용이 대칭키에 관한 내용이다.
 
 * RSA는 '공개키'와 '개인키'를 가진다.
 * 만약 A가 B에게 '안녕' 이라는 데이터를 전달하고 싶다. 또한 A,B 둘다 각각의 공개키와 개인키를 가지고 있다.
 * 공개키는 블로그같은 오픈된 곳에 공개해도 상관없지만 개인키는 자신만 가지고 있어야 한다.
 * 해커가 해당 데이터를 가로채고 싶어한다.
 * A는 공개키로 데이터를 암호화 하고 전송한다 =? 공개키(안녕)
 * 여기서 전달하는 공개키는 B만이 열어볼수 있게 해야함으로 B의 공개키 여야 하고 해당 공개키는 B의 개인키로만 열수 있다.
 * 해커는 B의 개인키가 없음으로 데이터를 어찌하지 못한다
 * 여기서 공개키로 감싸는것을 '암호화', 키를 열어 보는 것을 '복호화'라고 한다. 
 * B역시 A에 데이터를 보낼때 A의 공개키로 암호화해서 보내면 된다.
 * 여기까진 위에서 '열쇠를 어떻게 안전하게 보낼까?'에대한 해결책이고 해당 데이터의 수신자에 대한 신뢰문제 즉 인증문제가 남아있다.
 * 인증 문제는 A가 B에게 '잘지내니?' 라는 데이터를 A의 개인키로 암호화해 전송하면 B는 A의 개인키로만 해당 데이터를 열어볼수 있다. 즉 A의 공개키로 열린다는 것은 A의 개인키로 잠겼다는 의미이므로 A가 보낸 데이터라는 신뢰가 생길수 있게 된다
 * 공개키 -> 개인키 : 공개키는 개인키로 열 수 있다.(공개키로 암호화된것은 개인키로 복호화 할수 있다). 암호화 를 의미한다
 * 개인키 -> 공개키 : 개인키는 공개키로 열 수 있다(개인키로 암호화된것은 공개키로 복호화 할수 있다). 주로 전자서명을 의미한다.
 * 결국 최종적 암호화는 A와 B가 통신시 데이터를 "B의 공개키로 잠군후 A의 개인키로" 잠군다라고 할때
   1) B에서 받을때 A의 공개키로 열리면? -> 인증됨, 열리지 않으면? -> 다른사람이 암호화 했으므로 인증실패
   2) 열리게 되면 B의 개인키로 열어 데이터를 확인한다.
   3) 위와 같은 방식은 '인증'도 되고 '안전한 데이터 전달'도 가능하다. 이것을 'RSA 방식'이라고 한다. 
 
 ### XSS
 > CSRF와 같이 웹 어플맄이션 취약점중 하나로 관리자가 아닌 권한 없는 사용자가 웹사이트에 스크립트를 삽입하는 공격 기법을 말한다.
 * 예를 들어 게시글 작성에서 text 타입의 input에 <script>alert("안녕 친구?")</script> 를 쓰고 저장한다면 서버는 그대로 코드를 디비에 저장하고 다른유저가 해당 게시글을 볼때 위의 script가 실행되어 alert이 실행된다 
 * 악의적으로 스크립트를 삽입하여 이를 열람한 사용자의 쿠키가 해커에게 전송되며 이 쿠키를 통해 세션 하이재킹 공격을 한다. 해커는 세션ID를 가진 쿠키로 사용자의 계정에 로그인이 가능해지는 것이다.
 * 공격 종류로는 대표적으로 밑과 같은 것들이 있다
   * 지속성 : 말 그대로 지속적으로 피해를 입히는 유형으로 악성 스크립트를 삽입하여 열람한 사용자의 쿠키를 탈취하거나 리다이렉션 시키는 공격을 한다. 이떄 삽입된 스크립트를 DB에 저장시켜 지속적으로 공격하기에 지속적 XSS로 불린다. =>  주로 댓글, 글쓰기 기능에서 발생
   * 반사형 : 사용자에게 입력받은 값을 서버에서 되돌려주는 곳에서 발생한다. 공격자는 악의 스크립트와 함께 URL을 사용자에게 누르도록 유도하고 누른 사용자는 이 스크립트가 실행되어 공격을 당하게 되는 유형이다
 > 방어 방법 => 주로 검색 기능에서 발생.
 * 입출력 값 검증 : XSS 필터를 만들어 '<'나 '>'등 XSS공격을 위해 들어가는 특수기호들을 필터링해 사전에 예방한다.
 * XSS 방어 라이브러리, 확장앱 : Anti XSS 라이브러리를 제공하는 회사가 많다. 이 라이브러리를 서버단에 추가하며 사용자는 각자 브라우저에서 악성 스크립트가 실행되지 않도록 확장앱을 설치하여 방어할수 있다
 * 웹 방화벽 : 웹 공격에 특화된 것으로 다양한 injection을 한꺼번에 방어할 수 있는 장점이 있다.
 
 ### CSRF
 > CSRF 공격이란 웹 어플리케이션 취약점 중 하나로 인터넷 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위(CRUD등)를 특정 웹사이트에 요청하게 만드는 공격이다
 * CSRF를 통해 해커는 사용자의 '권한'을 도용해 중요기능을 실행하는 것이 가능하다.
 * 대표적으로 평소에 페이스북 계정이 해킹당해 광고성 글을 올리는 지인들의 모습을 보았는데 이러한 경우가 CSRF공격에 당한 것이다.
 * 다만 사용자의 컴퓨터를 감염시키거나 서버를 해킹해서 이뤄지는 공격은 아니다.
 * CSRF 공격이 이루어 지려면 밑과 같은 조건이 만족되어야 한다.
   * 위조 요청을 전송하는 서비스에 사용자가 로그인한 상태
   * 사용자가 해커가 만든 피싱 사이트에 접속한 경우
 * 보통 위의 2개를 만족시키긴 어려워 보이지만 자동로그인 한 플랫폼의 경우 조건 충족이 쉬워 피해사례가 많다(페이스북이라던가..) 로그인이 되어있는 상태에서 해커가 만든 피싱사이트를 통해 접속하면 공격이 이뤄진다고 한다
 * 동작방식:
   * A사이트의 관리자가 A사이트에 관리자 권한으로 로그인 되어있고 유저의 권한을 변경할때 GET /changeUserAuth?id=programmer93&auth=ROLE_ADMIN ( programmer93의 권한을 admin으로 변경 ) 이러한 url을 사용한다고 하면
   * 해커가 사용자에게 무작위 이메일을 보낼때 해당 url이 적용된 img 태그를 추가한다.
   * 그럼 사용자가 url을 입력시 img태그의 src속성에 url이 적용되있어 위의 권한 변경 url이 실행되는데 현재 관리자 권한으로 사용자가 로그인 되어있기 떄문에 권한이 바뀌어 버리게 된다.
 > 방어 방법
 1) Referrer 검증 
   * back-end 단에서 request의 Header내의 referrer를 확인하여 도메인이 일치하는지 검증하는 방법이다.
   * 일반적으로 referrer검증 만으로 대부분의 csrf공격을 방어할 수 있지만 같은 도메인내의 페이지에 XSS취약점이 있는 경우 csrf공격에 취약해질수 있다.
 2) CSRF토큰
   * referrer 검증이 불가한 환경이면 Security Token을 활용할 수 있다.
   * spring의 spring security는 디폴트로 프론트 form태그에서 CSRF토큰을 만들어 함께 요청해야 한다.
   * 사용자의 세션에 임의의 난수값을 저장하고 사용자의 요청마다 해당 난수 값을 포함시켜 전송한다.
   * 이후 Back단에서 요청을 받을 떄 마다 세션에 저장된 토큰값과 요청 파라미터에 전달되는 토큰값이 일치하는지 검증한다.
   * 이 방법역시 같은 도메인내에 XSS 취약점이 있다면 CSRF공격에 역시 취약해진다.
 
 ### SQL Injection
 > 해커에 의해 조작된 SQL쿼리문이 DB에 그대로 전달되어 비정상적 명령을 실행시키는 공격 기법.
 
 > 공격방법
 1) 인증 우회
 보통 로그인을 할때 아이디와 비밀번호를 input창에 입력하게 된다. 만약 id가 min, pw가 1234일때 쿼리는 아래와 같이 DB에 질의 될것이다
 ```
 select * from member where member_id = 'min' and password = '1234'
 ```
 이때 SQL Injection으로 공격시 input창에 비밀번호를 입력함과 동시 다른 쿼리문을 함꼐 입력하면..?
 ```
 1234; delete * member from member_id = '1'
 ```
 보안이 허술한경우 id,pw가 일치되고 뒤의 delete문도 실행 되어 DB에 영향을 줄수 있는 치명적인 해킹이다.
 
 2) 데이터 노출
 시스템에서 발생하는 에러메세지를 이용해 공격하는 방법이다. 예를 들어 해커가 Get방식의 url에 쿼리스트링을 추가하여 에러를 발생시키고 해당하는 오류가 올라오면 이를 통해 어플리케이션의 DB구조를 유추하여 해킹에 활용한다.
 
 > 방어 방밥
 1) input 값을 받을 때 특수문자 여부 검사
 * 로그인전 또는 동작시 db에 쿼리가 질의되는 기능 전, 검증 로직을 추가하여 미리 설정한 특수문자들이 입력되었을때 요청을 막아낸다. 
 
 2) SQL 서버 오류 발생시 해당하는 에러 메세지 감추기
 * 에러 발생시 에러 페이지를 통해 정확한 에러 메세지가 view로 전달되는 것을 막아 예방한다.
 
 3) prepareStatement 사용하기
 * prepareStatement를 사용하면 특수문자를 자동으로 escaping 해준다.(전달인자를 ?로 받는것) 이를 활용해 서버에서 필터링 과정을 통해 공격을 방어 할 수 있다.   

## 인텔리제이 단축키 (윈도우 & Linux)
### 일반적 단축키
- ALt + 0~9 : 각 단축키에 해당하는 도구창 열기
  - ALt + 0 : 깃 커밋 및 푸시 도구창 열람 ***
  - ALt + 1 : 프로젝트 도구창 열람 **
  - ALt + 2 : favorites(처음 보는 창이긴한데 breakPoint 볼수 있다는 점이 장점인듯) 도구창 열람 *
  - ALt + 3 : 하단 Find 도구창 열람
  - ALt + 4 : 하단 Run 도구창 열람 *
  - ALt + 5 : 하단 Debug 도구창 열람 *
  - ALt + 6 : 하단 Problems 도구창 열람
  - ALt + 7 : structure 도구창 열람 * 
  - ALt + 8 : 하단 service 도구창 열람
  - ALt + 9 : 하단 git 도구창 열람 ****
- Ctrl + s : 모두저장
- Ctrl + shift + F12 : 편집기 영역을 최대 크기로 토글
- Ctrl + shift + I : 현재 프로필 기준으로 현재 파일검사
- Ctrl + Alt + S : 설정창(Setting) 열기 ***
- Ctrl + Alt + shift + S : 프로젝트 구조창(Project Structure) 열기 ***
### 디버깅 관련 단축키
- F8 : 현재 브레이크된 라인에서 다음라인으로 이동
- F7 : 현재 브레이크된 라인에서 실행하고 있는 메서드로 이동
- Shift + F8 : 브레이크된 라인에서 실행하고 있는 메소드로 이동
- Alt + F9 : 포커스 되어있는 라인으로 이동
- Alt + F8 : 브레이크된 라인에서 사용 가능한 모든 코드를 실행
- F9 : 다음 브레이크 포인트로 이동
### Search/Replace : 검색 및 대체 관련 단축키
- Shift * 2 : 전체 검색창열기(Alt + 방향키로 All, File,Symbol,Actions등 선택가능)**
- Ctrl + Shift + F : 문자열 검색창 열기 **
- Ctrl + F : 현재 파일에서 문자열 검색 **
- F3/Shift + F3 : 검색된 문자열로 이전/이후 이동
- Ctrl + R : 현재 파일에서 문자열 대체 **
### Editing : IDE 관련 단축키
- Ctrl + Space :  기본코드를 자동 완성
- Ctrl + Shift + Space : 소스코드를 분석해서 적합한 자동완성 코드를 추천
- Ctrl + Shift + Enter : 문장 자동 완성(if문, for문 등)
- Ctrl + P : 메서드의 파라미터 정보를 조회 (메서드 작성시 어떤 파라미터를 적용하는지 가물할때 사용하면 유용할듯하다)
- Ctrl + Q : 도큐먼트를 조회 (해당 파일의 어노테이션과 리턴타입, 파라미터등의 정보를 알려준다.)
- Ctrl + O : Override 가능한 메서드 목록을 확인하여 코드를 자동 생성 (네비게이터 바의 override의 단축키)
- Ctrl + I : Implement 가능한 메서드 목록을 확인하여 코드를 자동 생성
- Ctrl + / : 라인단위로 주석처리(//주석처리)
- Ctrl + Shift + / : 블록단위로 주석처리 (/* 주석처리 */)
- Ctrl + . : 블록 접기/열기
- Ctrl + W : 커서 근처의 코드 선택영역을 확대(마우스 더블클릭 단축키)
- Ctrl + Shift + W : 커서 근처의 코드 선택 영역을 코드에 맞게 축소
- Alt + Enter : 추가되지 않은 Import 추가
- Alt + Shift + Enter : 가로/세로 편집모드로 변경
- Ctrl + Alt + L : 코드 포맷팅
- Ctrl + Alt + O : import 정리(미사용 import 삭제)
- Ctrl + Alt + I : 들여쓰기 정렬
- Ctrl + Alt + Enter : 커서가 위치한 라인에 바로 위 라인에서 시작
- Ctrl + D : 커서가 위치한 라인을복사하여 바로 밑에 라인에 붙여넣기
- Ctrl + Y : 커서가 위치한 라인을 삭제
- Shift + Enter : 커서가 위치한 라인에 바로 아래 라인에서 시작
- Ctrl + Shift + U : 대/소문자 변경
- Ctrl + Shift + J : 라인 합치기
- Shift + alt : 선택된 블록 채로 옮길수 있다.
- Ctrl 두번쨰에서 손때지 않고 + 방향키 : 멀티커서로 여러 변수를 한번에 변경할 때 용이하다
- Ctrl + Alt + <--> : 이전커서가 있는 곳으로 이동하는 명령어.
- Ctrl + Alt + m : 드래그한 내용을 메소드로 전환해준다. ***

### Gradle
> 입사전까진 메이븐만 쓰면서 그레이들에 익숙치 않았는데 회사에선 그레이들을 자주 사용하는 바람에 익숙해졌습니다. 다만 정확한 동작원리나 개념은 부족하기에 기본내용 정리 용도로 적어 봅니다 
  #### Build Tool이란
  - gradle은 일종의 빌드도구(Build Tool) 입니다. 여기서 빌드라는 개념은 단순히 프로그램을 컴파일하여 어플리케이션을 생성하는 작업만을 의미하는 것이 아닙니다
  - 개발한 소프트웨어가 제품으로 만들어지는 일련의 과정 즉, 컴파일, 테스트, 배포, 문서화 등의 작업을 포함하는 절차를 의미 합니다. 이때 빌드의 모든 과정을 자동으로 처리할 수 있도록 도와주는 것을 빌드 도구(Build Tool)라고 합니다.
  #### Groovy, DSL 
  - gradle은 groovy라고 하는 JVM기반의 동적 타이핑 언어를 사용해서 기술됩니다. 
  - 그런데 gradle은 groovy 문법 그 자체를 그대로 사용하지는 않고 '그루비 기반의 DSL을 사용합니다.'
  - DSL은 도메인 고유 언어라고 불리는데 특정한 용도에 한정된 언어를 가리킵니다. 기반 언어가 있지만 그언어 자체는 아닌 특정용도에 맞게 해당 언어를 기반으로 각색된 것이라고 합니다.
  - gradle에 사용되는 언어는 groovy를 기반으로 작성도니 gradle DSL입니다.
  #### build.gradle
  > build.gradle은 gradle에서 빌드 작업에 필요한 기본 설정, 동작등을 정의하는 파일입니다. 아래는 인텔리제이에서 스프링 프로젝트를 생성하고 몇가지 의존성을 추가했을때의 기본 형태입ㄴ디ㅏ.
  ```
  plugins {
        id 'org.springframework.boot' version '2.3.1.RELEASE'
        id 'io.spring.dependency-management' version '1.0.9.RELEASE'
        id 'java'
    }
    
    group = 'com.example'
    version = '0.0.1-SNAPSHOT'
    sourceCompatibility = '1.8'

    configurations {
        compileOnly {
            extendsFrom annotationProcessor
        }
    }

    repositories {
        mavenCentral()
    }

    dependencies {
        implementation 'org.springframework.boot:spring-boot-starter-data-jdbc'
        implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
        implementation 'org.springframework.boot:spring-boot-starter-oauth2-client'
        implementation 'org.springframework.boot:spring-boot-starter-security'
        implementation 'org.springframework.boot:spring-boot-starter-web'
        implementation 'org.springframework.kafka:spring-kafka'
        compileOnly 'org.projectlombok:lombok'
        runtimeOnly 'com.h2database:h2'
        runtimeOnly 'mysql:mysql-connector-java'
        annotationProcessor 'org.projectlombok:lombok'
        testImplementation('org.springframework.boot:spring-boot-starter-test') {
            exclude group: 'org.junit.vintage', module: 'junit-vintage-engine'
        }
        testImplementation 'org.springframework.kafka:spring-kafka-test'
        testImplementation 'org.springframework.security:spring-security-test'
    }

    test {
        useJUnitPlatform()
    }
  ```
  * plugins 
    * 프로젝트를 빌드하기 위해서 여러가지 작업을 처리해줘야 합니다. 컴파일이나 jar파일 생성같은 작업들입니다.
    * 이런 작업들을 해주는 플러그인이 존재하고 plugins 블록안에 필요한 플러그 인을 지정해주고 이런 플러그인 들은 필요한 과정들을 task로 포함하고 있습니다. 
    * 그래서 빌드시 필요한 과정들을 플러그인들의 내부 task가 진행을 해주게 됩니다.
    * 따라서 빌드시에 필요한 플러그인들을 파악해 배치 시켜야 합니다.
  * repository
    * repository는 저장소 정보를 관리하는 프로퍼티입니다. 
    * 로컬 환겨이나 네트워크에 라이브러리를 공개하고 그 주소를 저장소로 등록하면 저장소에 있는 라이브러리를 그레이들이 취득하여 이용할수 있는 구조 입니다.
    * 위의 코드엔 mavenCentral() 이라는 메서드를 통해 중앙저장소를 이용할 수 있고 jCenter() 메서드를 통해 jCenter 저장소를 이용할 수도 있습니다.
    * 저장소는 각종 라이브러리등이 등록된 일종의 소프트웨어 보관 장소라고 할 수 있습니다. 저장소에는 각종 프로그램이 등록되있어 그레들은 저장소로 부터 필요하나 라이브러리를 다운로드 하여 이용할수 있습니다.
    * 만약 중앙저장소에 공개되지 않거나 공개가 힘든경우는 로컬 저장소를 이용하면 됩니다.
  * dependencies
    > Dependencies는 의존성에 관한 설정을 관리하는 프로퍼티 입니다. 여기에 필요한 라이브러리등의 정보를 기술하면 그 라이브러리를 참조할 수 있습니다. 
    - implementation: 컴파일시 implementation에 지정한 라이브러리에 접근할 수 있다는 명세입니다.
    - testImplementation: 테스트 컴파일시 testImplementation에 지정한 라이브러리에 접근할 수 있다는 명세입니다.
    - compileOnly : compileOnly로 명시된 라이브러리는 컴파일 시에만 사용한다는 의미입니다
    - runtimeOnly : runtimeOnly로 명시된 라이브러리는 런타임 시에만 사용한다는 의미입니다
  #### 멀티모듈일때 build.gradle
  ```
  buildscript {
    ext {
        springBootVersion = '2.1.3.RELEASE'
    }
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
        classpath "io.spring.gradle:dependency-management-plugin:1.0.6.RELEASE"
    }
}

allprojects {
    group 'com.example'
    version '1.0-SNAPSHOT'
}

subprojects {
    apply plugin: 'java'
    apply plugin: 'org.springframework.boot'
    apply plugin: 'io.spring.dependency-management'

    sourceCompatibility = 1.8

    repositories {
        mavenCentral()
    }

    dependencies {
        testCompile group: 'junit', name: 'junit', version: '4.12'
    }
}

project(':example') {
    dependencies {
        ....
    }
}

project(':sub-example') {
    dependencies {
        ...
    }
}
  ```
  * ext 
  > ext블록은 gradle의 모든 task에서 사용할 수 있는 일종의 전역변수를 선언하는 블록이라고 생각하면 됩니다
  
  * buildscript
  > buildscript 블록은 빌드하는 동안 필요한 처리를 모아놓는 곳입니다. 이안에 dependencies와 repositories가 포함 될수 있습니다.
  
  * setting.gradle
  > 그레들 파일중 setting.gradle이라는 파일이 있는데 여러가지로 사용할 수 있지만 대표적으로 멀티모듈 사용시에 설정파일로 사용된다
  ```
  rootProject.name = '임시명'
  include 'module-web'
  include 'module-core'
  include 'module-common'
  ```
    - 위처럼 루트 모듈을 설정하고 하위 모듈을 명시해줘야 멀티모듈에 포함된다.
    
  * allprojects, subprojects, project
  > 멀티모듈의 경우 이렇게 새로운 블록이 등작합니다. allprojects는 전체 프로젝트에, subprojects는 하위프로젝트에 그리고 project는 해당하는 프로젝트에만 동작하는 설정입니다.
  
  * task
  > 사용자가 임의로 task를 작성해서 사용할 수 있습니다. 
  

### 멀티모듈
**회사 코드와 https://techblog.woowahan.com/2637/ 블로그 글을 참고하여 이해용도로 작성**
