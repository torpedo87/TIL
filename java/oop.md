# 객체지향 프로그래밍

## 개념
객체들을 레고블럭처럼 조립해서 프로그램을 만드는 것
기능별로 객체를 만들어서 관련된 변수와 메소드를 담아서 재활용성을 높인다
class(설계도)를 만들어서 instance(제품)를 생성할때마다 클래스를 재활용할 수 있다
---
## class
설계도(객체= 변수와 메소드를 갖는 작은 프로그램), 사용자 정의 데이터 타입이 될 수 있다
```java
class Calculator{
  int left, right;
  public void setOprands(int left, int right){
    this.left = left;
    this.right = right;
  }
  public void sum(){
    System.out.println(this.left+this.right);
  }
  public void avg(){
    System.out.println((this.left+this.right)/2);
  }
}
```
---
## instance
구체적인 제품(instace = new class)
cl 이라는 인스턴스 생성하기
```java
Calculator c1 = new Calculator();
c1.setOprands(10, 20);
c1.sum();
c1.avg();
```
---

## member
1. class member(static) = 변수, 메소드
2. instance member(nonstatic) = 변수, 메소드
instance 메소드는 class 멤버에 접근할 수 있다
class 메소드는 instance 멤버에 접근할 수 없다

```java
class Calculator3{
  public static void sum(int left, int right){
    System.out.println(left+right);
  }   // class 메소드는 static
  public static void avg(int left, int right){
    System.out.println((left+right)/2);
  }
}

public class CalculatorDemo3 {
  public static void main(String[] args) {
    Calculator3.sum(10, 20);  //class의 메소드를 사용할 때는 굳이 instance 생성하지 않아도 바로 호출가능하다
    Calculator3.avg(10, 20);
    Calculator3.sum(20, 40);
    Calculator3.avg(20, 40);
  }
}
```
---
## scope
변수 선언 = 유효 범위 결정
객체지향 프로그램을 통해 전역변수를 좀 더 맘 편히 사용할 수 있게 됨

### 정적 유효범위
해당 함수를 호출하는 함수의 범위와는 상관없이 해당 함수 자체의 유효범위만 해당
```java
public class ScopeDemo6 {
  static int i = 5;
  static void a() {
    int i = 10;
    b();
  }
  static void b() {
    System.out.println(i);
  }
  // a가 b를 호출한다 해도 i의 유효범위는 a와 무관하게 b의 지역변수 혹은 전역변수만 해당
  public static void main(String[] args) {
    a();
  }
}
```
### this
인스턴스 자신을 의미???
---
## 초기화

### 생성자(constructor)
인스턴스를 생성
```java
class Calculator {
  int left, right;
  public Calculator(int left, int right) {
    //class명과 같은 이름의 method, 반환값이 없다
    this.left = left;
    this.right = right;
  }
  public void sum() {
    System.out.println(this.left + this.right);
  }
  public void avg() {
    System.out.println((this.left + this.right) / 2);
  }
}
```
---
## 상속
*** 필요성
자식객체에 부모객체의 메소드를 중복해서 쓸 필요가 없다
기존의 부모객체를 유지하면서 어떤 기능을 추가하는 자식객체 생성(extends 사용)

```java
//부모class

class Calculator {
  int left, right;
  public void setOprands(int left, int right) {
    this.left = left;
    this.right = right;
  }
  public void sum() {
    System.out.println(this.left + this.right);
  }
  public void avg() {
    System.out.println((this.left + this.right) / 2);
  }
}

//자식 class
class SubstractionableCalculator extends Calculator {
  public void substract() {
    System.out.println(this.left - this.right);
  }
}

public class CalculatorDemo1 {
  public static void main(String[] args) {
    SubstractionableCalculator c1 = new SubstractionableCalculator();
    c1.setOprands(10, 20);
    c1.sum();
    c1.avg();
    c1.substract();
  }
}
```
CLASS에 생성자가 선언되어있지 않을 경우, 이후 INSTANCE(인자 없는 생성자) 생성할 때 자동으로 인자가 없는 생성자(기본 생성자)가 만들어져서 자식객체에서 호출할 수 있다
```java
package org.opentutorials.javatutorials.Inheritance.example4;
public class ConstructorDemo {
  public static void main(String[] args) {
    ConstructorDemo c = new ConstructorDemo();
  }
}
```

