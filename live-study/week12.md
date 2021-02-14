# 12주 차: 애노테이션

## 목표

자바의 애노테이션에 대해 학습하세요.

## 학습할 것

- 애노테이션 정의하는 방법

- @retention
- @target
- @documented
- 애노테이션 프로세서

---

### ■ 애노테이션 정의하는 방법

커스텀한 어노테이션을 만들어 사용하고 싶다면 다음과 같이 간단하게 Annotation 을 정의해 사용할 수 있다.

```java
public @interface Custom {
}

@Custom
public class Test {
}
```

또한 Annotation 들은 enum 과 String, primitive type 에 대한 값을 가질 수 있고 default 값을 선언할 수도 있다.

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Inherited
public @interface Custom {
    String name() default "hello";
    int age();
}


@Custom(age = 10)
public class Test {
    public static void main(String[] args) {
        Arrays.stream(Test.class.getAnnotations()).forEach( a ->{
            Custom custom = (Custom) a;
            System.out.println(custom.name());
            System.out.println(custom.age());
        });
    }
}
-----> console 
hello
10
```

참고로 만약 값을 하나만 사용한다면 value() 를 사용하면 사용하는 곳에서 값을 그냥 주어 사용할 수 있다.

```java
@Retention(RetentionPolicy.RUNTIME)
public @interface Name {
    String value();
}


@Name("This is name")
public class Tester {
    public static void main(String[] args) {
        Name annotation = Tester.class.getAnnotation(Name.class);
        System.out.println(annotation.value());
    }

}
---> console
This is name
```

### ■ @retention

javac와 자바 런타임이 커스텀 어노테이션을 처리해야 하는 시점을 나타낸다.

### ■ @target

애노테이션을 정의할 때, 애노테이션이 적용가능한 대상을 지정하는 데에 사용된다.

애노테이션이 적용가능한 대상 타입들은 다음과 같다.

| 대상 타입       | 의미                             |
| :-------------- | -------------------------------- |
| ANNOTATION_TYPE | 애노테이션                       |
| CONSTRUCTOR     | 생성자                           |
| FIELD           | 필드(멤버변수, enum 상수)        |
| LOCAL_VARIABLE  | 지역변수                         |
| METHOD          | 메서드                           |
| PACKAGE         | 패키지                           |
| PARAMETER       | 매개변수                         |
| TYPE            | 타입(클래스, 인터페이스, enum)   |
| TYPE_PARAMETER  | 타입 매개변수(JDK 1.8)           |
| TYPE_USE        | 타입이 사용되는 모든 곳(JDK 1.8) |

```java
@Target({FIELD, TYPE, TYPE_USE})	// 적용대상이 FIELD, TYPE, TYPE_USE
public @interface MyAnnotation {}	// My Annotation 정의

@MyAnnotation	// 적용대상이 TYPE인 경우
class MyClass{
    
    @MyAnnotation	// 적용대상이 FIELD인 경우
    int i;
    
    @MyAnnotation	// 적용대상이 TYPE_USE인 경우
    MyClass mc;
}
```

### ■ @documented

문서에도 애노테이션 정보가 표현된다. javadoc 과 같이 도구에 의해 내가 작성한 내용이 문서화 될 수 있도록 한다.


### ■ 애노테이션 프로세서

애노테이션 프로세스는 컴파일하는 중간에 특정한 애노테이션이 붙어있는 소스코드를 참고해서 또다른 소스코드를 작성하는 일을 해낼 수 있다.

대표적으로 Lombok이 자바의 애노테이션 프로세서를 사용하여 동작하며 컴파일 타임에 소스코드의 AST를 조작하게 된다. 본래 프로세서가 제공하는 API를 통해서는 기존 소스코드는 참조만 할 수 있으나, 공개된 API가 아닌 컴파일러 내부 클래스를 사용하여 소스 코드를 조작할 수 있다.