# 4주차: 제어문

## 목표

자바가 제공하는 제어문을 학습하세요.

## 선택문

Java는 if/else문(조건문)과 Switch/case문(선택문)을 제공한다.

### if/else 문

if문에 들어가는 조건식이 참인 경우에 if문 내의 블록 코드를 실행한다.

```
int a = 10;
if(a > 5) {   // 조건이 참이므로 코드 실행 
	a += 5;   
}
```

만약 조건식이 거짓인 경우 else if문이 있다면 else if 문의 조건을, else문이 있다면 else문의 코드를 실행한다.

```
int a = 5;
if(a > 5) {
	System.out.println("a가 5보다 큰 경우 코드 실행");
}else if(a < 5) {
	System.out.println("a가 5보다 작은 경우 코드 실행");
}else {
	System.out.println("a가 5인경우 코드 실행");
}
```

또한, if문 내에 다시 if문 사용이 가능하다. 이를 중첩 if문이라 한다.

```
int a = 8;
if(a > 5) {
	if(a < 10) {
		System.out.println("a가 5보다 크고 10보다 작으면 코드 실행");
	}else{
		System.out.println("a가 10이상이면 코드 실행");
	}
}
```

## 반복문

### for문

```
for(초기화; 조건식; 증감식){
	조건식이 true일 경우 수행될 구문을 기재합니다. 
}
```
for문의 구조는 초기화, 조건식, 증감식, 블럭으로 이루어져 있다.

1) 초기화

반복문에 사용될 변수의 초기화로 처음 한번만 수행됩니다. 

둘 이상의 변수 일 경우 ,(콤마)를 이용해서 초기화하며 변수의 타입은 동일해야합니다.

 

2) 조건식

조건식의 조건이 true이면 반복수행하고, false이면 수행을 중단하게 됩니다.

조건식이 true일 경우 {}내부에 구문이 수행됩니다.

 

3) 증감식

반복문을 제어하는 변수의 값을 증가 또는 감소 시키는 것으로, 증감식으로 변수의 값이 변하다가 false가 될 경우 더이상 수행되지 않는다.

증감식도 ,(콤마)를 이용해서 두 문장 이상을 하나로 연결해서 쓸 수 있으며, 초기화, 조건식, 증감식 모두 생략 가능하다.


### for ~ each문

```
//1 2 3 출력	
public static void main(String[] args) {
	int[] Arr = new int[3];
	Arr[0] =1;
	Arr[1] =2;
	Arr[2] =3;
		
    //향상된 For문
	for(int j : Arr) {
		System.out.println(j);
	}
}
```

for ~ each 문은 <향상된 for 문>이라고 불리는 구문으로 자바 5버전부터 추가된 구문입니다. 구문 자체는 배열의 항목수만큼 배열의 항목을 꺼내어 실행한다.

```
enum Face{ ONE, TWO, THREE, FOUR, FIVE, SIX};
    
public static void main(String[] args) {
    Collection<Face> faces = Arrays.asList(Face.values());
        
    for(Iterator<Face> i = faces.iterator(); i.hasNext();) {
        for(Iterator<Face> j = faces.iterator(); j.hasNext();) {
            System.out.println(i.next() + " " + j.next());
        }
    }
}
```

위에 소스는 중첩되는 순환문을 통해 주사위 모든 조합을 출력하기 위한 소스이다. 하지만.. 결괏값을 보면

의도한 바와는 다른 결괏값을 출력함을 알 수 있다.

```
enum Face{ ONE, TWO, THREE, FOUR, FIVE, SIX};

public static void main(String[] args) {
    Collection<Face> faces = Arrays.asList(Face.values());
        
        for(Face face1 : faces) {
            for(Face face2 : faces)
            System.out.println(face1 + "," + face2);
        }
    }
​```

이럴 경우 이렇게 향상된 for 문을 써서 해당 값을 나타낼 수 있다.