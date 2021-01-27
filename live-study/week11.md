# 11주 차: Enum

## 목표

자바의 열거형에 대해 학습하세요.

## 학습할 것

- enum 정의하는 방법

- enum이 제공하는 메소드 (values()와 valueOf())
- java.lang.Enum
- EnumSet

---

### ■ enum 정의하는 방법

```java
public enum Day {
  MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```


### ■ enum이 제공하는 메소드 (values()와 valueOf())

#### values()

열거형 상수가 선언된 순서대로 포함된 배열을 반환한다. 이 메서드는 상수의 반복문을 통해 하나 하나 값을 반환하는 형태로 풀어나갈 수 있다.

```java
for(Direction c : Direction.values()) {
	System.out.println(c);
}
```

#### valueOf()

두 가지 종류의 valueOf 메서드가 있다. 

- Enum 클래스에서도 사용 가능한 static 메서드이고 이는 인자로 Class 타입과 String으로 표현된 상수명을 받아 해당 상수를 반환

- 정의된 열거형 타입에서만 사용가능하며 인자로 String으로 표현된 상수명을 받아 해당 상수를 반환

### ■ java.lang.Enum

### ■ EnumSet