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

열거형 상수가 선언된 순서대로 포함된 배열을 반환한다. 이 메서드는 상수의 반복문을 통해 하나하나 값을 반환하는 형태로 풀어나갈 수 있다.

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

java.lang 에 포함된 Enum 클래스는 모든 자바 열거형의 조상이다. 
모든 열거형은 Enum 클래스를 상속받기 때문에 enum type은 별도의 상속을 받을 수 없다.

```java
public abstract class Enum<E extends Enum<E>>
        implements Constable, Comparable<E>, Serializable {
        
    private final String name;
    
    private final String name() {
        return name;
    }
}
```

### ■ EnumSet

EnumSet은 열거형 타입 상수들을 하나의 배열처럼 사용할 수 있게 해준다. 
EnumSet은 비트 연산을 이용하기 때문에 메모리의 공간을 작게 차지할 뿐만 아니라 속도면에서 빠르다.
EnumSet은 new 연산자를 이용해 선언할 수 없기 때문에 EnumSet.allOf(열거형 클래스.class); 형식으로 선언할 수 있다.

```java
public class EnumSetTest {
    public static void main(String[] args) {
				
				// EnumSet 선언
        EnumSet<Month> enumSet = EnumSet.allOf(Month.class);

        // EnumSet을 비우는 메소
        enumSet = EnumSet.noneOf(Month.class);

        // EnumSet.of() : 파라미터로 전달되는 열거형 상수를 제외한 상수를 담아 배열로 리턴하는 메소드
        enumSet = EnumSet.of(Month.JANUARY);

        // 파라미터로 들어오는 EnumSet을 제외한 상수를 담아 배열로 리턴
        enumSet = EnumSet.complementOf(enumSet);

        // 파라터로 전해지는 범위의 열거형 상수를 담아 배열로 리턴
        enumSet = EnumSet.range(Month.JANUARY,Month.JUNE);
    }
}
```