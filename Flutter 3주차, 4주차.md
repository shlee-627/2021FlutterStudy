# 3주차

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

+ MaterialApp은 **화면 이동 (route)와 테마 (theme)**을 주로 담당함. 

  + 주 색상, 강조 색상, 글꼴, 글자 style 등을 지정할 수 있음.

  + DarkTheme  attribute 설정 example.

    <!-- font family adding 하는 방식 -->



### 기본 Widget (Text, Image, Raised Button)

+ Text, Image, Raised Button 하나씩 포함되어있고, dark Theme, 일반 Theme을 임의로 설정한 어플리케이션 만들어서 제출 (**주차과제**)

  <!-- 모든 widget의 모든 attributes를 설명해 줄 수 없음을 강조. 책에서 제공하는 표 정도 만들어서 주기. -->

# 4주차

### Layout Widget (Container, Column, Raw)



### ListView Widget



