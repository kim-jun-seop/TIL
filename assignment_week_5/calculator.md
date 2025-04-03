# 계산기

## 너무 어렵다...

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const CalculatorApp());
}

class CalculatorApp extends StatelessWidget {
  const CalculatorApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '계산기',
      debugShowCheckedModeBanner: false,
      theme: ThemeData.dark().copyWith(
        scaffoldBackgroundColor: Colors.black,
      ),
      home: const CalculatorScreen(),
    );
  }
}

class CalculatorScreen extends StatelessWidget {
  const CalculatorScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Column(
          children: [
            // 상단 디스플레이 영역
            Expanded(
              flex: 2,
              child: Container(
                alignment: Alignment.bottomRight,
                padding: const EdgeInsets.all(20),
                child: const Text(
                  '0',
                  style: TextStyle(fontSize: 60, color: Colors.white),
                ),
              ),
            ),

            // 버튼 영역
            Expanded(
              flex: 5,
              child: Column(
                children: [
                  buildButtonRow(['%', 'CE', 'C', Icons.backspace]),
                  buildButtonRow(['1/x', 'x²', '√x', '÷']),
                  buildButtonRow(['7', '8', '9', '×']),
                  buildButtonRow(['4', '5', '6', '−']),
                  buildButtonRow(['1', '2', '3', '+']),
                  buildButtonRow(['+/-', '0', '.', '=']),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }

  Widget buildButtonRow(List<dynamic> labels) {
    return Row(
      children: labels.map((label) {
        int flex = 1;

        return Expanded(
          flex: flex,
          child: Padding(
            padding: const EdgeInsets.all(4.0),
            child: SizedBox(
              height: 100, // 버튼 높이 고정
              child: ElevatedButton(
                onPressed: () {},
                style: ElevatedButton.styleFrom(
                  backgroundColor:
                  label == '=' ? Colors.lightBlue : const Color(0xFF2E2E2E),
                  shape: RoundedRectangleBorder(
                    borderRadius: BorderRadius.circular(8),
                  ),
                ),
                child: label is IconData
                    ? Icon(label, color: Colors.white, size: 24)
                    : Center(
                  child: Text(
                    label,
                    style: const TextStyle(
                        fontSize: 20, color: Colors.white),
                  ),
                ),
              ),
            ),
          ),
        );
      }).toList(),
    );
  }

  Widget buildButton(dynamic label) {
    return Expanded(
      child: Padding(
        padding: const EdgeInsets.all(2),
        child: ElevatedButton(
          onPressed: () {},
          style: ElevatedButton.styleFrom(
            backgroundColor: label == '=' ? Colors.lightBlue : const Color(0xFF2E2E2E),
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(8),
            ),
            padding: const EdgeInsets.all(0),
          ),
          child: label is IconData
              ? Icon(label, color: Colors.white, size: 26)
              : Text(
            label,
            style: const TextStyle(fontSize: 22, color: Colors.white),
          ),
        ),
      ),
    );
  }
}
