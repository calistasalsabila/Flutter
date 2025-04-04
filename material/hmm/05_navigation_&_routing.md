# Navigation & Routing 🚀

## Introduction
Navigation in Flutter allows users to move between different screens (or pages). Flutter provides multiple ways to manage navigation and routing, including:

- **`Navigator.push()` & `Navigator.pop()`** 🔄 (Basic Navigation)
- **Named Routes** 📛 (Structured Routing)
- **`onGenerateRoute`** 🛣️ (Dynamic Routing)

Understanding navigation is crucial for building multi-page applications. Let's dive into it! 🎯

---

## 1. Basic Navigation 🔄
### Purpose:
The `Navigator` manages a stack of routes (screens). `Navigator.push()` adds a new screen, and `Navigator.pop()` removes the current screen.

### Syntax:
```dart
import 'package:flutter/material.dart';

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("First Screen")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
          },
          child: Text("Go to Second Screen"),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second Screen")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text("Go Back"),
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: FirstScreen(),
  ));
}
```

### Output:
- Pressing **"Go to Second Screen"** opens a new screen.
- Pressing **"Go Back"** returns to the first screen.

### Explanation:
- `Navigator.push()` moves to a new screen.
- `Navigator.pop()` removes the current screen and returns to the previous one.

---

## 2. Named Routes 📛
### Purpose:
Named routes make navigation **structured** and **manageable**, especially for large apps.

### Syntax:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    initialRoute: '/',
    routes: {
      '/': (context) => HomeScreen(),
      '/second': (context) => SecondScreen(),
    },
  ));
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Home Screen")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/second');
          },
          child: Text("Go to Second Screen"),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Second Screen")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text("Go Back"),
        ),
      ),
    );
  }
}
```

### Output:
- Clicking **"Go to Second Screen"** navigates using the **named route**.
- Clicking **"Go Back"** returns to the home screen.

### Explanation:
- `initialRoute` defines the starting screen.
- `routes` map route names (`/`, `/second`) to widget screens.
- `Navigator.pushNamed()` navigates using a route name.

---

## 3. Dynamic Routing (`onGenerateRoute`) 🛣️
### Purpose:
For **dynamic and parameterized navigation**, `onGenerateRoute` is used.

### Syntax:
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(
    initialRoute: '/',
    onGenerateRoute: (settings) {
      if (settings.name == '/profile') {
        final String username = settings.arguments as String;
        return MaterialPageRoute(
          builder: (context) => ProfileScreen(username: username),
        );
      }
      return null;
    },
    home: HomeScreen(),
  ));
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Home Screen")),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pushNamed(
              context,
              '/profile',
              arguments: 'Dokja',
            );
          },
          child: Text("Go to Profile"),
        ),
      ),
    );
  }
}

class ProfileScreen extends StatelessWidget {
  final String username;
  ProfileScreen({required this.username});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Profile Screen")),
      body: Center(
        child: Text("Welcome, $username!", style: TextStyle(fontSize: 24)),
      ),
    );
  }
}
```

### Output:
- Pressing **"Go to Profile"** navigates to a personalized profile screen with `Welcome, Dokja!`.

### Explanation:
- `onGenerateRoute` dynamically maps routes to widgets.
- `settings.arguments` passes data to the new screen.
- `Navigator.pushNamed()` navigates while passing parameters.

---

## Summary 📌
| Navigation Type  | Description |
|----------------|-------------|
| `Navigator.push()` & `Navigator.pop()` | Basic navigation using screen stacks. |
| Named Routes | Predefined routes for cleaner navigation. |
| `onGenerateRoute` | Dynamic navigation with arguments. |

---

🚀 Now that you understand **navigation & routing**, you're ready to build multi-screen Flutter apps! 🎉

