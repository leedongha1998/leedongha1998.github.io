---
title: "자바 알고리즘"
categories:
 - algorithm
tags: [algorithm] 
toc: true
author_profile: true #profile sidebar 감추기
# sidebar:
#     nav: "docs" # 목차 사이드바
search: true #검색 피하기
---



#자바 알고리즘 개념



##### Scanner 정의 및 특징

{: .notice-info}

1. ***기본적인 데이터 타입들을 Scanner의 메소드를 사용하여 입력받을 수 있다.***(예로 들어 100을 입력하고자 할 때, 문자열로 입력받고 싶으면 next()나 nextLine()을, 정수로 받고 싶다면 nextInt()를 사용하여 입력받으면 알아서 해당 타입으로 입력된다.)
2. ***Scanner를 사용할 시 util 패키지를 경로의 Scanner 클래스를 호출해야 한다.***(자바에서 쓰이는 대부분의 클래스는 lang패키지가 아니라면 import를 통해 호출해주어야 한다. Scanner의 경우는 java.util에 있다.)
3. ***공백(띄어쓰기) 또는 개행을 기준으로 읽는다.***(Scanner의 입력 메소드들은 대부분 공백과 개행을 기준으로 읽는다.)



###### Scanner 사용

1. Scanner import

2. Scanner 객체 생성

   ```java
   Scanner in = new Scanner(System.in); // System.in은 사용자로부터 입력을 받기 위한 입력 스트림이다.
   ```

3. 메소드를 사용하여 입력하기

   ```java
   in.nextByte();
   in.nextShort();
   in.nextInt();
   in.nextLong();
   
   in.nextFloat();
   in.nextDouble();
   
   in.nextBoolean();
   
   in.next(); // String 형 입력 및 리턴(공백 기준으로 한 단어 읽음)
   in.nextLine(); // String 형 입력 및 리턴(개행 기준으로 한 줄을 읽음)
   ```



##### 대소문자 변환

###### 	Character.isLowerCase()

​		char 타입 문자가 소문자냐고 물어보는 코드.



###### 	아스키 코드

​		65~90 -> 대문자

​		97~122 -> 소문자



##### 단어 뒤집기

###### 	StringBuilder

​	{: .notice-info}

​	문자열 버퍼에 담아 그 안에서 추가 수정 삭제 작업을 할 수 있	도록 도와주는 클래스



```java
public static void main(String[] args) {
    StringBuilder sb = new StringBuilder();
    //문자열이 커질수록 자동으로 크기를 추가하기 때문		에 초기에 주는 생성자에 크기값을 줄 필요가 크게 없다.
	}

sb.append("i"); // 문자열 끝에 추가
sb.insert(5,"i"); // 특정 위치에 추가
sb.setCharAt(4,'b'); // char이기 때문에 '' 사용
sb.replace(4,5,"cc"); // 시작점 끝점 설정후 해당 구간 변경 원하는 문자열 추가
sb.substring(0,4); // 0~3까지 문자열 추출
```





###### 	StringBuffer

​	{: .notice-info}

​	StringBuilder와 사용법이 동일하다.

​	문자열을 추가하거나 변경할 때 주로 사용하는 자료형.

​	동기화 키워드를 지원하여 멀티쓰레드 환경에서 안전.



###### 	valueOf()

​	{: .notice-info}

​	괄호 안의 해당 객체를 String 객체로 변환시키는 역할을 한다.



```java
String a = "1234";

String b = String.valueOf(10);

String c = String.valueOf(a);

String d = String.valueOf(true);

String e = String.valueOf(false);

//String.valueOf는 int형이든 double형				이든 boolean형이든 String객체로 만든다.

System.out.println(a);

System.out.println(b);

System.out.println(c);

System.out.println(d);

System.out.println(e);


System.out.println(a + b);

System.out.println(a + b + c);

System.out.println(c + d);

System.out.println(c + d + e);

//a,b,c,d,e 모두 String 객체이므로 +연산자로 합치면 글자를 합친 결과와 같다.
```



​	



