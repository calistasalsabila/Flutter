## 🎯 Purpose
To understand how `var` behaves in Dart compared to Java and Python, especially in object instantiation and type handling. This helps clarify Dart's type system and how it mixes the styles of Java and Python.

---

## 🧠 Theory Explanation
### What is `var` in Dart?
- `var` in Dart means *"let Dart infer the type of this variable from the assigned value"*.
- Once a type is inferred, it's fixed. You **can't change the type later**.

This differs from:
- **Java**: Strongly typed. `var` (since Java 10) infers type but still behaves like a fixed typed variable.
- **Python**: Dynamically typed. No `var` keyword; variables can change type at runtime.

---

## 🧪 Code Examples and Output

### ✅ Dart Example
```dart
class Person {
  String name;
  Person(this.name);
}

class Animal {
  String species;
  Animal(this.species);
}

void main() {
  var p = Person("Dokja");
  print(p.name); // Output: Dokja

  p.name = "Hamin"; // Changing internal state ✅
  print(p.name); // Output: Hamin

  p = Person("Jeha"); // Reassigning same type ✅
  print(p.name); // Output: Jeha

  // p = Animal("Dog"); // ❌ ERROR: type mismatch

  dynamic d = Person("Dazai"); // ✅ OK with dynamic
  d = Animal("Wolf"); // ✅ Also works
}
```

### ✅ Java Equivalent
```java
public class Main {
    public static void main(String[] args) {
        Person p = new Person("Dokja");
        System.out.println(p.name);

        p.name = "Hamin";
        System.out.println(p.name);

        p = new Person("Jeha");
        System.out.println(p.name);

        // p = new Animal("Dog"); // ❌ Compilation error
    }
}
```

### ✅ Python Equivalent
```python
class Person:
    def __init__(self, name):
        self.name = name

class Animal:
    def __init__(self, species):
        self.species = species

p = Person("Dokja")
print(p.name)

p.name = "Hamin"
print(p.name)

p = Person("Jeha")
print(p.name)

p = Animal("Dog")  # ✅ OK in Python
print(p.species)
```

---

## 💬 Conclusion
- Dart uses `var` to infer types, like Python, **but behaves like Java** in type strictness.
- You can reassign objects of the **same class** to a `var`, but not different classes.
- If you want flexibility like Python, use `dynamic` or `Object`, but beware of losing type safety.

⚠️ When working with multiple classes in Dart, always consider whether you need strict typing (`var`) or flexibility (`dynamic`).

> Dart is like Java in a Python suit — chill syntax, strict rules. 😎

