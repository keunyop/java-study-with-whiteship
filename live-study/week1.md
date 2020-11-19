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