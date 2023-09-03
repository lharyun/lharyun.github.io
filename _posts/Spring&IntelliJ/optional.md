<h1>
[Java] Optional이란? 개념 및 사용법
</h1>



## [Optional이란?]

<span style="color:red">Java8</span>에서는 Optional\<T>클래스를 사용해 NPE(NullPointException)를 방지할 수 있도록 도와준다. Optional\<T>는 null이 올 수 있는 값을 감싸는Wrapper클래스로, 참조하더라도 NPE가 발생하지 않도록 도와준다. Optional 클래스는 아래와 같은 value에 값을 저장하기 때문에 값이 null이더라도 바로 NPE가 발생하지 않으며, 클래스이기 때문에 각종 메서드를 제공해준다.

```Java
public final class Optional<T>{
	private final T value;
	...
}
```



#### Optional 객체의 생성

of() 메소드나 ofNullable() 메소드를 사용하여 Optional 객체를 생성할 수 있습니다.

 

of() 메소드는 null이 아닌 명시된 값을 가지는 Optional 객체를 반환합니다.

만약 of() 메소드를 통해 생성된 Optional 객체에 null이 저장되면 NullPointerException 예외가 발생합니다.

 

따라서 만약 참조 변수의 값이 만에 하나 null이 될 가능성이 있다면, ofNullable() 메소드를 사용하여 Optional 객체를 생성하는 것이 좋습니다.

ofNullable() 메소드는 명시된 값이 null이 아니면 명시된 값을 가지는 Optional 객체를 반환하며, 명시된 값이 null이면 비어있는 Optional 객체를 반환합니다.



###### ex)

```Java
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");

System.out.println(opt.get());
```

###### 결과

```
자바 Optional 객체
```

---

#### Optional 객체에 접근

get() 메소드를 사용하면 Optional 객체에 저장된 값에 접근할 수 있습니다.

만약 Optional 객체에 저장된 값이 null이면, NoSuchElementException 예외가 발생합니다.

따라서 get() 메소드를 호출하기 전에 isPresent() 메소드를 사용하여 Optional 객체에 저장된 값이 null인지 아닌지를 먼저 확인한 후 호출하는 것이 좋습니다.

 

다음 예제는 isPresent() 메소드를 이용하여 좀 더 안전하게 Optional 객체에 저장된 값에 접근하는 예제입니다.

###### ex)

```Java
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");

if(opt.isPresent()) {

    System.out.println(opt.get());

}
```

###### 결과

```JAVA
자바 Optional 객체
```

---



#### isPresent()와 ifPresent()의 차이



**1. isPresent() 메소드**

\- Boolean 타입

\- Optional 객체가 값을 가지고 있다면 true, 값이 없다면 false 리턴



**2. ifPresent() 메소드**

\- Void 타입

\- ifPresent()는 Optional 객체가 값을 가지고 있으면 실행 값이 없으면 넘어감





---







또한, 다음과 같은 메소드를 사용하여 null 대신에 대체할 값을 지정할 수도 있습니다.

 

1. orElse() 메소드 : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 값을 반환함.

2. orElseGet() 메소드 : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 람다 표현식의 결괏값을 반환함.

3. orElseThrow() 메소드 : 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 예외를 발생시킴.

###### ex)

```JAVA
Optional<String> opt = Optional.empty(); // Optional를 null로 초기화함.

System.out.println(opt.orElse("빈 Optional 객체"));

System.out.println(opt.orElseGet(String::new));
```

###### 결과

```
빈 Optional 객체
```

위의 예제에서 사용된 empty() 메소드는 Optional 객체를 null로 초기화해줍니다.

---

#### 기본 타입의 Optional 클래스

자바에서는 IntStream 클래스와 같이 기본 타입 스트림을 위한 별도의 Optional 클래스를 제공하고 있습니다.

 

1. OptionalInt 클래스

2. OptionalLong 클래스

3. OptionalDouble 클래스

 

이러한 클래스는 반환 타입이 Optional<T> 타입이 아니라 해당 기본 타입이라는 사실만 제외하면 거의 모든 면에서 비슷합니다.

 

또한, Optional 객체에서 get() 메소드를 사용하여 저장된 값에 접근할 수 있는 것처럼 클래스별로 저장된 값에 접근할 수 있는 다음과 같은 메소드를 제공하고 있습니다

| 클래스         | 저장된 값에 접근하는 메서드 |
| -------------- | --------------------------- |
| Optional<T>    | T get()                     |
| OptionalInt    | int getAsInt()              |
| OptionalLong   | long getAsLong()            |
| OptionalDouble | double getAsDouble()        |

###### ex)

```java
IntStream stream = IntStream.of(4, 2, 1, 3);

OptionalInt result = stream.findFirst();

 
System.out.println(result.getAsInt());
```

###### 결과

```
4
```



### optional 메소드

| 메소드                                                       | 설명                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| static\<T\>Optional\<T\>empty()                              | 아무런 값도 가지지 않는 비어있는 Optional 객체를 반환함.     |
| T get()                                                      | Optional 객체에 저장된 값을 반환함.                          |
| boolean isPresent()                                          | 저장된 값이 존재하면 true를 반환하고, 값이 존재하지 않으면 false를 반환함. |
| static\<T\>Optional\<T\>of(T value)                          | null이 아닌 명시된 값을 가지는 Optional 객체를 반환함.       |
| static\<T\>Optional\<T\>ofNullable(T vlaue)                  | 명시된 값이 null이 아니면 명시된 값을 가지는 Optional객체를 반환하며, 명시된 값이 null이면 비어있는 Optional객체를 반환함. |
| T orElse(T other)                                            | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 값을 반환함 |
| T orElseGet(Supplier\<? extends T\> other)                   | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 람다 표현식의 결과값을 반환함 |
| \<X extends Throwable\>T orElseThrow(Supplier\<?extends X\>exceptionSupplier) | 저장된 값이 존재하면 그 값을 반환하고, 값이 존재하지 않으면 인수로 전달된 예외를 발생시킴. |





##### 참고 사이트: http://www.tcpschool.com/java/java_stream_optional