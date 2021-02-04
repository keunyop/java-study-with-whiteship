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

### ■ @target

### ■ @documented

### ■ 애노테이션 프로세서