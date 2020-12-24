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

```
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

```
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