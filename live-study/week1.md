# 1주차: JVM은 무엇이며 자바 코드는 어떻게 실행하는 것인가.

## 목표

자바 소스 파일을 JVM으로 실행하는 과정 이해하기

## JVM이란 무엇인가?

JVM은 자바 가상 머신 (Java Virtual Machine)을 뜻하는 말로 바이트코드를 실행하는 주체이다.

Java Complier는 .java 파일을 .class라는 java 바이트코드로 변환한다.
바이트코드는 기계어가 아니기 때문에 OS에서 바로 실행이 되지 않기 때문에 JVM을 OS가 바이트코드를 이해할 수 있도록 해석해 주는 역할을 한다.

JVM을 해석을 거치기 때문에 c언어와 같은 네이티브 언어에 비해 속도가 느렸지만 JIT(Just In Time) 컴파일러를 구현해 개선했다.

OS에 종속적이지 않고 Java 파일 하나만 만들면 어느 디바이스든 JVM 위에서 실행할 수 있다.

JVM은 크게 Class Loader, Runtime Data Areas, Excution Engine, Garbage Collector 4가지로 구성되어 있다.

## 컴파일 하는 방법

자바 소스를 컴파일 및 실행하기 위해서는 기본적으로 javac.exe, java.exe 두 프로그램이 필요하다.

javac.exe는 자바 소스코드를 컴파일 할때 사용하는 프로그램이며 컴파일된 바이트코드를 실행할 때 java.exe. 사용한다.

javac.exe는 JDK, java.exe 는 JRE에 포함되어 있기에 JDK과 JRE를 설치해야 하지만 과거와 다르게 요즘은 JDK에 JRE가 포함된 형태로 배포되고 있기에 JDK만 설치해도 무관하다.

## 실행하는 방법

java.exe는  자바 인터프리터로서 컴파일러로 생성된 바이트 코드를 해석하고 실행한다.

## 바이트코드란 무엇인가

- JAVA bytecode란 자바 가상 머신이 이해할 수 있는 언어로 변환된 자바 소스 코드를 의미
- 자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 1바이트라서 자바 바이트코드라 불림
- 자바 바이트코드의 확장자는 .class
- 자바 바이트코드는 JVM만 설치되어 있으면 어떤 OS든 실행될 수 있음
- 자바 프로그램 실행 과정

## JIT 컴파일러란 무엇이며 어떻게 동작하는지

JIT 컴파일러란 기존 클래스파일(바이트코드)를 실행하는 방법은 Interpreter 방식이 기본이다. Interpreter 방식은 3-1에서 설명한바와 같이 명령어를 하나씩 해석해서 처리하는 개념이기 때문에 명령어 하나하나 실행하는 속도는 빠를지 모르나 전체 코드 관점에서 보면 실행 속도가 느린 단점이 있다. 해당 문제를 해결하기 위해서 나온 방법이 JIT 컴파일러이고
JIT 컴파일러는 런타임 시 클래스파일(바이트코드)를 네이티브 기계어로 한방에 컴파일 후 사용하는 개념으로 이해하는 것이 편하다.


## JVM 구성 요소

JVM은 크게 Class loader, Runtime Data Areas, Execution Engine으로 나누어집니다. 먼저 Class loader은 실행하는 시점에 자바로 코드를 컴파일하여 나온 .class형식의 Java byte code를 메모리에 로드하게 해준다.

다음으로 Runtime Data Areas는 프로그램을 수행하기 위해 OS로 부터 별도로 할당받은 메모리 공간을 의미합니다 이것은 또 크게 PC 레지스터, JVM stack, Native Method Stack, Method Area, Heap의 5가지 영역으로 나누어진다.

## JDK와 JRE의 차이

- JDK (Java Development Kit)

- JRE (Java Run-time Environment)

- JDK가 더 큰 개념 