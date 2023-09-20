# Dart Variables
> Dart 언어의 변수 사용 방법 설명

## var type

Dart언어도 C와 비슷하게 main 메소드에서 시작한다.

```dart
void main() {
    print("vhdl");
}
```

기본적인 변수 선언은 다음과 같다.
```dart
var name = 'vhdl';
//print(name); // vhdl
```
javascript의 `var` 타입과 비슷하게 어떤 타입의 변수도 할당 가능하다.  
하지만 JS의 var와 Dart의 var에는 차이가 있다.   
- javascript는 선언과 동시에 변수가 할당되어도 타입과 상관없이 재사용이 가능하다.   
- Dart의 `var`는 선언과 동시에 변수가 할당되면, 할당된 변수의 타입으로 고정된다.   

즉, 위의 예제에서 name 변수를 선언하면서 String 타입을 할당했으므로, name 변수의 타입은 String으로 고정이다.   

</br>

선언과 동시에 할당하지 않으면, 어떠한 데이터 타입도 저장 가능하다.
```dart
var name;
name = 'vhdl';
//print(name); // vhdl
name = 1;
//print(name); // 1
```
위와 같이 String 데이터를 할당하고, int 데이터를 할당했지만 에러가 없다.   
이러한 type을 `Dynamic Type`이라고 한다.

## dynamic type
기본적인 변수 선언은 다음과 같다.
```dart
dynamic name = 'vhdl';
//print(name); // vhdl
name = 1;
//print(name); // 1
```
dynamic type은 변수를 선언과 동시에 할당하더라도 타입과 상관없이 재사용이 가능하다.   
오히려 javascript의 var은 Dart의 dynamic과 동일하다고 볼 수 있다.


## int · double · string · bool
Dart 언어는 변수에 직접 type 지정이 가능하다.
```dart
int inum = 10;
double dnum = 10.0;
String snum = '10';
bool wrong = true;
```

## num type
Dart는 int에서 double 또는 double에서 int를 메소드에 의지하지 않고 대입할 시 오류가 발생한다.   
```dart
int x = 10;
x = x / 3;
//print(x); 
// A value of type 'double' can't be assigned to a variable of type 'int'.
```
그렇다면 다양한 숫자값을 받아야 하는 경우에는 어떻게 해야할까?   
바로 `num` type을 사용하면 된다.
```dart
num x = 10;
//print(x); // 10
x = 10.1;
//print(x) // 10.1
```
위의 예제와 같이 사용할 경우,   
x에 정수를 대입하고, 실수를 대입을 하더라도 문제 없이 출력이 가능하다.   
만일 다양한 숫자값을 받아야 한다면 num type을 쓰도록 하자.


## Nullable
Dart 언어는 초기값을 대입하지 않으면 에러가 발생한다.
```dart
String name;
//print(name);
//The non-nullable local variable 'name' must be assigned before it can be used.
```

</br>

Dart 언어는 기본적으로 모든 변수가 non-nullable 이다.   
하지만 null 값을 허용하려면 ? 기호를 사용하면 된다.

```dart
String? name;
//print(name); // null
```

### The null assertion operator (!)
Dart에서는 ! 기호를 통해 해당 변수가 null이 아님을 선언한다.   
해당 변수가 정말 null이 나오지 않을 경우 사용한다.
```dart
int? age = 26;
age = age! + 1;
```

### null check
Dart에서 사용 가능한 null 체크 오퍼레이터를 정리한다.

#### `??`
좌, 우 피연산자 중에서 Null이 아닌 것을 선택한다.  
아래 예제를 참고했을 때, a가 null이 아니라면 age에 a의 값이 대입된다.   
하지만 a가 null이라면, age에는 b의 값이 대입된다.
```dart
int? age;
int? a;
int b = 26;

age = a??b;
//print(age); // 26
```

#### `??=`
아래 예제를 참고했을 때, age가 null이라면 a의 값이 대입된다.   
물론 age가 null이 아니라면 age 값이 그대로 print 된다.
```dart
int? age;
int a = 26;

age ??= a;
//print(age); // 26

age = 30;
age ??= a;
//print(age); // 30
```

#### `?.`
객체가 null이 아닐 때만 속성과 메소드에 접근한다.   
아래 예제를 참고했을 때, x가 null이 아니라면 foo() 메소드 또는 bar 속성에 접근 가능하다.
```dart
x?.foo();
x?.bar;
```

## final variable
Dart 언어는 final을 사용하여 값을 고정할 수 있다.   
즉, 한 번 선언한 변수는 업데이트가 불가하다.   

```dart
final name = 'vhdl';
//name = 'hdl'; // err
```

## const variable
const 역시 final과 같이 값을 고정해서 업데이트를 불가하도록 만들 수 있다.   
```dart
const name = 'vhdl';
//name = 'hdl'; // err
```

## final vs const
그렇다면 `final`과 `const`는 어떤 차이가 있을까?   
아래 예시를 보도록 하자.
```dart
final DateTime now = DateTime.now();
//const DateTime now = DateTime.now(); // compile error
```
const의 경우, 컴파일타임에서 상수를 정의할 수 있다.   
즉, const로 정의한 상수는 런타임에서 정의되는 값을 설정할 수 없다.

#### compile-time
>**컴파일타임**   
>소스코드가 컴파일 과정을 통해 컴퓨터가 이해할 수 있는 기계어로 변환되는 과정

오류 유형
- Syntax error
- Type check error 등

#### run-time
>**런타임**   
>컴파일 과정을 마친 컴퓨터 프로그램이 실행되고 있는 환경 또는 동작되는 동안의 시간

오류 유형
- null 참조 오류
- index out of range 등

## late variable
late는 초기 데이터 없이 변수를 선언한 후, 나중에 데이터를 할당할 때 사용한다.
```dart
late final name;
late int age;
late var temp;
```
물론 데이터를 할당하지 않은 late 변수를 사용한다면 에러가 뜬다.
```dart
late String name;
//print(name); // Error: Late variable 'name' without initializer is definitely unassigned.
```

#### When?
그렇다면 late는 언제 사용하는 것일까?   
- API를 사용해 값을 얻어와 변수에 저장하는 경우
- 나중에 들어오는 값이 non-nullable인 경우

아래 예시를 보자.
```dart
// Using null safety, incorrectly:
class Coffee {
  String _temperature;

  void heat() { _temperature = 'hot'; }
  void chill() { _temperature = 'iced'; }

  String serve() => _temperature + ' coffee';
}

void main() {
  var coffee = Coffee();
  coffee.heat();
  coffee.serve();
}
```

```
Non-nullable instance field '_temperature' must be initialized.
```
예시의 코드를 그대로 작성하게 되면 다음과 같은 오류를 만난다.   
class 내에서는 무조건 non-nullable 변수를 초기화 해줘야 한다.   

</br>

하지만 값을 할당하기 전까지는 초기화하고 싶지 않을 경우, 두 가지 해결방법이 있다.
```dart
// Nullable
String? _temperature;
// late
late String _temperature;
```
1. 변수를 nullable로 선언
2. 변수의 데이터 할당을 잠시 미루도록 선언

</br>

즉, 변수가 아직 초기화는 되지 않았지만 변수가 non-nullable을 유지하고 싶을 경우 사용한다.   

방법 1 코드는 _temperature에 들어갈 데이터가 null도 가능하다고 인식할 수 있다.   
방법 2 코드는 _temperature 변수가 나중에 값을 할당받는다고 정확하게 인식할 수 있다.   