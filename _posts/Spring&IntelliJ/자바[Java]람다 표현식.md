---
layout: single
title: "자바 람다 표현식"
categories: JAVA
tag: [Spring&IntelliJ]
toc: true
author_profile: false

---





# 자바 람다 표현식 (lamda expression)

#### 람다 표현식(lambda expression)이란?

람다 표현식(lambda expression)이란 간단히 말해 메소드를 하나의 식으로 표현한 것입니다.

##### 메소드

```java
int min(int x, int y) {

  return x < y ? x : y;

}
```



##### 람다 표현식

```java
(x, y) -> x < y ? x : y;
```

 

위의 예제처럼 메소드를 람다 표현식으로 표현하면, 클래스를 작성하고 객체를 생성하지 않아도 메소드를 사용할 수 있습니다.

 

그런데 자바에서는 클래스의 선언과 동시에 객체를 생성하므로, 단 하나의 객체만을 생성할 수 있는 클래스를 익명 클래스라고 합니다.

따라서 자바에서 람다 표현식은 익명 클래스와 같다고 할 수 있습니다.

##### 람다 표현식

```java
(x, y) -> x < y ? x : y;
```



##### 익명 클래스

```java
new Object() {

  int min(int x, int y) {

​    return x < y ? x : y;

  }

}
```

 

이러한 람다 표현식은 메소드의 매개변수로 전달될 수도 있으며, 메소드의 결괏값으로 반환될 수도 있습니다.

따라서 람다 표현식을 사용하면, 기존의 불필요한 코드를 줄여주고, 작성된 코드의 가독성을 높여줍니다.

Java SE 8부터는 이러한 람다 표현식을 사용하여 자바에서도 함수형 프로그래밍을 할 수 있게 되었습니다.

------

#### 람다 표현식 작성

자바에서는 화살표(->) 기호를 사용하여 람다 표현식을 작성할 수 있습니다.

##### 문법

(매개변수목록)   -    >   { 함수몸체 }

 

자바에서 람다 표현식을 작성할 때 유의해야 할 사항은 다음과 같습니다.

 

1. 매개변수의 타입을 추론할 수 있는 경우에는 타입을 생략할 수 있습니다.

2. 매개변수가 하나인 경우에는 괄호(())를 생략할 수 있습니다.

3. 함수의 몸체가 하나의 명령문만으로 이루어진 경우에는 중괄호({})를 생략할 수 있습니다. (이때 세미콜론(;)은 붙이지 않음)

4. 함수의 몸체가 하나의 return 문으로만 이루어진 경우에는 중괄호({})를 생략할 수 없습니다.

5. return 문 대신 표현식을 사용할 수 있으며, 이때 반환값은 표현식의 결괏값이 됩니다. (이때 세미콜론(;)은 붙이지 않음)

 

다음 예제는 전통적인 방식의 스레드 생성과 람다 표현식을 사용한 스레드 생성을 비교하는 예제입니다.

##### 예제

```java
new Thread(new Runnable() {

  public void run() {

​    System.out.println("전통적인 방식의 일회용 스레드 생성");

  }

}).start();
```

 

  new     Thread  (()->{

​    System.  out  .  println("람다 표현식을 사용한 일회용 스레드 생성");

})  .  start();

[코딩연습 ▶](http://www.tcpschool.com/examples/tryit/tryJava.php?filename=Lambda01)

##### 실행 결과

전통적인 방식의 일회용 스레드 생성

람다 표현식을 사용한 일회용 스레드 생성

 

위의 예제에서 볼 수 있듯이 람다 표현식을 사용하면 불필요한 코드를 줄일 수 있으며, 코드의 가독성이 훨씬 좋아집니다.

------

#### 함수형 인터페이스(functional interface)

람다 표현식을 사용할 때는 람다 표현식을 저장하기 위한 참조 변수의 타입을 결정해야만 합니다.

##### 문법

참조변수의타입 참조변수의이름 = 람다 표현식

 

위의 문법처럼 람다 표현식을 하나의 변수에 대입할 때 사용하는 참조 변수의 타입을 함수형 인터페이스라고 부릅니다.

 

함수형 인터페이스는 추상 클래스와는 달리 단 하나의 추상 메소드만을 가져야 합니다.

또한, 다음과 같은 어노테이션(annotation)을 사용하여 함수형 인터페이스임을 명시할 수 있습니다.

##### 문법

@  FunctionalInterface  

 

위와 같은 어노테이션을 인터페이스의 선언 앞에 붙이면, 컴파일러는 해당 인터페이스를 함수형 인터페이스로 인식합니다.

자바 컴파일러는 이렇게 명시된 함수형 인터페이스에 두 개 이상의 메소드가 선언되면 오류를 발생시킵니다.

 

다음 예제는 함수형 인터페이스를 선언하고 사용하는 예제입니다.

##### 예제

```JAVA
@FunctionalInterface  

  interface Calc {  // 함수형 인터페이스의 선언 

    public int min(int x ,int y );

}
```

 

```JAVA
public class Lambda02 {

  public static void main(String[]args ){

     Calc minNum = (x, y) -> x < y ? x:y;  // 추상 메소드의 구현 

     System.out.println(minNum.min(3,4));   // 함수형 인터페이스의 사용 

  }

}
```

[코딩연습 ▶](http://www.tcpschool.com/examples/tryit/tryJava.php?filename=Lambda02)

##### 실행 결과

```
3
```

 

자바는 java.util.function 패키지를 통해 여러 상황에서 사용할 수 있는 다양한 함수형 인터페이스를 미리 정의하여 제공합니다.

java.util.function 패키지에 대한 더 자세한 사항은 다음 페이지를 참고하면 됩니다.

 

[Package java.util.function =>](http://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)



*참고 사이트 : http://www.tcpschool.com/java/java_lambda_concept