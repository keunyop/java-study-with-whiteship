# 14주 차: 제네릭

## 목표

자바의 제네릭에 대해 학습하세요.

## 학습할 것

- 제네릭 사용법

- 제네릭 주요 개념 (바운디드 타입, 와일드 카드)
- 제네릭 메소드 만들기
- Erasure

---

### ■ 제네릭 사용법

제네릭이란 클래스 내부에서 사용할 데이터 타입을 인스턴스로 생성할 때 확정해주고 타입 체크를 할 때 Generic을 사용한다.
제너릭을 사용할려면 선언하려는 클래스 옆에 <>안에 데이터 타입을 사용하고 <>안에 지정된 데이터 타입으로 T의 데이터 타입이 결정된다.
java5 부터 사용할 수 있다.
컬렉션이 담을 수 있는 타입을 컴파일러에 미리 알려줄 수 있다.
그래서 컴파일러는 알아서 형변환 코드를 추가할 수 있게 되고, 엉뚱한 타입의 객체를 넣으려는 시도를 컴파일 과정에서 차단하여 더 안전하고 명확한 프로그램을 만들어 준다.

```java
class Person<T> {
    public T name;
    private String age;
    
    public String getAge() {
        return age;
    }
    
    public void setAge(String age) {
        this.age = age;
    }
    
    public T getName() {
        
        return name;
    }
    
    public void setName(T name) {
        this.name = name;
    }
}
```


### ■ 제네릭 주요 개념 (바운디드 타입, 와일드 카드)

#### 와일드 카드

- 와일드카드란 카드 게임에서 유래된 용어로 카드 플레이어가 자기 맘대로 사용할 수 있는 만능 카드를 의미한다. 컴퓨터 용어에서는 이보다 좀 더 확장된 개념으로 사용하는데 주로 패턴을 정의할 때 많이 사용하며 ‘전체’ 의 의미로 쓰이거나 특정 문자에 따라 조건이 지정된다는 뜻으로 쓰인다.

- 주로 잘 알려진 와일드카드는 ‘?’ 와 ‘*’ 인데 제네릭에서는 ‘?’ 만 와일드카드로 사용할 수 있다.

#### 바운디드 타입

- 와일드카드에서 특정 타입으로 제한하는 것을 바운드 타입 파라미터라고 한다.

```java
public class GenericBoundExample<T extends Vehicle> {
    private T vehicleType;
    
    public void setVehicleType(T vehicleType) {
        this.vehicleType = vehicleType;
    }
    
    public T getVehicleType() {
        return vehicleType;
    }
}
```

### ■ 제네릭 메소드 만들기

매개 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드

```java
public class Util {

    public static <K, V> GenericMap<K, V> createGenericMap(K[] keyArr, V[] valueArr) {
        GenericMap<K, V> gMap = new GenericMap<>();
        for (int i = 0; i < keyArr.length; i++) {
            gMap.put(keyArr[i], valueArr[i]);
        }
        return gMap;
    }

    public static <K, V> boolean equalsHeadAndTail(GenericMap<K, V> gMap1, GenericMap<K, V> gMap2) {
        boolean equalsKey = gMap1.getHead().getKey().equals(gMap2.getHead().getKey()) && gMap1.getTail().getKey().equals(gMap2.getTail().getKey());
        boolean equalsValue = gMap1.getHead().getValue().equals(gMap2.getHead().getValue()) && gMap1.getTail().getValue().equals(gMap2.getTail().getValue());

        return equalsKey && equalsValue;
    }
}
```


### ■ Erasure