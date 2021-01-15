# 9주차: 예외 처리

## 목표

자바의 예외 처리에 대해 학습하세요.

## 학습할 것

- 자바에서 예외 처리 방법 (try, catch, throw, throws, finally)

- 자바가 제공하는 예외 계층 구조
- Exception과 Error의 차이는?
- RuntimeException과 RE가 아닌 것의 차이는?
- 커스텀한 예외 만드는 방법

---

### ■ 자바에서 예외 처리 방법 (try, catch, throw, throws, finally)

#### try-catch-finally

```java
try {
	// 예외가 발생할 수 있는 코드
} catch (예외클래스1 변수명) {
	// 예가 발생했을 때 해당 예외를 처리할 수 있는 코드
} catch (예외클래스2 변수명) {
	// 예가 발생했을 때 해당 예외를 처리할 수 있는 코드
} finally {
	// 예외 발생 여부 상관 없이 항상 실행되는 코드
}
```

#### catch

catch는 하나 이상 있을 수 있음

#### finally

생략가능

#### Throws

메서드 throws 예외 클래스 이름

```java
public static void main(String[] args) throws IOException {
    byte[] receive = new byte[64];
    Read(receive);
}

private static void Read(byte[] buffer) throws IOException {
    System.in.read(buffer);
}
```

반드시 시그니쳐 옆에 추가해야함
checked 예외를 던지는 메서드
다른 메서드에서 발생한 checked 예외를 처리하지 않는 메서드
추가 안하면 컴파일 오류

#### 예외 처리시 주의 사항

```java
try {

} catch (Exception e) {

} catch (ArithmeticException e) {
	// 자식 예외 클래스가 실행되지 못한다
}
```

부모 예외 클래스가 자식보다 먼저 나오면 안된다.

### printStackTrace()

현재 발생한 예외의 호출 스택을 보여줌

### 예외 발생시 진행 순서

1. try 블록 실행이 중단

2. catch 블록 중에 예외를 처리할 수 있는지 찾음

3. 예외를 처리할 수 있는 catch 블록이 없으면 finally 블록을 실행 후, 한 단계 높은 try 블록으로 전달

4. 예외를 처리할 수 있는 catch 블록이 있으면 catch 안의 코드 실행 fianlly 블록 실행

### RuntimeException의 생성자

```java
public RuntimeException() {
    super();
}

public RuntimeException(String message) {
    super(message);
}

public RuntimeException(String message, Throwable cause) {
    super(message, cause);
}

public RuntimeException(Throwable cause) {
    super(cause);
}

protected RuntimeException(String message, Throwable cause,
                            boolean enableSuppression,
                            boolean writableStackTrace) {
    super(message, cause, enableSuppression, writableStackTrace);
}
```

자식 클래스 생성자에서 반드시 super() 호출해야함

호출을 안하면 message, cause가 저장되지 않음



#### try-with-resource

```java
try (InputStream is = new FileInputStream(file)) {
     // 필요한 코드 실행
} catch (Exception e) {
    //예외 발생 시, 예외에 대한 처리
}
```


### ■ 자바가 제공하는 예외 계층 구조

- 최상위는 Object 클래스이다.

- 에러클래스와 예외클래스는 Throwable 클래스 에서 상속받는다.

### ■ Exception과 Error의 차이는?

Error는 시스템에서 발생하는 문제이고 Exception은 구현한 로직에서 발생하는 문제이다.

컴파일 시점에 발생하는 에러를 컴파일 에러라고하고 런타임 시점에 발생하는 에러를 런타임 에러라고 한다.

런타임 시점에서 발생하는 에러 중 시스템 레벨에서 발생한 에러가 아닌 로직 내에서 발생한 에러, 즉 처리 가능한 에러를 예외라고 한다.

### ■ RuntimeException과 RE가 아닌 것의 차이는?

RuntimeException은 UncheckedException에 속한다. 오로지 개발자의 경험에 의해서 예외 처리 코드를 작성해야 된다. 그럼으로써 실행 예외를 잘 익혀두어야 된다. 

Exception(일반예외)과 RuntimeException(실행예외) 클래스를 구별하는 방법은 일반 예외는 Exception을 상속 받고 실행 예외는 RuntimeException을 상속받는다. RuntimeException도 Exception을 상속받지만 JVM은 RuntimeException을 상속했는지 여부를 보고 실행 예외를 판단한다. 

### ■ 커스텀한 예외 만드는 방법

```java
public class CustomException extends Exception{
    CustomException(String msg){
        super(msg);
    }
}
```