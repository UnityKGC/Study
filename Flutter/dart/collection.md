# Dart Collection
Dart에는 총 3가지의 Collection 타입이 존재한다.
- [List](#list)
- [Map](#map)
- [Set](#set)

## List
>**Dart List 문서**   
>https://api.dart.dev/stable/2.15.1/dart-core/List-class.html   

기본적으로 Dart에서 List는 다음과 같이 사용한다.
```dart
var numbers = [1,2,3,4];
//print(numbers); // [1,2,3,4]
```

List의 타입을 int로 고정하고 싶다면 다음과 같이 사용한다.
```dart
List<int> numbers = [1,2,3,4];
//print(numbers); // [1,2,3,4]
```

### collection if
Dart는 List 내에 if문을 사용하여 조건에 따라 List 요소를 결정할 수 있다.   
다음은 collection if를 사용하여 List 요소를 결정하는 예제이다.
```dart
var isTrue = true;
var numbers = [1,2,3,4, if(isTrue) 5];
//print(numbers); // [1,2,3,4,5]
```

위의 예제는 아래의 코드와 동일한 결과를 갖는다.
```dart
var isTrue = true;
var numbers = [1,2,3,4];
if(isTrue) {
    numbers.add(5);
}
//print(numbers); // [1,2,3,4,5]
```

### collection for
Dart는 List 내에 for문을 사용하여 다른 List의 요소를 추가할 수 있다.
```dart
var samsung = ['Galaxy S','Galaxy A','Galaxy Tab'];
var mobile = [
    'iphone Pro',
    'iphone',
    'ipad',
    for (var galaxy in samsung) galaxy
];
//print(mobile); // [iphone Pro, iphone, ipad, Galaxy S, Galaxy A, Galaxy Tab]
```

위의 예제는 아래의 코드와 동일한 결과를 갖는다.
```dart
var samsung = ['Galaxy S','Galaxy A','Galaxy Tab'];
var mobile = ['iphone Pro','iphone','ipad'];

for (var galaxy in samsung) {
    mobile.add(galaxy);
}
//print(mobile); // [iphone Pro, iphone, ipad, Galaxy S, Galaxy A, Galaxy Tab]
```

## Map
기본적으로 Dart에서 Map은 다음과 같이 사용한다.
```dart
var member = {
    'name': 'vhdl',
    'email': 'whiper403@gmail.com'
};
//print(member);
```

type을 고정하고 싶다면 다음과 같이 사용한다.
```dart
Map<String, String> member = {
    'name': 'vhdl',
    'email': 'whiper403@gmail.com'
};
//print(member);
```

## Set
Dart에서 Set은 중복값을 허용하지 않는 List로 사용된다.   
Set은 다음과 같이 사용된다.
```dart
var numbers = {1,2,3,4};
```

type을 지정하고 싶다면 다음과 같이 사용한다.
```dart
Set<int> numbers = {1,2,3,4};
```

위에서 서술했듯이 List와 Set의 차이는 중복값의 허용여부이다.   
이는 다음 코드의 결과물을 통해 확인할 수 있다.
```dart
var temp_list = [1,2,3,4];
var temp_set = {1,2,3,4};

temp_list.add(2);
temp_set.add(2);

//print(temp_list); // [1,2,3,4,2]
//print(temp_set); // {1,2,3,4}
```