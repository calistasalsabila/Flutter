# Dart Basics 🚀

## Introduction
Dart is the programming language used in Flutter. It is optimized for building mobile, desktop, server, and web applications. In this section, we will cover the fundamental concepts of Dart to build a strong foundation for Flutter development. 💡

---

## 1. Variables and Data Types 📝
### Purpose:
Variables are used to store data, and Dart supports multiple data types.

### Syntax:
```dart
void main() {
  String name = "Dokja"; // Text
  int age = 25; // Whole number
  double height = 5.9; // Decimal number
  bool isFlutterDeveloper = true; // Boolean
  
  print("Name: $name");
  print("Age: $age");
  print("Height: $height");
  print("Is Flutter Developer? $isFlutterDeveloper");
}
```

### Output:
```
Name: Dokja
Age: 25
Height: 5.9
Is Flutter Developer? true
```

### Explanation:
- `String`: Stores text.
- `int`: Stores whole numbers.
- `double`: Stores decimal numbers.
- `bool`: Stores `true` or `false` values.
- Dart supports **type inference**, so you can use `var` or `dynamic` to declare variables without specifying the type explicitly.

---

## 2. Control Flow (if-else & loops) 🔄
### Purpose:
Control flow statements allow decision-making and repeating actions based on conditions.

### Syntax:
```dart
void main() {
  int score = 85;

  if (score >= 90) {
    print("Excellent!");
  } else if (score >= 75) {
    print("Good Job!");
  } else {
    print("Keep Trying!");
  }
}
```

### Output:
```
Good Job!
```

### Explanation:
- `if` checks a condition and executes the corresponding block of code.
- `else if` adds more conditions.
- `else` runs if no other condition matches.

#### Loops Example:
```dart
void main() {
  for (int i = 1; i <= 5; i++) {
    print("Hello, Jeha! ($i)");
  }
}
```

### Output:
```
Hello, Jeha! (1)
Hello, Jeha! (2)
Hello, Jeha! (3)
Hello, Jeha! (4)
Hello, Jeha! (5)
```

---

## 3. Functions 🛠️
### Purpose:
Functions allow you to organize reusable blocks of code.

### Syntax:
```dart
void greet(String name) {
  print("Hello, $name!");
}

void main() {
  greet("Hamin");
  greet("Dazai");
}
```

### Output:
```
Hello, Hamin!
Hello, Dazai!
```

### Explanation:
- `void` means the function does not return a value.
- Parameters like `String name` allow input values.
- Functions help keep code organized and reusable.

---

## 4. Classes & Objects 🏗️
### Purpose:
Dart is an object-oriented language, so understanding classes is crucial.

### Syntax:
```dart
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void introduce() {
    print("Hi, I'm $name and I'm $age years old.");
  }
}

void main() {
  Person dokja = Person("Dokja", 25);
  dokja.introduce();
}
```

### Output:
```
Hi, I'm Dokja and I'm 25 years old.
```

### Explanation:
- `class` defines a blueprint for objects.
- `this.name` and `this.age` initialize the properties.
- `introduce()` is a method that prints a message.
- `Person dokja = Person("Dokja", 25);` creates an instance of the class.

---

## Summary 📌
| Concept           | Description |
|------------------|-------------|
| Variables & Data Types | Store values with different types (String, int, double, bool). |
| Control Flow | Use `if-else` and loops to make decisions and repeat actions. |
| Functions | Encapsulate reusable code blocks. |
| Classes & Objects | Represent real-world entities using object-oriented programming. |

---

🚀 Now that you know the basics of Dart, you’re ready to dive into Flutter! Happy coding! 🎉

