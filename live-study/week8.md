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

- 인터페이스는 다형성을 이용해 구현할 수 있다.

- 자식 클래스의 인스턴스를 부모 클래스에 참조변수로 참조하는 것이 가능하다.

```java
interface Shape{
    void draw();
}

class Square implements Shape{
    @Override
    public void draw() {
        System.out.println("This is a square.");
    }
}

class Circle implements Shape{
    @Override
    public void draw() {
        System.out.println("This is a circle.");
    }
}
public class ReferenceImplements {
    public static void main(String[] args) {
        Shape shape1=new Square();
        Shape shape2=new Circle();

        shape1.draw();
        shape2.draw();
    }
}
```

### ■ 인터페이스 상속

인터페이스 상속이란, 자식 클래스가 부모 클래스를 상속받는 것과 비슷하게 작동한다.

클래스와 마찬가지로 extends 예약어를 사용한다

부모 인터페이스에 선언된 추상 메소드를 자식 인터페이스에서 상속받은 뒤, 새로운 추상 메소드나 상수를 추가한다.

```java
public interface A {
    int LENGTH = 10;

    public void speak();
}

public interface B extends A{
    @Override
    void speak();

    void run();
     int LENGTH = 20;

}

public class InheritanceExam implements B{
    @Override
    public void speak() {
        System.out.println("Hello!!");
    }

    @Override
    public void run() {
        System.out.println("running!!!!");
    }

    public static void main(String[] args) {
        A a = new InheritanceExam();
        B b = new InheritanceExam();

        System.out.println(a.LENGTH);
        System.out.println(b.LENGTH);
    }
}
```

### ■ 인터페이스의 기본 메소드 (Default Method), 자바 8

interface에서 업무를 구현할 수 있는 method

- JDK 1.7에서부터 interface에 업무를 구현할 수 있는 defalut method 추가

- 구현하게 되면 추상클래스와 큰 차이가 없어지게 된다.
- 사용은 객체를 생성한 후에 사용(is-a관계에서)

```java
접근지정자 default 반환형 method명(매개변수,,) {
            
}
```

### ■ 인터페이스의 static 메소드, 자바 8

구현하는 클래스에서 구현하지 않더라도 사용할 수 있도록 인터페이스에서 미리 구현하는 메소드이다.

- 현 클래스의 인스턴스를 생성하지 않더라도 사용할 수 있다.

- 구현 클래스 또는 하위 인터페이스에 상속되지 않는다.
- 상속되지 않기 때문에 구현 클래스에서 재정의 할 수 없다.

```java
public interface MyInterface {
    void show(String string);
    void sum(int num1, int num2);

    static void staticMethod() {
        System.out.println("static method");
    }
}

class MyClassTest {
    @Test
    public void test() {
        //인스턴스를 생성하지 않아도 바로 호출할 수 있다.
        MyInterface.defaultMethod();
    }
}
```


### ■ 인터페이스의 private 메소드, 자바 9

Java8 부터 default 및 static 메소드의 도입으로 인터페이스는 갑자기 메소드 이름(method signatures) 뿐만 아니라 구현을 포함 할 수 있게 되었다. 

일반적으로 이러한 메소드는 구현 세부 사항이며 외부에서 볼 수 없고 사용할 수 없으므로 주로 private 메소드를 사용한다.

Java9 부터는 인터페이스에서 private methods를 사용할 수 있게 되었다.

인터페이스에서 사용하는 private methods 는 다음과 같은 특성을 가지고 있다.

- 메소드 body가 있고 abstract가 아니다.

- static 이거나 non-static 일 수 있다.
- 구현 클래스와 인터페이스가 상속되지 않는다.
- 인터페이스에서 다른 메소드를 호출할 수 있다.