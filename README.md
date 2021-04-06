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

## while

while 은 대괄호 안에 주어진 표현식의 값의 따라 반복을 제어할 수 있는 키워드이다.  

```java
while (expression) {
    statement;
}
```

표현식이 참인 경우, 명령문을 반복해서 실행한다.  

## do while

while 문을 변경한 것으로 반복을 제어할 수 있는 키워드이다.  

```java
do {
    statement;
} while (expression)
```

while 문과는 다르게 명령문을 최초 한번 실행하고, while 문의 표현식의 값의 따라 반복을 수행한다.  

## for

for 는 반복하는 횟수를 알고 있을 경우 반복을 제어할 수 있는 키워드이다.

```java
for (초기화; 조건식; 증감식) {
    statement;
}
```

for 문은 변수 초기화, 조건식, 증감식, 명령문과 같이 모두 네 부분으로 이루어져 있다.  
1. 변수를 초기화한다. 이 단계는 처음 한 번만 수행된다.  
2. 해당 변수가 조건식을 만족하는지 판단하고 true 이면 명령문을 수행한다.
3. 해당 변수에 대하여 증감 연산을 수행한다.  
4. `2번`과 `3번`을 반복하고 만약 조건식의 결과가 false 이면 for 문 전체를 빠져나가게 된다.

#### 무한루프

```java
for ( ; ; ) {
    statement;
}
```

조건식이 없기 때문에 결과가 true 로 간주되어 명령문을 무한 반복 수행한다.  

#### forEach

```java
for (String name : names) {
    statement;
}
```

데이터 컬렉션에 대한 탐색을 단순화 한다.  
반복 횟수에 대하여 명시적이지 않으며, 명령문에서는 배열 또는 컬렉션을 하나씩 거치며 현재 값이 정의된 변수에 복사된다.  

## break

break 는 while, for 또는 switch 문에서 사용할 수 있으며 블럭을 종료할 수 있는 키워드이다.  

```java
while (true) {
    statement;
    
    if (expression) {
        break; // while 문 종료
    }
}
```

## continue

continue 는 반복 중 특정 조건에 대하여 다음 명령문을 수행하지 않고 넘어 갈 수 있게 해주는 키워드이다.  
for, while 문에서 함께 쓰인다.  

```java
while (true) {
    statement;
    
    if (expression) {
        continue;
    }
    
    statement2;
}
```

if 문의 표현식의 결과가 참이면 continue 가 실행되고, 뒤의 명령문(statement2)은 수행되지 않는다.

<hr>

#### References

> 웹 문서
> - [zetcode | Java control flow](https://zetcode.com/lang/java/flow/)
> - [[Java] 선택문과 제어문](https://ahnyezi.github.io/java/javastudy4-flowcontrol/)
