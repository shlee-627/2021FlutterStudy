# 5주차

### 화면 이동 (Navigator Class)

+ **Navigator** Class

  + Android와 비슷하게 back stack을 관리하는 듯한 API구조.

  ```dart
  _showNextPage (BuildContext context) => Navigator.push(context, 
                                                MaterialPageRoute(builder: (context) => NextPage ()));
  
  _showPrevPage (BuildContext context) => Navigator.pop (context);
  ```

  + context
    + **BuildContext**, flutter의 내부에 해당하는 객체. 
  + Android **Intent**와 비교. 
  + 각 페이지의 상위단에서 **전체 페이지의 경로를 정의**할 수 있음.

  ```dart
  import 'package:flutter/material.dart';
  
  void main () => runApp(MainApp ());
  
  class MainApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        initialRoute: '/',
        routes: {
          '/' : (context) => FirstPage (),
          '/next' : (context) => SecondPage (),
        },
      );
    }
  }
  
  class FirstPage extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar (title: Text("First Page"),),
        body: Center(
          child: RaisedButton (
            onPressed: () => Navigator.pushNamed(context, '/next'),
            child: Text("Go To Next"),
          ),
        ),
      );
    }
  }
  
  class SecondPage extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar (title: Text("Second Page "),),
        body: Center(
          child: RaisedButton (
            onPressed: () => Navigator.pop (context),
            child: Text("Back to Prev"),
          ),
        ),
      );
    }
  }
  ```

  + AppBar 내의 back 버튼은 자동 생성? 
    + 찾아보기

### Dynamic Route

+ 상세 정보 전달. (**Like Intent Message**)
+ 개념만 설명하고. 간단한 예제 작성.

```

```

+ Contact example 주고 dynamically 세부 정보 page 띄우게. (**주차 과제**)
  + `contact_app_ex` project.
  + permission 문제 다루기. (미리 설명해주기.)



# 6주차