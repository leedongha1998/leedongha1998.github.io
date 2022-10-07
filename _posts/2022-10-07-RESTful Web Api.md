---
title: "RESTful Web Api"
categories:
 - REST
tags: [REST] 
toc: true
author_profile: true #profile sidebar 감추기
# sidebar:
#     nav: "docs" # 목차 사이드바
search: true #검색 피하기
---

# RESTful Web API

##### http 응답

1. 상태 코드(status code)

​		세자리 숫자로 요청이 어떻게 됐는지 요약해 보여준다.

​		ex) 200, 404

2. 엔티티 바디(entity-body)

   클라이언트가 이해할 수 있으리라 예상되는 어떤 데이터 형식으로 작성된 문서.

   GET 요청을 표현에 대한 요청이라 생각한다면 엔티티 바디를 표현으로 생각할 수 있다.

   이 경우 엔티티 바디는 응답 끝에 붙은 {}로 둘러싸인 거대한 문서이다.

3. 응답 헤더

   HTTP 응답과 엔티티 바디를 전반적으로 설명하는 키-값 묶음이다.

   그 중에서 가장 중요한 부분은 Content-Type인데, HTTP 클라이언트에게 엔티티 바디를 어떻게 이해해야 할지 설명해준다.

   ex) text/html, image/jpeg

4. JSON

   평문으로 된 간단한 자료 구조를 표현하는 표준이다.

   엔티티 바디가 JSON 문서이다.

5. Collection + JSON

​		웹에서 검색 가능한 리소스 목록을 발표하는 표준이다.



##### Http의 프로토콜 의미 체계

1. GET : 리소스의 표현을 얻어온다.
2. DELETE : 리소스를 제거한다.
3. POST : 주어진 표현에 기반을 두고 이 리소스 아래 새 리소스를 생성한다.
4. PUT : 이 리소스의 현재 상태를 주어진 표현으로 대치한다.
5. HEAD : 이 리소스의 표현과 함께 주어질 헤더를 받아오지만, 표현 자체는 받지 않는다.
6. OPTION : 이 리소스가 어떤 HTTP 메서드에 응답하는지 알아낸다.
7. PATCH : 이 리소스의 일부 상태를 주어진 표현으로 변경한다.
8. LINK : 다른 리소스를 이 리소스에 연결한다.
9. UNLINK : 다른 리소스와 이 리소스의 연결 관계를 제거한다.