하위 클래스가 호출될 때 자동으로 상위 클래스의 기본 생성자를 호출하게 된다. 그런데 상위 클래스에 매개변수가 있는 생성자가 있다면 자바는 자동으로 상위 클래스의 기본 생성자를 만들어주지 않는다. 따라서 존재하지 않는 생성자를 호출하게 되기 때문에 에러가 발생했다. 이 문제를 해결하기 위해서는 아래와 같이 상위 클래스에 기본 생성자를 추가하면 된다.
```java
package org.opentutorials.javatutorials.Inheritance.example4;
public class ConstructorDemo {
  public ConstructorDemo(int param1) {}
    public static void main(String[] args) {
      ConstructorDemo c = new ConstructorDemo();
    }
}
```
### super
 super 키워드는 부모 클래스를 의미한다. 여기에 ()붙이면 부모 클래스의 생성자를 의미하게 된다. 이렇게 하면 부모 클래스의 기본 생성자가 없어져도 오류가 발생하지 않는다.하위 클래스의 생성자에서 super를 사용할 때 주의할 점은 super가 가장 먼저 나타나야 한다는 점이다. 즉 부모가 초기화되기 전에 자식이 초기화되는 일을 방지하기 위한 정책이라고 생각하자.
 ```java
 class SubstractionableCalculator extends Calculator {
   public SubstractionableCalculator(int left, int right) {
     super(left, right);
   }
   public void substract() {
     System.out.println(this.left - this.right);
   }
}
```
---
## overriding(재정의)
부모에게 상속받은 메소드를 그대로 쓰지 않고 재정의해서 사용하는 방법
부모객체와 자식객체의 메소드가 겹치면 자식객체의 메소드를 호출하는 것

### 동일조건
1. 메소드명
2. 메소드 매개변수의 갯수, 데이터타입, 순서
3. 메소드 리턴타입

### 중복제거 방법 = super(부모객체)
```java
public int avg() {
  return super.avg();
}
```
---
## overloading
overriding은 동일조건이 제약이 많았음
메소드 명은 같지만 매개변수가 다를 경우에 class에서 메소드를 선언할 때 같은 이름으로 인자만 다르게 추가로 선언해주면 된다
추가로 선언할 때 중복이 발생하는 것을 방지하는 법
```java
public void setOprands(int left, int right){
  this.left = left;
  this.right = right;
}

public void setOprands(int left, int right, int third){
  this.setOprands(left, right); // 부모객체의 메소드 호출(공통부분)
  this.third = third; // 다른 점 추가
}
```

### 조건
리턴 타입이 같아야 한다

### riding(올라탄다)을 이용해서 부모 클래스의 메소드의 동작방법을 변경하고, loading을 이용해서 같은 이름, 다른 매개변수의 메소드들을 여러개 만들 수 있다는 사실을 아는 것이 중요하다
---

## CLASS PATH(로직 관리수단)

소스코드 파일 1개를 JAVAC로 컴파일 하면 .CLASS파일 1개가 생성되는 것이 아니라, 소스코드 파일 내에 존재하는 CLASS 갯수만큼 .CLASS 파일들이 생성된다

JAVA 명령어를 사용하여 CLASS파일을 실행할 때 CLASS파일이 현재 디렉토리에 존재하지 않는다면 CLASS PATH를 지정해주어야 한다.
```java
java -classpath “.;lib” ClasspathDemo2
```
컴파일할때마다 CLASSPATH를 지정하면 귀찮으니까 운영체제의 환경변수에 CLASS파일의 PATH를 설정해둔다
---

## package
1. class 이름의 충돌현상 극복
패키지 == 디렉토리 개념과 비슷
패키지명 = 일반적으로 도메인이름으로 사용해서 중복 방지

2. 다른 패키지에 존재하는 class 가져오는 방법
import 해당패키지명.클래스명;

3. 여러 패키지들에 class 이름이 겹칠때
org.opentutorials.javatutorials.packages.example2.B b = new org.opentutorials.javatutorials.packages.example2.B();

## api
1. SYSTEM.OUT.PRINTLN(1);
System = class명
out = class member 변수 (객체)
println = out 객체 내의 메소드

