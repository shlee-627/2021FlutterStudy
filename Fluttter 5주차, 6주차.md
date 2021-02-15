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

```dart
import 'package:flutter/material.dart';

void main () => runApp(MainApp());

class PersonalInfo {
  final String name;
  final String number;

  PersonalInfo (this.name, this.number);
}

class MainApp extends StatelessWidget {

  final MaterialPageRoute _noWay = MaterialPageRoute(
      builder: (_) => Scaffold(
          body: Center(
            child: Text ("Invalid Path"),
          )
  ));

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "dynamic_app_ex",
      home: MainPage (),
      onGenerateRoute: (RouteSettings settings) {
        if (DetailPage.routeName == settings.name) {
          PersonalInfo info = settings.arguments;

          return MaterialPageRoute(builder: (context) => DetailPage(info));
        }
        return _noWay;
      },
    );
  }
}

class MainPage extends StatefulWidget {
  @override
  State createState() => MainAppState();
}

class MainAppState extends State<MainPage> {
  final nameCtrl = TextEditingController();
  final numCtrl = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar (title: Text("Dynamic Routing Ex"),),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            TextFormField(
              controller: nameCtrl,
              decoration: InputDecoration(
                border: OutlineInputBorder (),
              ),
            ),
            SizedBox(height: 5.0,),
            TextFormField(
              controller: numCtrl,
              decoration: InputDecoration(
                border: OutlineInputBorder (),
              ),
            ),
            SizedBox(height: 5.0,),
            RaisedButton(
                child: Text ("Submit"),
                onPressed: () => Navigator.pushNamed(context, DetailPage.routeName, arguments: PersonalInfo(nameCtrl.text, numCtrl.text)))
          ],
        ),
      ),
    );
  }
}

class DetailPage extends StatelessWidget {
  static const String routeName = '/detail';
  final PersonalInfo _info;

  DetailPage(this._info);
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Detailed Info Page "),),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text ("Name : " + _info.name),
            Text ("Phone Number : " + _info.number)
          ],
        ),
      ),
    );
  }
}
```

+ Contact example 주고 dynamically 세부 정보 page 띄우게. (**주차 과제**)
  + `contact_app_ex` project.
  + permission 문제 다루기. (미리 설명해주기.)
+ **State** Management.



# 6주차

<!-- https://jsonplaceholder.typicode.com/ -->

### HTTP Connection & Async Communication

+ `pubspec.yaml` 파일에 dependency 추가.

  ```yaml
  dependencies:
    http: ^0.12.0+2
  ```

+ Simple HTTP communication with jsonplaceholder web.

  + 비동기적 방식. 
  + **await**

  ```dart
  import 'package:http/http.dart';
  
  // Simple http communication
  void main() async {
    String url = "https://jsonplaceholder.typicode.com/todos/1";
  
    var resp = await http.get(url);
  
    print ("Status = ${resp.statusCode}");
    print ("Resp = ${resp.body}");
  }
  ```

  

### JSON Parsing

+ 서울 지하철 실시간 도착 정보 parsing. API 연동?

  <!-- http://data.seoul.go.kr/dataList/OA-12764/F/1/datasetView.do -->

+ 인증키 받는 routine 보여주기. *(이런식으로 open API를 신청해서 쓸 수 있는게 많다.)

  + *신청해서 받는데 오래걸림..*
  + http://swopenapi.seoul.go.kr/api/subway/785043514e736b3138394959506779/json/realtimeStationArrival/1/5/성균관대

+ Naver API

  + 바로 받아서 보여줄 수 있음. 

  ```dart
  import 'package:flutter/material.dart';
  import 'package:http/http.dart' as http;
  
  // Simple http communication
  void main() async {
    // String url = "https://jsonplaceholder.typicode.com/todos/1";
    String input = "플러터";
    String url = "https://openapi.naver.com/v1/search/blog.json?query=" + input;
    var requestHdr = {"X-Naver-Client-Id" : "1nfiYTL5EILLoh9FZHsK", "X-Naver-Client-Secret" : "8iz3PrleNQ"};
  
    var resp = await http.get(url, headers: requestHdr);
  
    print ("Status = ${resp.statusCode}");
    print ("Resp = ${resp.body}");
  }
  ```

  + <!-- https://openapi.naver.com/v1/search/blog.json?query=; -->

+ TextFromField로 텍스트 (쿼리) 받고, API로 검색결과 받아와서 **result.dart**에 포맷팅해서 출력. (**주차 과제**)

