# Jan. 30th Study

#### TODO

+ ~~개발환경 구축~~
+ ~~기본 앱 구현 해보기~~
+ stateful, stateless Widget 하나씩 써보고 감 익히기.
+ Dart 언어 기본 구조 찾아보기.

### Flutter Basic

+ 기존 android와 형태는 유사.

+ AoT (Ahead of Time) 방식으로 Dart 언어가 native 언어들로 변환 되어 설치되는 방식.

+ Dart 언어의 **성능적 측면**이 빠른 변환, 성능적 측면의 이점을 가져와 주는 것.

  ```dart
  void main () {
      runApp (MainApp ());
  }
  ```


### Widget

+ Widgets describe what their view should look like given their current configuration and state.

+ **Widget Tree.**

+ *MaterialApp?*...

  ```dart
  void main() {
    runApp(
      Center(		// Center is a new widget tree's root. (runApp function set Center as a root)
        child: Text(			// Center widget's child widget.
          'Hello, world!',
          textDirection: TextDirection.ltr,
        ),
      ),
    );
  }
  ```

  

+ A widget’s <u>main job is to implement a `build ()`function,</u> which describes the widget in terms of other, lower-level widgets.

+ framework builds this widget.. (framework가 widget을 그린다..?)

+ 정확한 구동방식, 그리는 방식에 대한 이해도 필요할 듯... (설명하려면..)

+ **Widget == View (in Android)**

### Stateless Widget & Stateful Widget

+ Widget은 모두 **build 함수** (override method)를 필수적으로 가져야 함.
+ Scaffold?

+ **Stateless Widget**
  
  + 앱 구동중에 속성을 변경할 수 없는 widget.
+ **Stateful Widget** 
  
  + 쉽게 말해서 앱 구동중에 내용이나 모양 바꿀 수 있는 widget.
  
  + Main Widget이나 큰 덩어리가 아니더라도, 매 번 contents를 바꿀 수 있도록 구현하려면 필요한 듯...?
  
  + State Class를 구현해서 붙여줘야함.
  
    + 매 State를 생성하고 만들어주는 class 별도로 붙여야 함.
  
      ```dart
      StateClass createState () => StateClass ();
      ```
  

### Conclusion

+ 단순한 앱을 만들어 본 결과. **파일을 다수 생성하지 않고도** 앱을 만들 수 있다(?) 라는 장점 있어보이고,
+ ListView를 생성하는 것 자체도 **직관...적? 이고, 쉽다**.



### Reference

http://murmurblog.com/flutter-widget/

https://flutter-ko.dev/docs/development/ui/widgets-intro

https://medium.com/@dan_kim/%EB%B2%88%EC%97%AD-flutter-%EC%9C%84%EC%A0%AF-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0-1a22231d25c6