2. IMPORT JAVA.LANG.*
패키지 java.lang은 자바 프로그래밍을 하기 위해서 필수적인 클래스들을 모아둔 패키지다. 따라서 사용자의 편의를 위해서 자동으로 로딩을 하고 있는 것이다.
클래스 System은 바로 이 java.lang의 소속이다.

3. [api 문서 링크](http://docs.oracle.com/javase/8/docs/api/index.html)

---
## 규제
### 접근제어자
1. 개념
사용자가 접근하면 안되거나 접근할 필요가 없는 멤버에 대한 접근을 규제

2. 타입
public = 모두 접근 가능
protected = 다른 패키지일지라도 상속이면 접근가능
default = 같은 패키지일때만 접근 가능
private = 모두 접근 불가

3. class의 접근제어자(패키지 개념)
public = 모두 접근 가능
default = 같은 패키지일때만 접근 가능
public class가 포함된 소스코드는 public class의 이름과 소스코드 파일명이 같아야한다.(= 하나의 소스코드 파일에는 하나의 public class만 존재할 수 있다)

### abstract
1. 개념
상속을 하고 재정의 해야만 접근가능한 메소드
```java
abstract class A{
  public abstract int b();
  public void d(){
    System.out.println(“world”);
  }
}

class B extends A{
  public int b(){return 1;}
}
```

2. 사용이유
부모 class = 공통분모, template 패턴
자식 class = 화면에 출력하는 모습을 달리해야하는 경우

### final
static = 모든 instance에서 공통
final = 더이상의 변경 불가(상속이나 overriding 불가)

### interface
1. 개념
어떤 객체가 특정한 인터페이스를 사용한다면 그 객체는 반드시 인터페이스의 메소드들을 구현해야 한다
```java
public interface Calculatable {
  public void setOprands(int first, int second, int third) ;
  public int sum();
  public int avg();
}

class Calculator implements Calculatable {
  int first, second, third;
  public void setOprands(int first, int second, int third) {
    this.first = first;
    this.second = second;
    this.third = third;
  }
  public int sum() {
    return this.first + this.second + this.third;
  }
  public int avg() {
    return (this.first + this.second + this.third) / 3;
  }
}

```
2. 사용이유
협업할 때 서로가 동일한 메소드를 만들도록 규약을 만들어서 이후에 공유한 결과 각자가 상대의 일정이나 구현하는 방식에 덜 영향을 받으면서 애플리케이션을 구축할 수 있다

3. 규칙
인터페이스 내 메소드는 public이어야 한다
하나의 class는 복수개의 인터페이스 구현 가능(class는 하나의 부모 class에 대해서만 상속 가능)
인터페이스도 상속이 가능하다

4. abstract vs interface
인터페이스와 추상 클래스는 서로 비슷한 듯 다른 기능이다. 인터페이스는 클래스가 아닌 인터페이스라는 고유한 형태를 가지고 있는 반면 추상 클래스는 일반적인 클래스다. 또 인터페이스는 구체적인 로직이나 상태를 가지고 있을 수 없고, 추상 클래스는 구체적인 로직이나 상태를 가지고 있을 수 있다.

---
## 다형성
1. 개념
하나의 메소드나 클래스가 있을 때 이것들이 다양한 방법으로 동작하는 것
ex) overloading

2. class와 다형성
클래스 B를 클래스 A의 데이터 타입으로 인스턴스화 했을 때 클래스 A에 존재하는 맴버만이 클래스 B의 맴버가 된다. 동시에 클래스 B에서 오버라이딩한 맴버의 동작방식은 그대로 유지한다.

```java
class A{
  public String x(){return “A.x”;}
}

class B extends A{
  public String x(){return “B.x”;}
  public String y(){return “y”;}
}

public class PolymorphismDemo1 {
  public static void main(String[] args) {
    A obj = new B();
    System.out.println(obj.x()); // B.x가 출력된다
  }
}

```
```java
public class CalculatorDemo {
  public static void execute(Calculator cal){
    System.out.println(“실행결과”);
    cal.run();
  }
  public static void main(String[] args) {
    Calculator c1 = new CalculatorDecoPlus();
    c1.setOprands(10, 20);
    Calculator c2 = new CalculatorDecoMinus();
    c2.setOprands(10, 20);
    execute(c1);
    execute(c2);
  }
}
```
3. 인터페이스와 다형성
인터페이스 I는 메소드 A만을 정의하고 있고 I를 데이터 타입으로 하는 인스턴스는 마치 메소드 A만을 가지고 있는 것처럼 동작하기 때문이다.

