# 10주차: 멀티 쓰레드 프로그래밍

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

- NEW: 스레드가 생성되었지만 아직 실행되지 않음.

- RUNNABLE: 스레드가 JVM에 의해 실행되고 있거나, 실행 준비 되어 스케쥴링 기중.
- WAITING: 다른 스레드가 notify(), notifyAll()을 호출하는 것을 대기중. 보통 스레드 동기화를 위해 사용한다.
- TIMED_WAITING: 스레드가 sleep()을 호출하여 일시중지된 상태.
- BLOCK: 스레드가 I/O작업 요청을 하면 자동으로 변경되는 상태.
- TERMINATED: 스레드 종료.

### ■ 쓰레드의 우선순위

쓰레드의 우선순위 방식은 우선 순위를 정하고 높은 우선 순위를 가진 쓰레드가 우선 실행된다. 1 ~ 10 까지 정할 수 있으며, 10이 가장 높다. 우선 순위를 할당하지 않으면 기본 값으로 5로 설정된다.

쓰레드 클래스에서는 MAX_PRIORITY, NORM_PRIORITY, MIN_PRIORITY라는 상수 값을 가지고 있으며 각각 10, 5, 1을 가리킨다.

```java
Thread thread1 = new Thread(() -> System.out.println("Thread 1"));
Thread thread2 = new Thread(() -> System.out.println("Thread 2"));
Thread thread3 = new Thread(() -> System.out.println("Thread 3"));

thread1.setPriority(Thread.MAX_PRIORITY);
thread2.setPriority(Thread.NORM_PRIORITY);
thread3.setPriority(Thread.MIN_PRIORITY);

System.out.println(thread1.getPriority());	// 10
System.out.println(thread2.getPriority());	// 5
System.out.println(thread3.getPriority());	// 1
```

### ■ Main 쓰레드

자바에서 메인 메소드를 통해 프로그램이 실행되면 하나의 쓰레드가 시작되는데 이를 메인 쓰레드 라고 부른다.

우리가 만든 프로그램을 실행하면 JVM에선 자동으로 메인 쓰레드를 생성해준다.

- currentThread() 를 호출하면 해당 쓰레드의 참조값을 가져올 수 있다.
- getName()를 호출하면 currentThreadI()로 가져온 현 쓰레드의 Name 값을 알 수 있다.

```java
public class MainThreadTest {
    public static void main(String[] args) {
        Thread thread = Thread.currentThread();
        System.out.println(thread.getName()); // main
    }
}
```

### ■ 동기화

여러 개의 Thread가 한 개의 자원을 사용하고자 할 때, 해당 Thread만 제외하고 나머지는 접근을 못하도록 막는 것

```java
synchronized(객체의 참조변수) {

}

public synchronized void cal() {
        
}
```



### ■ 데드락

- 데드락은 운영체제나 소프트웨어가 자원을 효율적으로 배분하지 못해 프로세스가 멈춰버리는 현상이다. 

- 이러한 상태에서는 프로그램을 강제로 종료하는 방법 뿐이다. 
- 멀티 스레드 프로그래밍 환경에서 서로 다른 스레드가 지속적으로 얻으려고 하면서 충돌이 일어나고 무한 대기 상태에 빠지게 된다. 
- 이 문제를 예방하기 위해서는 스레드 코드 순서를 조정해주면서 우선순위 혹은 순환 할당으로 스레드가 동시에 많이 일어나지 않게 하면 된다. 
