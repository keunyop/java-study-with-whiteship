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

### ■ 제네릭 메소드 만들기

### ■ Erasure