이것은 인터페이스의 매우 중요한 특징 중의 하나를 보여준다. 인스턴스 objI2의 데이터 타입을 I2로 한다는 것은 인스턴스를 외부에서 제어할 수 있는 조작 장치를 인스턴스 I2의 맴버로 제한한다는 의미가 된다. 인스턴스 I2와 I3로 인해서 하나의 클래스가 다양한 형태를 띄게 되는 것이다.

4. 비유
Steve와 Rachel의 사용자인 직장에서는 Steve와 Rachel의 인터페이스인 programmer를 통해서 두사람과 관계하게 된다. 두 사람이 어떤 종교나 가족관계를 가졌건 인터페이스 programmer을 가지고 있다면 고용할 수 있다. 회사에서는 코딩을 할 수 있는 사람이 필요하고 어떤 사람이 programmer라는 인터페이스를 구현하고 있다면 그 사람은 반드시 coding이라는 메소드를 구현하고 있을 것이기 때문이다. 또 두 사람에게 업무를 요청 할 때는 programmer라는 인터페이스의 메소드인 coding을 통해서 요청하면 된다. 하지만 두 사람의 성향이나 능력에 따라서 그 업무를 수행한 결과는 다른데 Steve는 빠르게 코딩하고 Rachel은 우아하게 코딩하고 있다.

```java
interface father{}
interface mother{}
interface programmer{
  public void coding();
}
interface believer{}

class Steve implements father, programmer, believer{
  public void coding(){
    System.out.println(“fast”);
  }
}

class Rachel implements mother, programmer{
  public void coding(){
    System.out.println(“elegance”);
  }
}

public class Workspace{
  public static void main(String[] args){
    programmer employee1 = new Steve();
    programmer employee2 = new Rachel();
    employee1.coding();
    employee2.coding();
  }
}
```
---
## 예외
### try, catch

try {
  예외 발생 예상되는 로직
} catch (예외클래스 인스턴스){
  예외가 발생했을 때 실행되는 로직
} finally {
  예외여부와 관계없이 실행되는 로직
}
ex)0으로 나누기 할때
```java
try {
  System.out.print(“계산결과는 “);
  System.out.print(this.left/this.right);
  System.out.print(” 입니다.”);
} catch(Exception e){
  System.out.println(“오류가 발생했습니다 : “+e.getMessage());
}
```

ex)여러가지 오류가 생길때 대처방법(다중 catch 사용, catch는 else와 비슷하군)
```java
try {
  System.out.println(arr[first] / arr[second]);
} catch(ArrayIndexOutOfBoundsException e){ //else if
  System.out.println(“ArrayIndexOutOfBoundsException”);
} catch(ArithmeticException e){ //else if
  System.out.println(“ArithmeticException”);
} catch(Exception e){ //else
  System.out.println(“Exception”);
}
```

### EXCEPTION 클래스의 메소드들
e.getMessage(); // by zero
e.toString(); // java.lang.ArithmeticException: / by zero
e.printStackTrace(); // 가장 자세한 예외정보 제공

### FINALLY 왜 쓰나
데이터베이스를 사용한다면 데이터베이스 서버에 접속해야 한다. 이때 데이터베이스 서버와 여러분이 작성한 에플리케이션은 서로 접속상태를 유지하게 되는데 데이터베이스를 제어하는 과정에서 예외가 발생해서 더 이상 후속 작업을 수행하는 것이 불가능한 경우가 있을 수 있다. 예외가 발생했다고 데이터베이스 접속을 끊지 않으면 데이터베이스와 연결 상태를 유지하게 되고 급기야 데이터베이스는 더 이상 접속을 수용할 수 없는 상태에 빠질 수 있다. 접속을 끊는 작업은 예외 발생여부와 상관없기 때문에 finally에서 처리하기에 좋은 작업이라고 할 수 있다. 말하자면 finally는 작업의 뒷정리를 담당한다고 볼 수 있다.

### 예외 타입들 정리
illegalArgumentException = 매개변수가 의도하지 않은 상황을 유발시킬 때
llegalStateException = 메소드를 호출하기 위한 상태가 아닐 때
NullPointerException = 매개 변수 값이 null 일 때
IndexOutOfBoundsException = 인덱스 매개 변수 값이 범위를 벗어날 때
ArithmeticException = 산술적인 연산에 오류가 있을 때

