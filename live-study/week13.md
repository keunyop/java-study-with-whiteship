# 13주 차: I/O

## 목표

자바의 Input과 Ontput에 대해 학습하세요.

## 학습할 것

- 스트림 (Stream) / 버퍼 (Buffer) / 채널 (Channel) 기반의 I/O

- InputStream과 OutputStream
- Byte와 Character 스트림
- 표준 스트림 (System.in, System.out, System.err)
- 파일 읽고 쓰기

---

### ■ 스트림 (Stream) / 버퍼 (Buffer) / 채널 (Channel) 기반의 I/O

#### 스트림 (Stream)

실제의 입력이나 출력이 표현된 데이터의 이상화된 흐름을 말하며, 자바에서는 파일이나 콘솔에서의 입출력을 스트림을 통해 다룬다. 스트림은 한 방향으로만 통신이 가능하기 때문에 입력과 출력을 동시에 처리할 수 없다.

#### 버퍼 (Buffer)

채널과 상호작용할 때 사용되는 것으로 데이터는 채널에서 버퍼로 읽어지거나 버퍼에서 읽혀 채널로 쓰여진다.

#### 채널 (Channel) 기반의 I/O

NIO에서는 채널을 통해 데이터를 읽고 쓴다.

### ■ InputStream과 OutputStream

### ■ Byte와 Character 스트림

### ■ 표준 스트림 (System.in, System.out, System.err)

### ■ 파일 읽고 쓰기