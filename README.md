# Java Control Flow

자바에는 프로그램의 흐름을 변경하는 데 사용되는 여러 키워드가 존재한다.  
if, else 및 switch 문은 조건문에 사용되며 while, for 문은 주기를 생성하고 break 와 continue 문은 루프를 변경하는 데 사용된다.

## if

표현식(expression)이 참인지 확인하는 데 사용되는 if 키워드이다.  

```java
if (expression) {
    statement;
}
```

참이면 명령문(statement)이 실행된다.  
본문에 명령문이 하나만 있는 경우라면 대괄호는 생략할 수 있다.  

## else

else 키워드를 사용하여 간단한 분기를 만들 수 있다.  

```java
if (expression) {
    statement;
} else {
    statement2;
}
```

if 표현식이 false 라면 else 본문의 명령문이 실행된다.

## else if

else if 키워드를 사용하여 여러 분기를 만들 수 있다.   

```java
if (expression) {
    statement;
} else if (expression2) {
    statement2;
} else if (expression3) {
    statement3;
} else if
        ...
} else {
    statement7;
}
```

else if 키워드는 이전 조건이 충족되지 않은 경우에만 해당 조건을 확인한다.

## switch

switch 는 선택을 제어하는 키워드이다.  

```java
switch (domain) {
    case A:
        statement;
        break;
    case B:
        statement2;
        break;
    case C:
        statement3;
        break;
    ...
    default:
        statement7;
        break;
}
```
값 또는 표현식의 결과를 통해 여러 분기를 만들 수 있고, 프로그램 실행의 흐름을 제어 할 수 있다.  
if 및 else if 문 조합보다 더 간단한 방법으로 여러 분기를 만들 수 있다. 

switch 문에는 다음과 같은 특징이 존재한다.  
- 각 분기는 break 키워드로 끝이 난다. 만약, 해당 case 에 break 문이 없다면 하단에 존재하는 case 명령문이 실행되며 break 를 만날때까지 해당 과정이 진행된다.
- default 명령문은 변수 또는 표현식의 결과와 일치하는 case 가 없을 경우 실행되는 명령문으로 선택적으로 정의할 수 있다.
- switch 문에 사용할 수 있는 값으로는 byte, short, char, int(이상 Wrapper 포함), enum 또는 String 타입이 가능하다.

## switch expression

자바 12 부터 break 대신 yield 문과 arror 를 사용한 switch 문이 추가되었다.  
- yield: case 의 결과로 반환하고 싶은 값이 있을 경우 사용한다.  
- ->: 콜론(:) 대신 사용할 수 있다.  

```java
int number = switch (domain) {
    case A:
        yield 1;
    case B:
        yield 2;
    case C:
        yield 3;
    default:
        yield 4;
}
```

number 는 domain 에 따라 1, 2, 3 또는 4 일 수 있다.  

```java
switch (domain) {
    case A -> 1;
    case B -> 2;
    case C -> 3;
    default -> 4;
}
```

<hr>

#### References

> 웹 문서
> - [zetcode | Java control flow](https://zetcode.com/lang/java/flow/)
> - [[Java] 선택문과 제어문](https://ahnyezi.github.io/java/javastudy4-flowcontrol/)