### throw
예외를 CATCH하지 않고 다음사용자에게 양도하기
```java
import java.io.*;
class B{
  void run() throws IOException, FileNotFoundException{
    BufferedReader bReader = null;
    String input = null;
    bReader = new BufferedReader(new FileReader(“out.txt”));
    input = bReader.readLine();
    System.out.println(input);
  }
}

class C{
  void run(){
    B b = new B();
    try {
      b.run();
    } catch (FileNotFoundException e) {
      e.printStackTrace();
    } catch (IOException e) {
      e.printStackTrace();
    }
  }
}

public class ThrowExceptionDemo {
  public static void main(String[] args) {
    C c = new C();
    c.run();
  }
}
```
### CHECKED EXCEPTION VS UNCHECKED EXCEPTION
Throwable > Exception > IOException
Throwable > Exception > RuntimeException > ArithmeticException

RuntimeException = unchecked Exception (예외를 처리 안해도 됨)
!RuntimeException = checked Exception (예외를 catch 하거나 throw해야함)

checked인지 uncheck인지 판단= 사용자가 복구 가능하면 checked

---
## Object(class)
1. 개념
모든 class의 공통 조상
모든 class는 무조건 object class를 상속한다

2. OBJECT CLASS의 메소드들
필요에 따라 재정의해서 사용할 수도 있다

toString( println(c1)= println(c1.toStirng) ) //직접 구현해서 사용해보기

equals //객체와 객체를 비교할때, string 비교시 (단, 원시데이터타입 비교시에는 == 사용)

3. EQUALS 재정의하기
```java
public boolean equals(Object obj) {
  Student _obj = (Student)obj;
  return name == _obj.name;
}
```
(Student)obj 는 메소드 equals로 전달된 obj의 데이터 타입이 Object이기 때문에 이를 Student 타입으로 형 변환하는 코드다. 아래 코드를 통해서 현재 객체의 변수 name과 equals의 인자로 전달된 객체의 변수 name을 비교한 결과를 Boolean 값으로 리턴하고 있다. 이 값에 따라서 두 개의 객체는 같거나 다른 것이 된다.

4. GARBAGE COLLECTION
램을 효율적으로 사용하기 위해 더이상 사용하지 않는 데이터를 램에서 제거하는 작업을 자동화한 것
---

## ENUM(ENUMERATED TYPE)
1. 서로 연관된 상수들의 집합
```java
class Fruit{
public static final Fruit APPLE = new Fruit();
public static final Fruit PEACH = new Fruit();
public static final Fruit BANANA = new Fruit();
}

enum Fruit{
APPLE, PEACH, BANANA;
}
```

2. 사용이유
코드가 단순해진다
인스턴스 생성과 상속을 방지한다
구현의 의도가 열거임을 분명하게 나타낸다

3. 열거형 특성
연관된 값들 저장하고 값들이 변경되지 않도록 보장
class 이기 때문에 열거형 내부에 생성자,필드,메소드를 가질 수 있어서 단순히 상수가 아니라 더 많은 역할 가능

4. CLASS와 ENUM의 차이점
배열처럼 멤버 전체를 열거할 수 있는 value 메소드
```java
for(Fruit f : Fruit.values()){
  System.out.println(f+”, “+f.getColor());
}
```
---
## 복제와 참조
복제 = 기본 데이터 타입
참조 = 기본 이외의 데이터 타입, new
---

## 제네릭
1. 개념
클래스 내부에서 사용할 데이터 타입을 외부에서 지정
```java
class Person{
  public T info;
}

public class GenericDemo {
  public static void main(String[] args) {
    Person p1 = new Person();
    Person p2 = new Person();
  }
}
```
2. 사용이유
코드의 중복 제거 + 데이터 타입의 안전성

