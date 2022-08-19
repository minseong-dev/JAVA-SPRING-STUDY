# Web Server와 WAS

- 스프링 부트 프로젝트를 생성하면서 패키징 파일로 jar와 war 중 선택을 하게 되었고,  
둘의 차이점에 대해 공부를 하며 계속 언급되는 WAS를 막연히 서버라고만 이해하고 있는 것 같아서 좀 더 자세히 알아보았다.

<br>
<br>

## Web Server

- 웹 브라우저 클라이언트로 부터 HTTP요청을 받아 **정적인 컨텐츠**를 제공하는 프로그램
    1. HTTP 프로토콜을 기반으로 하여 클라이언트의 요청을 서비스
    2. 정적인 컨텐츠 제공
        - WAS를 거치지 않고 바로!
    3. 동적인 컨텐츠 제공을 위한 요청 전달

ex) apache, nginx

<br>

## Web Application Server

- DB조회나 다양한 로직 처리를 요구하는 **동적인 컨텐츠**를 제공하기 위해 만들어진 Application Server
    1. 프로그램 실행 환경과 DB 접속 기능 제공
    2. 여러 개의 트랜잭션 관리 기능
    3. 업무를 처리하는 비즈니스 로직 수행
- Web Server + Web Container(Servlet Container)

ex) Tomcat

<br>

## 둘을 같이 사용하는 이유

- 기능을 분리하여 서버 부하 방지
    - WAS 앞에 웹 서버를 둬서 웹 서버에 정적인 문서만 처리하도록하고, WAS는 애플리케이션의 로직만 수행하도록 기능을 분배해서 서버의 부담을 줄인다.
- 물리적으로 분리하여 보안 강화
    - 클라이언트와 연결하는 포트가 직접 WAS에 연결이 되어 있다면 중요한 설정 파일들이 노출될 수 있기 때문에 WAS 설정 파일을 외부에 노출시키지 않도록 하기 위함
    - 웹 서버와 WAS에 접근하는 포트가 다르기 때문에 WAS에 들어오는 포트에는 방화벽을 쳐서 보안을 강화할 수도 있음
- 여러 대의 WAS 연결 가능
    - 대용량 웹 어플리케이션의 경우(여러 개의 서버 사용) Web Server와 WAS를 분리하여 무중단 운영을 위한 장애 극복에 쉽게 대응할 수 있다.

<br>

## Web Server Architecture
![web-server-architecture](./assets/web-service-architecture.png)

<br>
<br>

참고
> https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html  
> https://jeong-pro.tistory.com/84  
> https://2dubbing.tistory.com/29  
> https://pjh3749.tistory.com/267  
> https://brunch.co.kr/@springboot/21
