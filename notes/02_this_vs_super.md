# 📌 `this` vs `super` in Dart and Java

## **🛠️ Purpose**
Understanding how `this` and `super` work in Dart and Java, including their syntax, differences, and real-world use cases. 🚀

---
## **📖 Theoretical Explanation**
### **1️⃣ `this` Keyword**
📌 **Definition**: `this` refers to the current instance of a class and is useful for distinguishing instance variables from parameters or calling instance methods inside the same class.
- ✅ Helps resolve naming conflicts.
- ✅ Can be used in constructors.
- ✅ Used to call another constructor (in some languages).

### **2️⃣ `super` Keyword**
📌 **Definition**: `super` refers to the superclass (parent class) and is used to:
- ✅ Call a superclass constructor.
- ✅ Access superclass methods.
- ✅ Ensure proper inheritance behavior.

---
## **📌 Code Examples & Outputs**

### **Dart: `this` Keyword**
```dart
class Person {
  String name;

  // Constructor using `this`
  Person(this.name);

  void showName() {
    print("Name: \$name");
  }
}

void main() {
  var p = Person("Dokja");
  p.showName();
}
```
**🖥️ Output:**
```
Name: Dokja
```

---
### **Java: `this` Keyword**
```java
class Person {
    String name;

    // Constructor using `this`
    Person(String name) {
        this.name = name;
    }

    void showName() {
        System.out.println("Name: " + name);
    }
    
    public static void main(String[] args) {
        Person p = new Person("Dokja");
        p.showName();
    }
}
```
**🖥️ Output:**
```
Name: Dokja
```

---
### **Dart: `super` Keyword**
```dart
class Animal {
  String species;

  Animal(this.species);

  void makeSound() {
    print("\$species makes a sound!");
  }
}

class Dog extends Animal {
  Dog(String species) : super(species);

  void makeSound() {
    super.makeSound(); // Calls parent method
    print("\$species barks!");
  }
}

void main() {
  var dog = Dog("Dog");
  dog.makeSound();
}
```
**🖥️ Output:**
```
Dog makes a sound!
Dog barks!
```

---
### **Java: `super` Keyword**
```java
class Animal {
    String species;

    Animal(String species) {
        this.species = species;
    }

    void makeSound() {
        System.out.println(species + " makes a sound!");
    }
}

class Dog extends Animal {
    Dog(String species) {
        super(species); // Calls parent constructor
    }

    void makeSound() {
        super.makeSound(); // Calls parent method
        System.out.println(species + " barks!");
    }

    public static void main(String[] args) {
        Dog dog = new Dog("Dog");
        dog.makeSound();
    }
}
```
**🖥️ Output:**
```
Dog makes a sound!
Dog barks!
```

---
## **📌 Conclusion**
| Feature | Dart | Java |
|---------|------|------|
| **`this`** | Used directly in constructors (`Person(this.name);`) | Requires explicit assignment (`this.name = name;`) |
| **`super`** | Called using `: super(param);` | Called using `super(param);` |
| **Method Overriding** | Uses `super.methodName();` | Uses `super.methodName();` |

🚀 **Dart is more concise, while Java is more explicit!**

---

