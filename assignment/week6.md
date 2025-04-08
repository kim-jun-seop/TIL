# 6주차 과제

# FirstPage.dart

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

import 'Person.dart';
import 'SecondPage.dart';

class FirstPage extends StatelessWidget{
  @override
  Widget build(BuildContext context){
    return Scaffold(
      appBar: AppBar(
        title: Text('First'),
      ),
      body: ElevatedButton(
          onPressed: () async {
            final person = Person('홍길동',20);
            final result = await Navigator.pushNamed(
              context,
              '/second',
            );

            print(result);
          },
          child: Text('다음 페이지로')
      ),
    );
  }
}
```

# main.dart

```dart
import 'package:c_week6/FirstPage.dart';
import 'package:flutter/material.dart';

import 'SecondPage.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(

        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
      ),
      home: FirstPage(),
      routes: {
        '/first': (context) => FirstPage(),
        '/second': (context) => SecondPage(),
      },
    );
  }
}
```

# Person.dart

```dart
class Person{
  String name;
  int age;

  Person(this.name, this.age);
}
```

# SecondPage.dart

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'Person.dart';

class SecondPage extends StatelessWidget{
  Person? person;

  SecondPage({@required this.person});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second'),
      ),
      body: Column(
        children: [
          Text('${person?.name},${person?.age}'),
          ElevatedButton(
            onPressed: () {
              Navigator.pop(context, 'ok!!!');
          },
            child: Text('이전 페이지로')
      ),
      ],
      )
    );
  }
}
```
