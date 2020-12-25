# 6주차: 상속

## 목표

자바의 상속에 대해 학습하세요.

## 학습할 것
- 자바 상속의 특징
- super 키워드
- 메소드 오버라이딩
- 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
- 추상 클래스
- final 키워드
- Object 클래스

### ■ 자바 상속의 특징

한 클래스의 멤버를 다른 클래스가 물려받는 것을 상속이라 한다.

멤버를 물려주는 클래스를 superclass(parent class), 멤버를 물려받는 클래스를 subclass(child class) 라고 한다.

### 자바에서의 상속
- Object 클래스는 superclass를 가지지 않는다.
- Object를 제외한 모든 클래스는 단 하나의 superclass를 가진다.
- superclass가 보이지 않는 클래스는 Object 클래스를 이미 상속하고 있다.
- 따라서 Object 클래스를 제외한 모든 클래스는 Object 클래스의 descendants라고 할 수 있다.
- superclass의 멤버는 subclass에 상속된다. 접근 제어자에 따라서 달라진다.
- 생성자는 멤버가 아니기에 subclass에 상속되지 않는다.
- 하지만 superclass의 생성자는 subclass에서 호출할 수 있다.

### ■ super 키워드

super 키워드는 자식 클래스에서 부모 클래스의 자원을 참조하는데 사용되는 변수다. 

부모 클래스의 자원도 this 키워드를 사용해 참조할 수 있고, 자식 클래스의 자원과 부모 클래스의 자원을 구별해서 사용해야 할 때 super 키워드를 사용한다.

```java
class Product {
    String productCode;
    String type = "Product Type";
}

class Book extends Product {
    String author;
    String type = "Book Type";

    void displayType() {
        System.out.println(String.format("Super: %s, This: %s", super.type, this.type));
    }
}

public class SampleTest {
    public static void main(String[] args) {
        Book book = new Book();
        book.displayType();
    }
}
```

출력결과

> Super: Product Type, This: Book Type


### ■ 메소드 오버라이딩

조상 클래스로부터 상속받은 메서드의 내용을 변경하는 것.

어떤 메서드를 사용할 때 상속받은 메서드를 그대로 사용할 수도 있지만, 자손 클래스에 맞게 변경해야 하는 경우엔 조상의 메서드를 오버라이딩한다.

```java
public class Graph {
    int x;
    int y;

    String getLocation() {
        return "x : " + x + "y : " + y;
    }
}

public class Graph3D extends Graph {
    int z;

    @Override
    String getLocation() {
        return "x : " + x + "y : " + y + "z : " + z;
    }
}
```

#### 오버 라이딩의 조건

- 선언부가 조상 클래스의 메서드와 일치해야 한다.
- 접근 제어자를 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다.
- 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다.

### ■ 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)

- 오버라이딩 된 메소드들이 있는 경우 어떤 것을 호출할지를 런타임에서 결정하는 것
- 해당 메소드 참조에 의해 호출될 때, 객체 유형에 따라서 실행할 메소드를 결정
- 자바는 묵시적으로 메소드를 호출할 객체를 인자로 넘기기 때문에 메소드 내부에서 호출 객체를 참조할 수 있다. → 런타임에서 호출하는 객체도 결정된다.

- 자바는 묵시적으로 메소드를 호출할 객체를 인자로 넘기기 때문에 메소드 내부에서 호출 객체를 참조할 수 있다. → 런타임에서 호출하는 객체도 결정된다.

```java
public class Test {
    public static void main(String[] args) {
        A a = new C();
        a.print();
    }
}

class A {
    public A() {
        System.out.println("부모 클래스 호출!");
    }

    public void print() {
        System.out.println("부모 클래스 print() 호출!");
    }
}

class B extends A {
    public B() {
        System.out.println("B 클래스 호출!");
    }

    @Override
    public void print() {
        System.out.println("B 클래스 print() 호출!");
    }
}

class C extends A {
    public C() {
        System.out.println("C 클래스 호출!");
    }

    @Override
    public void print() {
        System.out.println("C 클래스 print() 호출!");
    }
}

/* 출력 결과
부모 클래스 호출!
C 클래스 호출!
C 클래스 print() 호출!
*/
```

### ■ 추상 클래스

추상 클래스는 `abstract`를 붙여 선언할 수 있고, 추상 메서드를 포함할 수도, 안할 수도 있다.

추상 메서드는 어떠한 구현도 없이 선언된 메서드다.

```java
abstract void moveTo(double dX, double dY);
```

#### 특징

- 추상 클래스는 `인스턴트화`할 수 없다.
- 추상 메서드를 포함하려면 클래스는 무조건 추상 클래스로 선언되어야 한다.
- 추상클래스를 상속할 때, 하위 클래스는 보통 상위 클래스에 있는 추상 메서드에 대한 구현을 제공한다.

### ■ final 키워드

변수, 메서드, 클래스에 적용될 수 있으며, 적용되는 대상에 따라 다른 역할을 수행한다.

- final 변수 : 변수의 재할당을 막기 위함
- final 메서드 : 메서드 오버라이딩을 막기 위함
- final 클래스 : 클래스 상속을 막기 위함

#### final 변수

- final 키워드가 변수의 앞에 붙으면, 해당 변수는 수정될 수 없다.
- 반드시 선언시에 초기화 값을 넣어주어야 한다.
- final 변수가 참조변수일 경우에는 해당 참조값이 가리키는 인스턴스가 달라질 수 있다.

#### final 메서드

final 클래스란 다른 클래스로 상속될 수 없는 클래스를 말한다.

- 상속을 방지하기 위함
- 불변 클래스를 만들기 위함

#### final 클래스

- final키워드가 붙은 메서드이며, 자식 클래스에서 오버라이딩 할 수 없다.
- Object 클래스의 getClass(), wait(), notify() 등


### ■ Object 클래스

자바 클래스 구조의 최상위에 있는 클래스로 모든 클래스의 부모클래스로 존재한다.

- java.lang 패키지에 존재
- 이 패키지들은 import가 생략 가능
- Object 클래스는 모든 클래스의 최고 조상
- 멤버변수는 없고 오직 11개의 메소드만 갖고 있다.