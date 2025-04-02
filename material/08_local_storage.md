# Local Storage in Flutter 🗄️

## Introduction
Local storage allows Flutter apps to save data **permanently** on the device. Some common methods include:

- **Hive** 🐝 (Fast NoSQL database)
- **SQLite** 🗄️ (Relational database for structured data)
- **Shared Preferences** 🔖 (Key-value storage for simple data)

Let’s explore each method in detail. 🚀

---

## 1. Hive 🐝 (NoSQL Storage)
### Purpose:
Hive is a lightweight and high-performance NoSQL database for Flutter.

### Installation:
Add Hive dependencies in `pubspec.yaml`:
```yaml
dependencies:
  hive: ^2.2.3
  hive_flutter: ^1.1.0

dev_dependencies:
  hive_generator: ^2.0.0
  build_runner: ^2.3.2
```

### Initialize Hive:
```dart
import 'package:flutter/material.dart';
import 'package:hive_flutter/hive_flutter.dart';

void main() async {
  await Hive.initFlutter();
  await Hive.openBox('myBox');
  runApp(MyApp());
}
```

### Save & Retrieve Data:
```dart
void saveData(String key, String value) {
  var box = Hive.box('myBox');
  box.put(key, value);
}

String? getData(String key) {
  var box = Hive.box('myBox');
  return box.get(key);
}
```

### Output:
Stores and retrieves **key-value pairs** efficiently.

### Best Use Case:
- Storing **lists, maps, and objects**.
- Faster than SQLite for small-scale data.

---

## 2. SQLite 🗄️ (Relational Database)
### Purpose:
SQLite is a structured database for **storing complex data**.

### Installation:
Add `sqflite` dependency:
```yaml
dependencies:
  sqflite: ^2.2.6
  path_provider: ^2.1.1
```

### Initialize Database:
```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';

Future<Database> initDatabase() async {
  return openDatabase(
    join(await getDatabasesPath(), 'my_database.db'),
    onCreate: (db, version) {
      return db.execute(
        "CREATE TABLE users(id INTEGER PRIMARY KEY, name TEXT, age INTEGER)",
      );
    },
    version: 1,
  );
}
```

### Insert & Retrieve Data:
```dart
Future<void> insertUser(Map<String, dynamic> user) async {
  final db = await initDatabase();
  await db.insert('users', user);
}

Future<List<Map<String, dynamic>>> getUsers() async {
  final db = await initDatabase();
  return await db.query('users');
}
```

### Output:
Stores and retrieves **structured relational data**.

### Best Use Case:
- When data has **relationships**.
- Ideal for apps requiring **complex queries**.

---

## 3. Shared Preferences 🔖 (Key-Value Storage)
### Purpose:
Shared Preferences is a simple way to store **small data** persistently.

### Installation:
Add `shared_preferences` dependency:
```yaml
dependencies:
  shared_preferences: ^2.2.0
```

### Save & Retrieve Data:
```dart
import 'package:shared_preferences/shared_preferences.dart';

Future<void> saveString(String key, String value) async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString(key, value);
}

Future<String?> getString(String key) async {
  final prefs = await SharedPreferences.getInstance();
  return prefs.getString(key);
}
```

### Output:
Stores **primitive data types** like `String`, `int`, `bool`.

### Best Use Case:
- **User settings, preferences, and simple flags**.
- **Does not support complex objects**.

---

## Summary 📌
| Storage Type | Use Case |
|-------------|----------|
| **Hive** 🐝 | Best for storing objects, maps, and lists (fast & lightweight) |
| **SQLite** 🗄️ | Best for structured relational data with complex queries |
| **Shared Preferences** 🔖 | Best for simple key-value storage like user settings |

---

🚀 Now you know how to store data locally in Flutter! Happy coding! 🎉