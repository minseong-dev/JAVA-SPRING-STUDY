# 예외처리

## 프로그램 오류

- 프로그램이 실행 중 어떤 원인에 의해 오작동을 하거나 비정상적으로 종료되는 경우가 있는데 이런 결과를 초래하는 원인을 프로그램 에러 또는 오류라고 한다.

## Error, Exception

### Error

- 코드에 의해 수습이 될 수 없는 심각한 오류

### Exception

- 코드에 의해 수습될 수 있는 미약한 오류

### 에러의 종류

### Compillation error

- 문법 오류로 인해 컴파일 시 발생하는 에러
    
    (Ex) 맞춤법, 문장부호( ; ), 선언되지 않은 변수 사용
    

### Runtime error

- 프로그램 실행 중 발생하는 에러
- JVM에서 여러 메세지가 출력됨 ( XXXException 에러)
- unchecked 예외 → 컴파일러가 예외처리를 확인하지 않음

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/85557b57-f673-4345-ad24-346d20a15049/Untitled.png)

### Logical Error

- 실행은 되지만, 의도와 다르게 동작하는 것
- 에러 메세지가 없어 수정이 어렵다.

## 예외처리 with try-catch

- 정의 : 프로그램 실행 시 발생할 수 있는 예외에 대비한 코드를 작성하는 것
- 목적 : 프로그램의 비정상 종료를 막고, 정상적인 실행 상태를 유지하는 것

```java
try{
	//예외가 발생할 가능성이 있는 코드
}catch(Exception1 e1){
	//Exception1이 발생했을 경우, 이를 처리하기 위한 코드
}catch(Exception2 e2){
	//Exception2가 발생했을 경우, 이를 처리하기 위한 코드
}

발생한 예외의 종류와 일치하는 catch블럭이 없으면 예외는 처리되지 않음
//if문과 달리 try혹은 catch블럭 내ㅑ에 포함된 문장이 하나뿐이어도 괄호{}를 생략할 수 없다.
```

### try블럭 내에서 예외가 발생한 경우

1. 발생한 예외와 일치하는 catch 블럭이 있는지 확인
2. 일치하는 catch 블럭을 찾으면 해당 catch 블럭에서 문장들을 수행하고 전체 try-catch 문을 빠져나가서 다음 문장을 계속 수행, 일치하는 블럭을 못찾으면 예외 처리되지 못함.

### 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a4b29839-39b8-41e3-a578-fcc41649134a/Untitled.png)

### catch 활용

```java
catch(Exception e){ }

catch(ArtihmeticException ae) { }

catch(NullPointerException npe) { }
```

- Exception 클래스를 참조변수로 선언하면 모든 예외상황을 잡아낼 수 있다.
- 예외에 따라 다른 처리를 해야할 경우에는 해당하는 예외클래스를 선언하여 사용

## getMessage(), printStackTrace(), toString()

### e.getMessage()

- 간단하게 왜 에러가 발생하였는지 보여줌

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/213031ad-52f6-4667-994b-abf927fdccc7/Untitled.png)

### e.toString()

- 발생한 Exception의 유형과 원인, 이유를 보여줌
- 발생한 위치는 알려주지 않음

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b31e480-0dad-4986-9cb8-65cf246218d8/Untitled.png)

### e.printStackTrace()

- 발생한 Exception의 유형, 원인, 이유, 위치를 포함한 전체적인 단계를 다 출력함.
- 빠르게 파악이 가능함.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7778fb14-84db-441f-ac90-9002bbfb60aa/Untitled.png)

## method Exception

```java
void method() throws Exception1, Exception2, ... ExceptiopN{}

void method() throws Exception{} //모든 종류의 예외가 발생할 가능성이 있음
```

- 메서드 선언부에 예외를 선언함으로써 메서드를 사용하기 위해 처리되어야할 예외를 쉽게 알 수 있도록 함.
- 견고한 프로그램 코드를 작성할 수 있도록 도와줌

## finally

- 예외 발생여부와 관계없이 실행되어야할 코드를 포함시킬 목적으로 사용
- try-catch-finally 순으로 구성

```java
try{
	startInstall(); //파일 설치
	copyFiles(); // 파일 복사
	deleteTempFile(); //설치에 사용된 임시파일 삭제
catch(Exception e){
	e.printStackTrace();
	deleteTempFile(); //설치에 사용된 임시파일 삭제
}

try{
	startInstall(); //파일 설치
	copyFiles(); // 파일 복사
catch(Exception e){
	e.printStackTrace();
}finally{
	deleteTempFile(); //설치에 사용된 임시파일 삭제
}
```

## try-with-resource

- JDK1.7부터 추가