# 📌 Positional vs Named Parameters: Dart, Java, and Python

## **🛠️ Purpose**
Understanding how positional and named parameters work in Dart, Java, and Python, including their syntax, usage, and flexibility. This helps in writing cleaner and more maintainable code. 🚀

---
## **📖 Theoretical Explanation**
### **1️⃣ Positional Parameters**
📌 **Definition**: Positional parameters are arguments that must be passed in the correct order when calling a function.
- ✅ Required unless default values are provided.
- ✅ Order-sensitive.
- ❌ Cannot be skipped without a default value.

### **2️⃣ Named Parameters**
📌 **Definition**: Named parameters allow specifying arguments by name, making function calls more readable.
- ✅ Order-independent.
- ✅ Can be optional with default values.
- ❌ Not directly available in Java (must use Builder Pattern or method overloading).

### **3️⃣ Flexible Parameters (`*args`, `**kwargs`)**
📌 **Definition**: Special syntax in Python that allows passing an arbitrary number of arguments.
- ✅ `*args`: Handles multiple positional arguments.
- ✅ `**kwargs`: Handles multiple named arguments as a dictionary.

---
## **📌 Code Examples & Outputs**

### **Dart: Positional Parameters**
```dart
void examplePositional(int num1, int num2) {
  print('First number: \$num1');
  print('Second number: \$num2');
}

void main() {
  examplePositional(10, 20);
}
```
**🖥️ Output:**
```
First number: 10
Second number: 20
```

---
### **Java: Positional Parameters**
```java
public class Main {
    static void examplePositional(int num1, int num2) {
        System.out.println("First number: " + num1);
        System.out.println("Second number: " + num2);
    }

    public static void main(String[] args) {
        examplePositional(10, 20);
    }
}
```
**🖥️ Output:**
```
First number: 10
Second number: 20
```

---
### **Python: Positional Parameters**
```python
def example_positional(num1, num2):
    print(f"First number: {num1}")
    print(f"Second number: {num2}")

example_positional(10, 20)
```
**🖥️ Output:**
```
First number: 10
Second number: 20
```

---
### **Dart: Named Parameters**
```dart
void exampleNamed({int? num1, int? num2}) {
  print('First number: \$num1');
  print('Second number: \$num2');
}

void main() {
  exampleNamed(num1: 10, num2: 20);
  exampleNamed(num2: 30); // num1 defaults to null
}
```

---
### **Java: Named Parameters (Using a Class)**
```java
class Parameters {
    int num1;
    int num2;

    public Parameters(int num1, int num2) {
        this.num1 = num1;
        this.num2 = num2;
    }
}

public class Main {
    static void exampleNamed(Parameters params) {
        System.out.println("First number: " + params.num1);
        System.out.println("Second number: " + params.num2);
    }

    public static void main(String[] args) {
        exampleNamed(new Parameters(10, 20));
    }
}
```

---
### **Python: Named Parameters**
```python
def example_named(num1=0, num2=0):
    print(f"First number: {num1}")
    print(f"Second number: {num2}")

example_named(num2=30, num1=10) 
example_named(num2=40)  # num1 defaults to 0
```
**🖥️ Output:**
```
First number: 10
Second number: 30

First number: 0
Second number: 40
```

---
### **Python: `*args` and `**kwargs`**
```python
def example_args(*args):
    print(args)  # args is a tuple

def example_kwargs(**kwargs):
    print(kwargs)  # kwargs is a dictionary

example_args(1, 2, 3, 4, 5)
example_kwargs(name="Dokja", age=25, country="Korea")
```
**🖥️ Output:**
```
(1, 2, 3, 4, 5)
{'name': 'Dokja', 'age': 25, 'country': 'Korea'}
```

---
## **📌 Conclusion**
| Feature | Dart | Java | Python |
|---------|------|------|--------|
| **Positional** | `(num1, num2)` | `example(int num1, int num2)` | `def example(num1, num2)` |
| **Named** | `{num1, num2}` | Not directly supported | `def example(num1=0, num2=0)` |
| **Flexible Args** | No `*args`, only List | Uses **Varargs (`...args`)** | `*args` and `**kwargs` |
| **Default Values** | Uses `=` in Named Parameters | Uses **Overloading** | Uses `=` |

🚀 **Python is the most flexible, Dart is simple, Java is strict!**

---

