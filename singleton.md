```dart
   import 'package:flutter/material.dart';

  class Singleton {
    late int count;
   //late를 안붙이면 error: Non-nullable instance field 'count' must be initialized
  
    static final Singleton _instance = Singleton._internal();
   //'_'는 private
    //기본값이 설정된 Singleton._internal()을 변수 _instance에 넣기

    factory Singleton() => _instance;
    //factory를 플러터에서 싱글톤 패턴을 사용할 때 쓰는 (??근데 왜? factory의 특징은?)
    //Singleton()의 인스턴스를 생성하면 _instance를 반환
  
   // = factory Singleton() {return _instance}; 랑 같은 코드

    Singleton._internal() {
     count = 0;
      print("Singleton was created");
    }
  }
   //맨 처음 인스턴스를 생성할 때만 사용되어지고 그다음부턴 적용X (근데 어떻게?? 어떠한 이유로 이건 넘어가는 거?? 원리 이해 ㄴ)

  void main() {
  var one = Singleton();
  one.count++;
  print(one.count); //1

  var two = Singleton();
  var three = Singleton();
  two.count++;
  three.count++;
   //이 부분 이해안된다 위에는 왜 1이고 뒤에 print는 3이쥐?
 //=> 이유는 그냥 Singleton() 이거로 인스턴스를 100개 만들어도 
 //그냥 하나에 클래스에 같은 값이 들어가는 거니까

    print(two.count); //3
  print(three.count);//3
  }
```
