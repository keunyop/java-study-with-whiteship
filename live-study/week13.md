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

두 클래스는 Byte Stream의 입력과 출력을 담당하는 클래스이다.

##### InputStream의 경우 ByteArrayInputStream을 구현체로 사용하였다.

- read()
- read(byte[] b)
- read(byte[] b, int off, int len)Permalink
- close()

##### OutputStream의 경우, FileOutputStream을 구현체로 사용하였다.

- write(int b)
- write(byte[] b)
- write(byte[] b, int off, int len)
- flush()
- close()

### ■ Byte와 Character 스트림

#### Byte 스트림

자바의 스트림은 기본적으로 Byte 단위로 스트림을 전송하며 입출력 대상에 따라 제공하는 클래스가 다르다. 또한, 그림, 멀티미디어, 문자 등 모든 종류의 데이터를 주고받을 수 있다는 특징을 가지고 있다.

- FileInputStream / FileOutputStream : 파일 입출력 대상

- ByteArrayInputStream / ByteArrayOutputStream : 메모리 입출력 대상
- PipedInputStream / PipedOutputStream : 프로세스 입출력 대상
- AudioInputStream / AudioOutputStream : 오디오 장치 입출력 대상

#### Character 스트림

자바에서 가장 작은 타입인 char 형이 2바이트이므로, 1바이트씩 전송되는 바이트 기반 스트림으로는 원활한 처리가 힘든 경우가 있다. 이러한 경우를 해결하기 위해 자바는 문자 기반 스트림을 지원한다. 문자 기반 스트림은 오직 문자 데이터를 주고받기 위해 존재하는 스트림으로 문자 데이터를 입출력 할 때 사용하는 스트림이다. Reader와 Writer 클래스를 상속받아 사용한다.

- FileReader / FileWriter : 파일 입출력 대상

- CharArrayReader / CharArrayWriter : 메모리 입출력 대상
- PipedReader / PipedWriter : 프로세스 입출력 대상
- StringReader / StringWriter : 문자열 입출력 대상

### ■ 표준 스트림 (System.in, System.out, System.err)

표준 스트림이란 프로그램과 입출력 사이에 연결된 입출력 스트림을 의미한다.

#### System.in

콘솔로부터의 입력을 받는 표준 스트림을 가리키는 상수이다. 해당객체는 JVM 이 메모리에 올라갈때 생성된다고 한다. InputStream 으로 byte 단위로 입력을 받을 수 있다.

#### System.out

콘솔로 출력을 하는 표준 스트림을 가리키는 상수이다.
대표적인 사용의 예시로 System.out.println() 을 생각해볼 수 있다.

#### System.err

표준 에러 출력 장치를 가리키는 상수이다

### ■ 파일 읽고 쓰기

#### 파일 쓰기

```java
public class FileWriterExample {

    public static void main(String[] args) {
        try(
            FileWriter writer = new FileWriter("FileWriter.txt", true);
            BufferedWriter bufferedWriter = new BufferedWriter(writer);
        ) {
            bufferedWriter.write("Java Study");
            bufferedWriter.newLine();
            bufferedWriter.write("Week 13");
            bufferedWriter.newLine();
            bufferedWriter.flush();
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
}
```

#### 파일 읽기

```java
public class FileReaderExample {

    public static void main(String[] args) {
        try(
                FileReader reader = new FileReader("FileWriter.txt");
                BufferedReader bufferedReader = new BufferedReader(reader);
        ) {
            String readLine = null;
            while( ( readLine =  bufferedReader.readLine()) != null ){
                System.out.println(readLine);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```