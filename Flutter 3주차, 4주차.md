# 3주차

<!-- MainApp 지우면 빨간줄 뜨는거 인지시키기..? -->

### MaterialApp, Scaffold Widget

+ 기본 MaterialApp, Scaffold의 역할, 구조. 차이점 설명.

+ 가장 기본이 되는 Widget이기 때문에 먼저 설명해주는 것으로..

  ```dart
  // without MaterialApp, Scaffold
  
  import 'package:flutter/widgets.dart';
  
  void main() => runApp (NoMaterialApp ());
  
  class NoMaterialApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Container (
        padding: EdgeInsets.all(50),
        child: Text ("This is NOT Material App.", textDirection: TextDirection.ltr,),
      );
    }
  }
  ```

+ 둘 다 없는 경우, format이 전혀 없는 검은 화면의 흰 글씨만을 볼 수 있음. (어떠한 Layout, Design, alignment 설정 없음.)

  + **TextDirection.ltr** 있고 없고 비교시키기. (Design이나 direction에 대한 어떠한 style도 없는 코드이기 때문에, 없으면 오류발생.)

  + padding -> LeftTop에서 부터 all 방향으로의 padding 설정하는 **attributes**.

    <!-- Android xml과 동일하게 모든 widget의 모든 attributes를 정리해서 줄 수 없음을 강조. -->

  ```dart
  class ExMaterialApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp (
          title: "Material App",
          home: Container (
            padding: EdgeInsets.all (50),
            child: Text ("Now it is material application."),
          )
      );
    }
  }
  ```

+ 이래도 아직 정상적인 앱이라고 보기 힘듦.

  ```dart
  class RealMaterialApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp (
          title: "Material App",
          home: Scaffold (
            appBar: AppBar (
              title: Text("material + scaffold"),
            ),
            body: Text ("Now it is material application."),
          )
      );
    }
  }
  ```

+ 가장 기본적인 (계속 다루던) Application의 format 확인 가능.

+ MaterialApp은 **화면 이동 (route, 2주 뒤 학습) 와 테마 (theme)**을 주로 담당함. 

  + 주 색상, 강조 색상, 글꼴, 글자 style 등을 지정할 수 있음.

  + DarkTheme  attribute 설정 example.

    <!-- font family adding 하는 방식 -->

+ 



### 기본 Widget (Text, Image, Raised Button)

+ Text, Image, Raised Button 하나씩 포함되어있고, dark Theme, 일반 Theme을 임의로 설정한 어플리케이션 만들어서 제출 (**주차과제**)

  <!-- 모든 widget의 모든 attributes를 설명해 줄 수 없음을 강조. 책에서 제공하는 표 정도 만들어서 주기. -->

# 4주차

### Layout Widget (Container, Column, Raw)

+ **Column**, **Row** : VerticalLayout. vertical한 배치 지원.

  + mainAxisAlignment
    + 정렬 방향의 정렬 방식.
    + start, center, end
  + crossAxisAlignment
    + 정렬방향과 반대 방향으로의(*column widget에서는 세로 방향*)의 정렬 방식을 정하는 opt.
    + start, center, end.
  + children : 안에 넣어서 정렬시킬 Widget들 list. Container, Text, Image 다 넣을 수 있다.

+ **Container** : 리스트가 아닌 한 개의 자식을 갖는 layout widget.

  + padding

    + 내부 패딩.

    + **EdgeInset.only, symmetric method** 사용하여 설정.

      ```dart
      padding: EdgeInsets.only(left: 10, top: 20, bottom: 20)
      padding: EdgeInsets.symmetric(vertical: 30, horizontal: 50)
      ```

      

+ Android의 Layout들과 비슷한 역할을 하나, 훨씬 동적이고 자유로운 배치를 지원함.
+ **padding** options.

+ 로그인 화면 제작. (**주차과제**)
  + TextFormField Widget 힌트 주기.

```dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';

void main () => runApp(LoginForm ());

class LoginForm extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "LoginForm",
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        // appBar: AppBar(title: Text(),),
        body: Container (
          padding: EdgeInsets.fromLTRB(20, 120, 20, 120),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Image.asset(
                'assets/icon.jpg',
                width: 150,
                height: 150,
              ),
              SizedBox(height: 45.0,),
              TextFormField(
                keyboardType: TextInputType.emailAddress,
                initialValue: 'example@example.com',
                decoration: InputDecoration(
                    border: OutlineInputBorder(),
                 ),
              ),
              SizedBox(height: 15.0,),
              TextFormField(
                initialValue: "input password",
                obscureText: true,
                decoration: InputDecoration (
                  border: OutlineInputBorder (),
                ),
              ),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: <Widget>[
                  RaisedButton(
                      child: Text("Log In"),
                      onPressed: () {}),
                  SizedBox(width: 15.0,),
                  RaisedButton(
                      child: Text ("Cancel"),
                      onPressed: () {})
                ],
              )
            ],
          ),
        ),
      ),
    );
  }
}
```

<!-- 키보드 올라오면 UI 깨지는 현상. how to solve? -->

### ListView Widget

+ 문제 - 위의 것들을 다 하다보면 시간이 남을까 의문임. Service 하면서 추가로 학습시키는 방법도 고려해봐야할 듯.

