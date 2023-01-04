[toc]

# 프로젝트 흐름

1. 프로젝트 설정(자바, 서버 버전)
1. 내 인덱스 페이지로 요청하기 위해 HomeController에서 `return "forward:/index.jsp";`으로 수정
1. servlet 버전과 web.xml 버전을 일치시킴
1. `<context:component-scan>`
   1. 해당 태그는 servlet-context.xml 파일에 있다.
   1. @Controller, @Service, @Repository와 같은 어노테이션을 사용할 수 있다.
1. `pageContext.request.contextPath` 
   1. http://localhost:9090/project/ 에서 /project를 의미한다.
1. db 연결
   1. `<context:property-placeholder>` 태그를 사용한 외부 설정 프로퍼티 사용
   1. 위 태그 location 속성 값에 classpath:datasource.properties라고 적어두었는데 여기서 classpath는 프로젝트의 buildpath에 나와있는 경로에 있는 datasource.properties를 가리킨다.
1. jstl 
   1. `<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
      <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt"%>
      <%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions"%>`
   1. 위 친구들 자주 쓰는 애들이라 jsp 작성할 때 저 친구들 일단 써놓기
