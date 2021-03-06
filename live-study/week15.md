# 15주 차: 람다식

## 목표

자바의 람다식에 대해 학습하세요.

## 학습할 것

- 람다식 사용법

- 함수형 인터페이스
- Variable Capture
- 메소드, 생성자 레퍼런스

---

### ■ 람다식 사용법

```java
public class LambdaDemo {

    public static void main(String[] args) {

        Thread thread = new Thread(() -> System.out.println(Thread.currentThread().getName()));
        thread.start();
    }

}
```

#### 람다식 특징

// return void
1. (Integer a) -> System.out.println(a);
2. (a) -> { System.out.println(a) };
3. a -> System.out.println(a);

// return value
4. (a, b) -> a + b; // return a + b;
5. (a, b) -> {System.out.println(a+b); return a+b;}

- 매개변수 타입도 표기가 가능하나 일반적으로 언급하지 않는다.

- 하나의 매개변수 일경우 () 생략이 가능하다.
- 실행문(Body) 가 하나일 경우 {} 생략이 가능하다.
- return type이 있을때, 실행문(Body)가 하나일 경우 return 예약어 생략이 가능하다.

### ■ 함수형 인터페이스

함수형 인터페이스는 단 하나의 추상 메소드만이 선언된 인터페이스 이다.

```java
MyFunction f = new MyFunction() {
                   public int plus(int x, int y) {
                        return x + y;
                   }
              };
f. plus(1,2);
```

```java
MyFunction f = (int x, int y) -> x + y;
f.plus(1,2);
```

인터페이스를 구현한 익명 객체를 람다식으로 표현할 수 있는 이유는 람다식도 사실 익명 객체이고,
인터페이스를 구현한 익명 객체의 메서드 plus와 람다식이 매개변수 타입, 개수, 반환값이 일치하기 때문이다.

반드시 함수형 인터페이스에는 오직 하나의 추상 메서드만 정의되어 있어야한다.
왜냐하면 람다식과 인터페이스의 메서드가 1:1로 연결되어야 하기 때문이다.

### ■ Variable Capture

### ■ 메소드, 생성자 레퍼런스