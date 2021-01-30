# DART Lang. Basic

*Reference : https://blockdmask.tistory.com/393*

+ C 같은 python 느낌의 언어...

+ is : Type 검사

  ```dart
  class Point { int x; int y; } 
  class PointDetail extends Point { int z; }
  
  void main() { 
      Point point = Point(); 
      point.x = 4; // Use the setter method for x. 
      point.y = 5; 
      if (point is PointDetail) { 
          PointDetail p = point as PointDetail; //다운 캐스팅 
          print("Yes"); 
      } else { 
          print("No"); 
      } 
  }
  ```

  

+ as : **Type Casting**

  + Use the as operator to cast an object to a particular type if and only if you are sure that the object is of that type.

  ```dart
  int a = 33;
  int b = a as int;
  ```

  

+ *_를 변수 앞에 붙이면 private* (**Dart 문법**)