# Widgets Basics 🎨

## Introduction
Widgets are the building blocks of a Flutter app. Everything in Flutter is a widget, from simple text elements to complex layouts. In this section, we will explore two main types of widgets: **Stateless Widgets** and **Stateful Widgets**. 🏗️

---

## 1. Stateless Widgets 🧱
### Purpose:
A **Stateless Widget** does not change once it is built. It is **immutable**, meaning its properties cannot be updated dynamically.

### Syntax:
```dart
import 'package:flutter/material.dart';

class MyStatelessWidget extends StatelessWidget {
  final String message;

  MyStatelessWidget({required this.message});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Stateless Widget")),
      body: Center(
        child: Text(
          message,
          style: TextStyle(fontSize: 24),
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: MyStatelessWidget(message: "Hello, Dokja!"),
  ));
}
```

### Output:
A screen with the text **"Hello, Dokja!"** displayed in the center.

### Explanation:
- `StatelessWidget` does **not** maintain any state.
- The `message` property is passed once and cannot be changed later.
- `build` method creates the UI structure.

---

## 2. Stateful Widgets 🔄
### Purpose:
A **Stateful Widget** can change dynamically while the app is running. It has an internal state that can be modified using `setState()`.

### Syntax:
```dart
import 'package:flutter/material.dart';

class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Stateful Widget")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              "Counter: $counter",
              style: TextStyle(fontSize: 24),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: incrementCounter,
              child: Text("Increment"),
            ),
          ],
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: MyStatefulWidget(),
  ));
}
```

### Output:
A screen displaying a counter starting at `0`, with a button labeled **"Increment"**. Pressing the button increases the counter value.

### Explanation:
- `StatefulWidget` maintains **state** that can change.
- `_MyStatefulWidgetState` contains `counter` variable to track the count.
- `setState()` updates the UI when the counter is incremented.

---

## Summary 📌
| Widget Type       | Description |
|------------------|-------------|
| Stateless Widget | Does not change after being built. Useful for static UI components. |
| Stateful Widget  | Can change dynamically using `setState()`. Useful for interactive elements. |

---

🚀 Now that you understand **Stateless** and **Stateful** widgets, you’re ready to build dynamic UIs in Flutter! 🎉

