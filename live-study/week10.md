# 10주차: 멀티쓰레드 프로그래밍

## 목표

자바의 멀티쓰레드 프로그래밍에 대해 학습하세요.

## 학습할 것

- Thread 클래스와 Runnable 인터페이스

- 쓰레드의 상태
- 쓰레드의 우선순위
- Main 쓰레드
- 동기화
- 데드락

---

### ■ Thread 클래스와 Runnable 인터페이스

쓰레드를 구현하는 방법은 Thread 클래스를 상속받는 방법과 Runnable 인터페이스를 구현하는 방법, 2가지가 있다.

둘 중 어느 쪽을 사용해도 별 차이는 없지만 Java에서는 다중 상속을 허용하지 않기 때문에,

Thread 클래스를 상속받으면 다른 클래스를 상속받을 수 없어서 Runnable 인터페이스를 구현하는 방법이 일반적이다.

Runnable 인터페이스를 구현하는 방법은 재사용성이 높고 코드의 일관성을 유지할 수 있다는 장점이 있기 때문에

보다 객체지향적인 방법이라 할 수 있다.

Runnable인터페이스는 run()메소드만 정의되어 있는 간단한 인터페이스이다.

```java
// 1. Thread클래스를 상속
public class MyThread extends Thread {

    // Thread 클래스의 run()을 오버라이딩
    public void run() {
        /* 작업내용 */
    }
}

// 2. Runnable인터페이스를 구현
public class MyThread implements Runnable {
    // Runnable인터페이스의 추상메소드 run()을 구현
    @Override
    public void run() {
        /* 작업내용 */
    }
}
```

### ■ 쓰레드의 상태

### ■ 쓰레드의 우선순위

### ■ Main 쓰레드

### ■ 동기화

### ■ 데드락
