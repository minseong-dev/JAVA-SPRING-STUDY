# Servlet

## Servlet이란?
- **클라이언트의 요청을 처리하고, 그 결과를 반환하는 Servlet 클래스의 구현 규칙을 지킨 자바 웹 프로그래밍 기술**
- html을 사용하여 요청에 응답
- 자바로 구현된 CGI
- 스레드 단위로 작업 -> CGI는 프로세스 단위로 작업하여 이를 보완
- MVC패턴에서 Controller로 사용
- 보안 기능을 적용하기 쉬움

## Servlet Container
- **서블릿을 관리해주는 컨테이너**
- Web server와의 통신 지원
- Servlet 생명주기 관리
- 멀티스레드 지원 및 관리
- 보안 관리

## Servlet 동작 과정
1. Servlet Request, Servlet Response 객체를 생성
2. 설정 파일을 참고하여 매핑할 Servlet 확인
3. 해당 Servlet 인스턴스 존재의 유무를 확인하고 없으면 init() 메소드를 호출하여 생성
4. Servlet Container에 스레드를 생성하고 service 실행
5. 응답을 처리했으면 destroy() 메소드를 실행하여 Servlet Request, Servlet Response 객체 소멸

참고
> https://mangkyu.tistory.com/14  
> https://coding-factory.tistory.com/742  
> https://velog.io/@jakeseo_me/자바-서블릿에-대해-알아보자.-근데-톰캣과-스프링을-살짝-곁들인