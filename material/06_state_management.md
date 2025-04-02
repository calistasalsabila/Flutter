# State Management in Flutter 🔄

## Introduction
State management is a crucial part of Flutter development. It determines how UI updates when data changes. In this section, we'll cover three common state management approaches:

- **`setState()`** 🛠️ (Basic state management)
- **Provider** 🔌 (Scoped state management)
- **Riverpod** 🌊 (Advanced, safer state management)

Understanding these methods will help you build efficient and scalable Flutter apps. 🚀

---

## 1. `setState()` 🛠️
### Purpose:
`setState()` is the simplest way to manage state **within a single widget**.

### Syntax:
```dart
import 'package:flutter/material.dart';

class CounterApp extends StatefulWidget {
  @override
  _CounterAppState createState() => _CounterAppState();
}

class _CounterAppState extends State<CounterApp> {
  int counter = 0;

  void incrementCounter() {
    setState(() {
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Counter App")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text("Counter: $counter", style: TextStyle(fontSize: 24)),
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
    home: CounterApp(),
  ));
}
```

### Output:
A counter that updates **when the button is pressed**.

### Explanation:
- `setState()` triggers UI rebuilds when `counter` changes.
- Best for **small apps** or stateful widgets that don’t affect other widgets.

---

## 2. Provider 🔌
### Purpose:
**Provider** allows state management across **multiple widgets** efficiently.

### Setup:
1. **Add dependency** in `pubspec.yaml`:
```yaml
dependencies:
  provider: ^6.0.5
```
2. **Usage**
```dart
import 'package:flutter/material.dart';
import 'package:provider/provider.dart';

void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => CounterProvider(),
      child: MyApp(),
    ),
  );
}

class CounterProvider extends ChangeNotifier {
  int counter = 0;

  void incrementCounter() {
    counter++;
    notifyListeners();
  }
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CounterScreen(),
    );
  }
}

class CounterScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final counterProvider = Provider.of<CounterProvider>(context);

    return Scaffold(
      appBar: AppBar(title: Text("Provider Example")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text("Counter: ${counterProvider.counter}", style: TextStyle(fontSize: 24)),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: counterProvider.incrementCounter,
              child: Text("Increment"),
            ),
          ],
        ),
      ),
    );
  }
}
```

### Output:
A counter that updates **across multiple widgets**.

### Explanation:
- `ChangeNotifier` notifies listeners when data changes.
- `ChangeNotifierProvider` provides state globally.
- `Provider.of<T>(context)` accesses state.
- Suitable for **medium-sized apps**.

---

## 3. Riverpod 🌊
### Purpose:
**Riverpod** improves on Provider by making state management **safer and more scalable**.

### Setup:
1. **Add dependency** in `pubspec.yaml`:
```yaml
dependencies:
  flutter_riverpod: ^2.3.2
```
2. **Usage**
```dart
import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';

final counterProvider = StateProvider<int>((ref) => 0);

void main() {
  runApp(ProviderScope(child: MyApp()));
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CounterScreen(),
    );
  }
}

class CounterScreen extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final counter = ref.watch(counterProvider);

    return Scaffold(
      appBar: AppBar(title: Text("Riverpod Example")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text("Counter: $counter", style: TextStyle(fontSize: 24)),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: () => ref.read(counterProvider.notifier).state++,
              child: Text("Increment"),
            ),
          ],
        ),
      ),
    );
  }
}
```

### Output:
A counter that updates **efficiently with Riverpod**.

### Explanation:
- `ProviderScope` is the root of all Riverpod providers.
- `StateProvider` manages a simple piece of state.
- `ref.watch()` listens to state updates.
- `ref.read().notifier.state++` updates state.
- Great for **large-scale apps**.

---

## Summary 📌
| State Management | Description |
|----------------|-------------|
| `setState()` | Local state, easy to use but limited to a single widget. |
| Provider | Efficient for app-wide state management, using `ChangeNotifier`. |
| Riverpod | Advanced and safe state management with better structure. |

---

🚀 Now that you understand **state management**, you’re ready to manage complex app states efficiently! 🎉

