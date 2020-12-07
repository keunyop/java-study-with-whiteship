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
```s



## 반복문