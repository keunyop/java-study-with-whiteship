# 8주차: 인터페이스

## 목표

자바의 인터페이스에 대해 학습하세요.

## 학습할 것
- 인터페이스 정의하는 방법

- 인터페이스 구현하는 방법
- 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법
- 인터페이스 상속
- 인터페이스의 기본 메소드 (Default Method), 자바 8
- 인터페이스의 static 메소드, 자바 8
- 인터페이스의 private 메소드, 자바 9

---

### ■ 인터페이스 정의하는 방법

class 키워드 대신 interface를 사용하여 작성한다.

접근제어자는 public과 default가 가능하다. 

```java
public interface Car {
    int MAX_SPEED = 300; // public static final int
    void moveForward(int degree); // public abstract moveForward(int degree);
    void moveBackward(int degree); // public abstarct moveBackward(int degree);
}
```

인터페이스는 다양한 특성을 가지고 잇다.

- 멤버는 추상 메소드와 상수만 가능하다.
- 모든 메소드는 public이며 생략이 가능하다.
- 상수는 public static final 생략이 가능하다.
- 인터페이스는 객체를 생성할 수 없다. ex) new Car(); // X
- 다른 인터페이스에 상속될 수 있고 다중 상속을 허용한다.
- 인터페이스는 래퍼런스 변수로 사용이 가능하다. ex) Car car; // O

하지만 Java8부터는 default method를 정의할 수 있다. 이로 인하여 추상 클래스의 경계가 모호해졌다.  

인터페이스안에 인터페이스나 클래스를 중첩하여 사용 할 수 있다. 인터페이스 내부에 선언된 인터페이스나 클래스는 public static으로 간주된다.


### ■ 인터페이스 구현하는 방법

인터페이스는 implements 키워드를 이용해서 클래스를 선언하고 클래스에 실제 메서드의 처리를 정의한다.

```java
public class Bar implements Foo {
    @Override
    public String say() {
       System.out.println("Bar");                
    }                                      
}
```

인터페이스에는 메서드뿐만아니라 상수(public static final 필드)를 정의하는 것도 가능하다.
또한 public static final도 생략이 가능하다.

```java
interface Foo{
   int number = 10;
}
```

- 인터페이스는 반드시 public 이므로 생략 가능하다.

- 모든 메서드는 public abstract 이어야 하며, 이를 생략할 수 있다.(static, default 메서드는 예외, JDK 1.8~)
- 모든 멤버변수는 public static final 이어야 하며, 이를 생략할 수 있다.

### ■ 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법

### ■ 인터페이스 상속

### ■ 인터페이스의 기본 메소드 (Default Method), 자바 8

### ■ 인터페이스의 static 메소드, 자바 8

### ■ 인터페이스의 private 메소드, 자바 9