3. 다수의 제네릭 사용방법
```java
class Person{
  public T info;
  public S id;
  Person(T info, S id){
    this.info = info;
    this.id = id;
  }
}

public class GenericDemo {
  public static void main(String[] args) {
    Person p1 = new Person(new EmployeeInfo(1), 1);
  }
}
```
4. 제네릭에 기본 데이터타입은 들어갈 수 없다(참조데이터만 가능) 해결방법은?
wrapper data type 사용하기
```java
class Person{
  public T info;
  public S id;
  Person(T info, S id){
    this.info = info;
    this.id = id;
  }
}

public class GenericDemo {
  public static void main(String[] args) {
    EmployeeInfo e = new EmployeeInfo(1);
    Integer i = new Integer(10);
    Person p1 = new Person(e, i);
    System.out.println(p1.id.intValue());
  }
}
```
5. 제네릭 제한하기(EXTENDS)
```java
abstract class Info{
  public abstract int getLevel();
}

class EmployeeInfo extends Info{
  public int rank;
  EmployeeInfo(int rank){ this.rank = rank; }
  public int getLevel(){
    return this.rank;
  }
}

class Person{
  public T info;
  Person(T info){ this.info = info; }
}

public class GenericDemo {
  public static void main(String[] args) {
    Person p1 = new Person(new EmployeeInfo(1));
    Person p2 = new Person(“부장”);
  }
}

// Person의 T는 Info 클래스나 그 자식 외에는 올 수 없다.
```

---

## COLLECTIONS FRAMEWORK
### ARRAYLIST (VS ARRAY)
크기를 미리 지정하지 않으므로 많은 값 저장가능
length 대신에 size 를 사용한다
값을 넣을때는 add(value) 를 사용한다(이때 value type은 무엇이든 가능하도록 object type을 지닌다 따라서 밑에 반복문에서 value값 가져올때 형변환 필요)
값을 가져올때는 get(index) 을 사용한다
```java
for(int i=0; i<al.size(); i++){
  String val = (String)al.get(i);
  System.out.println(val);
}
```
제네릭을 사용하면 ArrayList 내에서 사용할 데이터 타입을 인스턴스를 생성할 때 지정할 수 있기 때문에 데이터를 꺼낼 때(String val = al.get(i);) 형변환을 하지 않아도 된다.
```java
ArrayList<String> al = new ArrayList<String>();
al.add("one");
al.add("two");
al.add("three");
for(int i=0; i<al.size(); i++){
    String val = al.get(i);
    System.out.println(val);
}
```
### COLLECTIONS FRAMEWORK 구성
collection(set,list,queue) + map
collection, map = interface
set, list, queue = class

### list vs set(집합)
list 는 데이터의 중복가능, index 존재
set 은 데이터 중복불가, index 없음

### iterator (인터페이스 Collection에 있는 메소드)
데이터 하나씩 확인가능
```java
Iterator ai = al.iterator();
while(ai.hasNext()){
    System.out.println(ai.next());
}
```
MAP은 ITERATOR 메소드가 없으므로 데이터 불러올때 HOW??
1. map의 데이터를 set에 넣기
2. set의 iterator 사용
```java
public static void main(String[] args) {
        HashMap<String, Integer> a = new HashMap<String, Integer>();
        a.put("one", 1);
        a.put("two", 2);
        a.put("three", 3);
        a.put("four", 4);
        System.out.println(a.get("one"));
        System.out.println(a.get("two"));
        System.out.println(a.get("three"));

        iteratorUsingForEach(a);
        iteratorUsingIterator(a);
    }

    static void iteratorUsingIterator(HashMap map){
            Set<Map.Entry<String, Integer>> entries = map.entrySet();
            Iterator<Map.Entry<String, Integer>> i = entries.iterator();
            while(i.hasNext()){
                Map.Entry<String, Integer> entry = i.next();
                System.out.println(entry.getKey()+" : "+entry.getValue());
            }
        }    
```
### 데이터 정렬 (sort)
Collections class의 메소드 중 sort를 활용하라
public static void sort(List list)
sort의 인자인 list는 데이터 타입이 List이다. 즉 메소드 sort는 List 형식의 컬렉션을 지원한다는 것을 알 수 있다. 인자 list의 제네릭 는 coparable을 extends 하고 있어야 한다. Comparable은 인터페이스인데 이를 구현하고 있는 클래스는 아래 메소드를 가지고 있어야 한다.
```java
public int compareTo(Object o) {
  return this.serial – ((Computer)o).serial;
}
```
메소드 sort를 실행하면 내부적으로 compareTo를 실행하고 그 결과에 따라서 객체의 선후 관계를 판별하게 된다.
