# 절차지향적 프로그래밍

## 비교-조건문-논리연산자
1. 비교연산자
⋅⋅⋅ ==, !=

2. 기본 데이터 타입 비교
⋅⋅⋅ ==

3. 기본 데이터타입 이외의 문자열, 객체 등 비교
⋅⋅⋅ stringA.equals(stringB)

4. 논리연산자
⋅⋅⋅ &&, ||
⋅⋅⋅ 조건문의 중첩을 줄일 수 있다
---
## 반복문 제어
1. break  //특정 조건에서 반복문 빠져나가기
2. continue // 특정 조건에서 실행 안하고 다음 조건으로 반복
---
## array
⋅⋅⋅ 변수 안에 여러개의 데이터를 담기

### 정의 방법
1. 한번에 정의
```java
String[] classGroup = { "최진혁", "최유빈", "한이람", "이고잉" };
// 대괄호가 아니네???
```

2. 껍대기만 정의하고 하나씩 넣기
```java
String[] classGroup = new String[4];
classGroup[0] = "최진혁";
classGroup[1] = "최유빈";
classGroup[2] = "한이람";
classGroup[3] = "이고잉";

String[] classGroup = new String[4];
classGroup[0] = "최진혁";
System.out.println(classGroup.length);      //4
classGroup[1] = "최유빈";
System.out.println(classGroup.length);      //4
classGroup[2] = "한이람";
System.out.println(classGroup.length);      //4
classGroup[3] = "이고잉";
System.out.println(classGroup.length);      //4
//여기서의 length는 배열 내 현재 데이터 갯수가 아니라 데이터가 몇개 들어갈 수 있나를 의미
```

### for-each
⋅⋅⋅ 배열과 반복문을 함께 사용할 때 좀 더 간결하게 하려고
```java
for(String e : members) {
System.out.println(e + "이 상담을 받았습니다");
}
```
### array 한계
⋅⋅⋅ 처음에 배열 정의할때 length 값을 지정해주면 이후에 데이터를 초과해서 삽입하면 오류가 뜬다 즉 length가 자동적으로 변경되지 않는 불편함이 있다 -> collection으로 극복

---

## method
### 효용
1. 로직을 재사용
2. 유지보수
3. 매개변수 넣어서 재사용성 높일 수 있다

### return type
```java
void main(){}      // return 값이 없는 메소드
String main(){}    // return 값의 데이터타입이 string
```
### 하나의 메소드가 다양한 type 처리
```java
public class MethodDemo7 {
    public static String numbering(int init, int limit) {
        int i = init;
        String output = "";
        while (i < limit) {
            output += i;
            i++;
        }
        return output;
    }

    public static void main(String[] args) {
        String result = numbering(1, 5);
        System.out.println(result);
        try { // 무시
            // 다음 행은 out.txt 라는 파일에 numbering이라는 메소드가 반환한 값을 저장합니다.
            BufferedWriter out = new BufferedWriter(new FileWriter("out.txt"));
            out.write(result);
            out.close();
        } catch (IOException e) {
        } // 무시
    }
}
```
---

## 사용자의 입력값 전달
1. CLI(cmd에서 매개변수 전달)
```java
package org.opentutorials.javatutorials.io;

class InputDemo{
    public static void main(String[] args){
        System.out.println(args.length);
    }
}

javac InputDemo.java
java InputDemo 1 2 3 4 5 6;        // 6
java InputDemo one two three;      // 3
```

2. eclipse
⋅⋅⋅ run configuration – 추가 – argument 탭에 값 입력

3. 앱실행 중에 전달
⋅⋅⋅ scanner 라이브러리 사용
⋅⋅⋅ run 실행-콘솔창에 인자값 입력 후 enter- 콘솔창에 결과값 출력됨
```java
import java.util.Scanner;  //스캐너 로드

public class ScannerDemo {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);  //사용자가 입력한 값을 담는다
        int i = sc.nextInt();
        System.out.println(i*1000);
        sc.close();
    }

}
```
4. 특정 조건에서 항상 상호작용
⋅⋅⋅ 반복문 사용
```java
import java.util.Scanner;

public class Scanner2Demo {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        //사용자의 입력값이 정수이면 true를 받아서 항상 실행된다
        while(sc.hasNextInt()) {
            System.out.println(sc.nextInt()*1000);
        }
        sc.close();    // 사용자의 입력값이 정수가 아니면 프로그램 종료
    }

}
```

5. 키보드 이외의 입력값 받기
```java
import java.io.*;

public class Scanner3Demo {

    public static void main(String[] args) {
        try {
            //out.txt파일내용을 입력값으로 받아라
            File file = new File(&quot;out.txt&quot;);
            Scanner sc = new Scanner(file);
            while(sc.hasNextInt()) {
                System.out.println(sc.nextInt()*1000);
            }
            sc.close();
         // out.txt파일 없으면 밑에 catch안의 로직을 실행해라
        } catch(FileNotFoundException e){
            e.printStackTrace();
        }

    }

}
```

---
