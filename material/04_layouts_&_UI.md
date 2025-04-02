# Layouts & UI 🎨

## Introduction
In Flutter, **layouts** are created using widgets. Flutter provides several layout widgets to arrange UI components in different ways. In this section, we'll cover the most commonly used layout widgets:

- **Column** 📏 (Vertical layout)
- **Row** 📏 (Horizontal layout)
- **Stack** 📚 (Overlapping widgets)
- **ListView** 📜 (Scrollable list)

Understanding these layout widgets is essential for designing responsive and interactive UI in Flutter. 🚀

---

## 1. Column 📏 (Vertical Layout)
### Purpose:
A **Column** widget arranges children **vertically** from top to bottom.

### Syntax:
```dart
import 'package:flutter/material.dart';

class ColumnExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Column Example")),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        crossAxisAlignment: CrossAxisAlignment.start,
        children: [
          Text("Hello, Dokja!", style: TextStyle(fontSize: 24)),
          Text("Hello, Jeha!", style: TextStyle(fontSize: 24)),
          Text("Hello, Hamin!", style: TextStyle(fontSize: 24)),
        ],
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: ColumnExample(),
  ));
}
```

### Output:
Displays three text widgets stacked **vertically**.

### Explanation:
- `mainAxisAlignment` controls vertical spacing (e.g., `center`, `start`, `end`, `spaceEvenly`).
- `crossAxisAlignment` controls horizontal alignment (e.g., `start`, `center`, `end`).
- Children are arranged from **top to bottom**.

---

## 2. Row 📏 (Horizontal Layout)
### Purpose:
A **Row** widget arranges children **horizontally** from left to right.

### Syntax:
```dart
import 'package:flutter/material.dart';

class RowExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Row Example")),
      body: Center(
        child: Row(
          mainAxisAlignment: MainAxisAlignment.spaceAround,
          children: [
            Text("Dokja", style: TextStyle(fontSize: 24)),
            Text("Jeha", style: TextStyle(fontSize: 24)),
            Text("Hamin", style: TextStyle(fontSize: 24)),
          ],
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: RowExample(),
  ));
}
```

### Output:
Displays three text widgets arranged **horizontally**.

### Explanation:
- `mainAxisAlignment` controls horizontal spacing (e.g., `start`, `center`, `spaceAround`).
- `crossAxisAlignment` aligns children vertically within the row.
- Children are arranged from **left to right**.

---

## 3. Stack 📚 (Overlapping Widgets)
### Purpose:
A **Stack** widget places widgets **on top of each other**, like layers.

### Syntax:
```dart
import 'package:flutter/material.dart';

class StackExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Stack Example")),
      body: Center(
        child: Stack(
          alignment: Alignment.center,
          children: [
            Container(width: 200, height: 200, color: Colors.blue),
            Container(width: 150, height: 150, color: Colors.red),
            Container(width: 100, height: 100, color: Colors.yellow),
          ],
        ),
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: StackExample(),
  ));
}
```

### Output:
A **blue** square, with a **red** square on top, and a **yellow** square on top of both.

### Explanation:
- Widgets are **layered** in order, with the last widget appearing on top.
- `alignment` controls how widgets are positioned inside the Stack (e.g., `center`, `topLeft`).

---

## 4. ListView 📜 (Scrollable List)
### Purpose:
A **ListView** is used to display a **scrollable list** of widgets.

### Syntax:
```dart
import 'package:flutter/material.dart';

class ListViewExample extends StatelessWidget {
  final List<String> names = ["Dokja", "Jeha", "Hamin", "Dazai", "Kim", "Lee"];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("ListView Example")),
      body: ListView.builder(
        itemCount: names.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(names[index]),
            leading: Icon(Icons.person),
          );
        },
      ),
    );
  }
}

void main() {
  runApp(MaterialApp(
    home: ListViewExample(),
  ));
}
```

### Output:
A **scrollable** list of names with person icons.

### Explanation:
- `ListView.builder` creates an efficient, **dynamic** list.
- `itemCount` determines the total number of items.
- `itemBuilder` generates each list item.

---

## Summary 📌
| Layout Widget | Description |
|--------------|-------------|
| Column | Arranges widgets **vertically**. |
| Row | Arranges widgets **horizontally**. |
| Stack | Overlaps widgets on top of each other. |
| ListView | Displays a **scrollable** list. |

---

🚀 Now that you understand **layout widgets**, you're ready to build beautiful UI in Flutter! 🎉