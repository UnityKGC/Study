# Widget
> **Flutter**에서 사용하는 **Widget**에 대해 알아보자

Flutter의 화면은 모든 요소가 위젯으로 이루어져 있다.   
하나의 큰 위젯 안에 여러 위젯이 들어가고 그 위젯 안에도 다른 여러 위젯이 들어간다.   
그렇기에 UI 코드가 복잡하다는 점이 있다.

우선 위젯은 크게 두가지로 분류된다.
- Stateless Widget
- Stateful Widget

<br>

## StatelessWidget

> 💡 변화가 필요없는 화면을 구성할 때 사용하는 위젯 클래스

### 특징
- build 메서드가 한 번만 호출됨 → 이후 다시는 호출 안함
- 이름에서 알 수 있듯 State(상태)를 가지지 않는 클래스
- 즉, SLW 내부의 모든 UI 위젯들은 상태의 변화를 인지 못함
    - 변수값이 변해도 Text 위젯에는 반영 안됨.
- 예시 코드

```dart
class SLWdemo extends StatelessWidget {
	int _count = 0;

	@override
	Widget build(BuildContext context) {
		return Scaffold(
			...
		)
	}
}
```


## StatefulWidget

> 💡 한번 생성한 화면의 구성이변경될 수 있는 경우에 사용하는 위젯 클래스

### 특징
- State 객체의 **setState 메서드**가 위젯의 상태 변화를 알려줌
- setState가 호출되면 플러터가 위젯을 다시 그림
- 예시 코드

```dart
class SFWdemo extends StatefulWidget {
  @override
  SFWdemoState createState() => SFWdemoState();
}

class SFWdemoState extends State<SFWdemo> {
  int _count = 0;

  @override
  Widget build(BuildContext context) {
		return Scaffold(
			...
		)
	}
}
```