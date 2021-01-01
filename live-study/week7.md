# 7주차: 패키지

## 목표

자바의 패키지에 대해 학습하세요.

## 학습할 것
- package 키워드
- import 키워드
- 클래스패스
- CLASSPATH 환경변수
- classpath 옵션
- 접근지시자

### ■ package 키워드

자바의 패키지란 비슷한 성격의 클래스를 모아서 만든 자바의 디렉토리이다.

자바에서는 다수의 클래스를 정의하기 때문에 애플리케이션에서 클래스를 정리할 필요가 있다. 그래서 이를 정리하기 위해 패키지를 사용한다.

#### 패키지의 특성

- 자바는 패키의 가장 상위 디렉토리에서 실행
- 소스 코드 맨 첫 줄에 있어야하고, 패키지 선언은 소스 코드에 단 하나만 있어야함
- 패키지 이름과 위치한 폴더는 동일 해야함
- 패키지 이름은 'java'로 시작하면 안됨

### ■ import 키워드

#### import 패키지명.클래스이름

import 문이 작성되는 위치는 패키지 선언가 클래스 선언의 사이이다.
만약 그 패키지안에 있는 모든 클래스를 한거번에 import 해서 사용하고 싶다면 ' * ' 를 사용하도록 하자 .

```java
package org.example; //패키지 선언

import org.example.test2.Apple; // import 선언 Apple 클래스 사용
import org.example.test2.*; // import 선언 test2 안에 있는 모든 클래스 사용

public class App // 클래스 선언
{
    Apple apple = new Apple();
}
```

### ■ 클래스패스

클래스패스는 컴파일러나 JVM 등이 클래스의 위치를 찾는데 사용되는 경로이다.

클래스패스는 환경변수 또는 옵션을 통하여 사용할 수 있다.


### ■ CLASSPATH 환경변수

환경변수란, OS에서 참고하고 있는 변수이다. 프로그래밍에서 변수를 사용하여 동적인 동작을 할 수 있듯 프로세스는 환경변수를 보고 자신이 해야할 동작을 결정한다.

이러한 환경변수들 중에 CLASSPATH 라는 변수를 설정할 수 있으며 이는 JVM이 구동될 때 클래스 로더가 이 변수를 호출하여 해당 경로 안에 클래스들을 로드한다. 환경변수를 설정하면 실행 시에 따로 설정을 하지 않아도 된다는 장점이 있다.

### ■ classpath 옵션

`javac <options> <souce files>`

컴파일러가 컴파일 하기 위해서 필요로 하는 참조할 클래스 파일들을 찾기 위해서 컴파일시 파일 경로를 지정해주는 옵션이다.

만약 `Hello.java`파일이 `C:\Java` 디렉터리에 존재하고, 필요한 클래스 파일들이 `C:\Java\Engclasses`에 위치한다면,`javac -classpath C:\Java\Engclasses C:\Java\Hello.java` 로 해주면 된다.

만약 참조할 클래스 파일들이 그 외의 다른 디렉터리, 그리고 현 디렉토리에도 존재한다면,`javac -classpath .;C:\Java\Engclasses;C;\Java\Korclasses C:\Java\Hello.java` 과 같이`;` 으로 구분해줄 수 있다. ( `.` 은 현 디렉토리, `..` 은 현 디렉토리에서 상위 디렉토리를 의미한다.)

또한 classpath 대신 단축어인 cp를 사용해도 된다.

`javac -cp .;C:\Java\Engclasses;C;\Java\Korclasses C:\Java\Hello.java`



### ■ 접근지시자

- public: 모든 접근 허용, 어떤 클래스가 접근을 하든 모두 허용 됨

- protected: 상속 받은 클래스 또는 같은 패키지에서만 접근 가능
- default: 자신 클래스 내부와 같은 패키지 내에서만 접근 가능
- private: 외부 접근 불가능, 같은 클래스 내에서만 접근 가능