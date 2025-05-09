## 구구단 출력 코드

```dart
     void main(){
       for(var i = 1; i < 10; i++){
         for(var j = 1; j < 10; j++){
           print('$i * $j = ${i * j}');
          }
           print('');
        }
      }
```

## 꽉 찬 사각형 그리기 코드

```dart
    void main(){
      var n = 10;
        for(var i = 0; i < n; i++){
          var result = '';
          for(var j = 0; j < n; j++){
            result += '*';
          }
            print(result);
        }
      }
```

## 테두리 사각형 그리기 코드

```dart
      void main(){
        var n =10;
        for(var i = 0; i < n; i++){
          var result = '';
          for(var j = 0; j < n; j++){
            if(i == 0 || i == 9 || j == 0 || j == 9){
              result += '*';
            } else {
                result += '';
            }
          }
            print(result);
        }
      }
```

## /표시 사각형

```dart
      void main(){
        var n =10;
        for(var i = 0; i < n; i++){
          var result = '';
          for(var j = 0; j < n; j++){
            if(i == 0 || i == 9 || j == 0 || j == 9){
              result += '*';
            } else if(i + j == 9){
                result += '*';
            } else {
                result += '';
            }
          }
            print(result);
        }
      }
```
## \표시 사각형

```dart
      void main(){
        var n =10;
        for(var i = 0; i < n; i++){
          var result = '';
          for(var j = 0; j < n; j++){
            if(i == 0 || i == 9 || j == 0 || j == 9){
              result += '*';
            } else if(i == j){
                result += '*';
            } else {
                result += '';
            }
          }
            print(result);
        }
      }
```

## x표시 사각형 그리기 코드

```dart
  void main(){
        var n =10;
        for(var i = 0; i < n; i++){
          var result = '';
          for(var j = 0; j < n; j++){
            if(i == 0 || i == 9 || j == 0 || j == 9){
              result += '*';
            } else if(i == j){
                result += '*';
            } else if(i + j == 9){
                result += '*';
            } else {
                result += '';
          }
        }
          print(result);
        }
      }
```

## 년/월/일을 입력하면 요일을 출력하기

### ex)2025-03-11 --> 출력 : 화요일

```dart
    String changeDay(dateString){
        DateTime date = DateTime.parse(dateString);
        var days = ['월요일', '화요일', '수요일', '목요일', '금요일', '토요일', '일요일'];

        return days[date.weekday - 1];
    }

void main(){
    print(changeDay("2025-03-14"));
}
```
      























