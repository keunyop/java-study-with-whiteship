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

### ■ Variable Capture

### ■ 메소드, 생성자 레퍼런스