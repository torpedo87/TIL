# java 컴파일

1. Helloworld.java (소스코드)
2. javac Helloworld.java
3. Helloworld.class (byte 코드)
4. java Helloworld
---

# eclipse

1. src 폴더 - 소스코드 저장(.java)
2. bin 폴더 - byte 코드 저장(.class)
3. eclipse에서 소스코드 저장하면 자동으로 .class파일 생성

---

# 데이터타입

## 데이터타입이 용량을 결정
8 bit = 1 byte
1024 byte = 1 kilobyte
1024 kilobyte = 1 megabyte
1024 megabyte = 1 gigabyte
1024 gigabyte = 1 terabyte

## 숫자
1. 정수형 int (4byte)
byte < short < int < long

2. 실수형 double (8byte)
float < double

## 문자 char (2byte)
문자(chracter) // '문'
문자열(string) // "문자열", "문"
문자열 내부에 큰따옴표 써야될 경우 // \"
줄바꿈 // \n

## 변수
### 변수의 효용
1. 중복의 제거
2. 가독성


## 상수
```java
double a = 2.2;   //소수인 상수는 자동적으로 double 타입을 갖는다
float b = 2.2F;
long c = 2147483648L;   //상수가 int 범위를 넘어서도 자동적으로 int타입이므로 L 붙여줘야한다
```

## 형변환
1. 자동형변환
더 큰 범위의 데이터타입으로 전환시 손실 없으므로 가능
```java
double a = 3.0F   //3.0 이 자동으로 double로 형변환됨(double이 더 큰범위이므로 손실 없으므로)
// char 의 범위 = short의 범위
int a = 3;
float b = 1.0F;
double c = a + b;
```

2. 명시적 형변환
앞에 ()를 이용해서 데이터타입을 지정해준다
```java
floata = (float)100.0;
intb = (int)100.0F;
int a = 10;
int b = 3;
float c = 10.0F;
float d = 3.0F;
System.out.println(a/b);   //3
System.out.println(c/d);   //3.3333333
System.out.println(a/d);   // 3.3333333
```
---
