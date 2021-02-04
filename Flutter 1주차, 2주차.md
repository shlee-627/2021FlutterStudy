# 1주차

+ 개발환경 설치.

  + Flutter SDK 설치, git 설치. 환경변수 설정.

    ```
    $ flutter doctor
    ```

  + Android Studio에 flutter plugin 설치.

+ Dart 언어 간략한 설명.  (책 chap. 3)

  + UML?
  + 기본 소개, 성능적 측면.
  + 간단한 문법.
  + Class, Inheritance, 형변환 등 꼭 알아야할 문법들 소개하기.

+ Flutter 프로젝트 구조.

  + 파일 structure.
  + main.dart 구조. 동작방식. (자동 주석 제거하고 코드 보여주기. )
  + **간단한 dart파일 새로 구성해서 hello world 띄우기.  **
    + AppBar background 색 바꿔서 제출.**(주차 과제)**
  + Android 프로젝트와 비교해보기.

```dart
import 'package:flutter/material.dart';

void main() => runApp (MaterialApp(
  title: "Hello Flutter!",
  home: Scaffold (
    appBar: AppBar(title: Text("My First Flutter Application")),
    body: Text ("Hello Flutter"),
  )
));
```

+ Flutter Framework is opensource.
  + git에 소스 공개되어있음.
+ App 구조. (Project Name이 어플리케이션 이름이 되고. android project가 형성된다는 것..? )

# 2주차

### Widget

+ 기본 개념.

  + What's widget.
  + **Life cycle of widget.** (especially Stateful)
  + Comparison with View (in Android).
  + **Stateless vs. Stateful. Inherited vs. Normal WIdget.**

+ Stateless Widget Example (구조가 바뀌는 경우는, 앱 껐다 켜야함.)

  ```dart
  import 'package:flutter/material.dart';
  
  void main() => runApp(MaterialApp(
    title: "Stateless Widget Demo",
    home: Scaffold (
      appBar: AppBar (title: Text ("Stateless Widget Test"), backgroundColor: Colors.white30,),
      body: _FirstStatelessWidget (),
    ),
  ));
  
  class _FirstStatelessWidget extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Text ("This is Stateless Widget");
    }
  }
  ```

+ Stateful Widget Example 

  + **Stateful Widget 생명주기 함수.**
  + Hot reload 시마다 count 증가 -> State가 return 하는 text가 바뀌는 코드 구현.
  + Random한 6개 숫자 매번 reload시 출력. (**주차과제**)
    + import 'dart:math'
    + var rng = new Random(), rng.nextInt (45)

  ```dart
  //Week2 StatefulWidget Example
  void main () => runApp (MaterialApp(
    title: 'Stateful Widget Demo',
    home: Scaffold (
      appBar: AppBar(title: Text ("Stateful Widget Test"),),
      body: _FirstStatefulWidget (),
    )
  ));
  
  class _FirstStatefulWidget extends StatefulWidget {
    @override
    State<StatefulWidget> createState() => _FirstStatefulWidgetState();
  }
  
  class _FirstStatefulWidgetState extends State<_FirstStatefulWidget> {
    int count = 1;
    @override
    Widget build(BuildContext context) {
      // TODO: implement build
      // throw UnimplementedError();
      count += 1;	
      return Text ("This is stateful Widget $count", style: TextStyle (fontWeight: FontWeight.bold));
    }
  }
  ```

  
  + <!--TODO--> button 추가해서 누를때마다 번호 바뀌는 어플리케이션 구상. 