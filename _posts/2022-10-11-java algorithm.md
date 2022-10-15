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

[TOC]

#자바 알고리즘 개념





##### 입출력 관련

###### Scanner 정의 및 특징

​	{: .notice--info}

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



##### 문자 관련

###### 대소문자 변환

###### 	Character.isLowerCase()

​		char 타입 문자가 소문자냐고 물어보는 코드.



###### 	아스키 코드

​		65~90 -> 대문자

​		97~122 -> 소문자



###### ReplaceAll(pattern, str)

패턴과 일치하는 조건들을 주어진 str로 바꿔주는 함수

###### 	정규표현식

| Reqular Expression | Description                                  |
| :----------------: | :------------------------------------------- |
|         .          | 어떤 문자 1개를 의미                         |
|       ^regex       | ^다음 regex로 line을 시작하는 지             |
|       regex$       | $앞의 regex가 line의 마지막으로 끝나는지     |
|       [abc]        | a,b,c 중의 문자 1개                          |
|     [abc]\[vz]     | a,b,c 중에 문자 1개와 v,z 중에 문자 1개 조합 |
|       [^abc]       | a,b,c를 제외한 문자 1개                      |
|      [a-d1-7]      | a-d,1-7 사이의 문자 1개                      |
|         \d         | 0-9 사이의 숫자 [0-9]와 동일                 |
|         \D         | 숫자가 아닌 어떤 문자, \[^0-9]와 동일        |
|         \s         | 공백 1개                                     |
|         \S         | 공백을 제외한 문자                           |
|         \w         | 알파벳,숫자 [a-zA-Z_0-9]와 동일              |
|         \W         | 위의 조건을 제외한 문자                      |
|        \S+         | 공백을 제외한 여러 문자                      |
|         \b         | 단어의 경계(공백)을 찾는다                   |



##### 단어 뒤집기

###### 	StringBuilder

​	{: .notice--info}

​	문자열 버퍼에 담아 그 안에서 추가 수정 삭제 작업을 할 수 있	도록 도와주는 클래스



```java
public static void main(String[] args) {
    StringBuilder sb = new StringBuilder();
    //문자열이 커질수록 자동으로 크기를 추가하기 때문에 초기에 주는 생성자에 크기값을 줄 필요가 크게 없다.
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

​	{: .notice--info}

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





##### 배열 관련

###### 배열 앞 뒤 순서 바꾸기 문제

lt, rt로 양쪽에서 하나씩 점검하면서 좁혀오는 과정

```java
char[] arr = str.toCharArray();
		int lt = 0;
		int rt = str.length() -1;
		char temp = 'a';
		while(lt < rt) {
			if(!Character.isAlphabetic(arr[lt])) {
				lt++;
			}else if (!Character.isAlphabetic(arr[rt])) {
				rt--;
			}else {
				temp = arr[lt];
				arr[lt] = arr[rt];
				arr[rt] = temp;
				lt++;
				rt--;
			}
		}
```



##### indexOf

{: .notice--info}

먼저 indexOf는 특정 문자나 문자열이 앞에서부터 처음 발견되는 인덱스를 반환. 만약 찾지 못했으면 -1 리턴.





##### 정렬 관련

###### Collections.reversOrder()

​	내림차순 정렬, 기본타입(int,long)과 같은 타입으로 사용할 수 	없고 <span style="background-color:yellow"> 래퍼 클래스 및 개체에서</span> 작동하는 메소드이다. 



###### 문자열 내 마음대로 정렬하기 문제(프로그래머스)

{: .notice--info}

참고 사이트 : <https://discover.tistory.com/42>

1. sort와 substring으로 해결하기
2. 알파벳 int형
3. compare
4. 람다식









