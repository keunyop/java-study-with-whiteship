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