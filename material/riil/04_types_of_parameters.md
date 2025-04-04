# 🧠 Types of Parameters in Dart: Positional vs Named Arguments

> "Clear parameters lead to clear code. Dart gives you flexibility — but with great power comes great responsibility."
> — Professor Jip 😎

---

## 🎯 Objective

Understand the difference between **positional** and **named** parameters in Dart, how to make parameters optional or required, and how to assign default values.

---

## 📚 Theoretical Explanation

### 🔹 1. Positional Parameters

These parameters are defined **by their position**. The order in which arguments are passed determines which parameter receives the value.

```dart
void add(a, b) {
  print(a + b);
}

add(5, 10); // Output: 15
```

🧩 `a` receives 5 (first argument), `b` receives 10 (second argument).

By default, positional parameters are **required**. If not provided, an error will occur.

---

### 🔸 2. Named Parameters

Named parameters are enclosed in **curly braces `{}`** and are called by specifying the parameter name.

```dart
void add({a, b}) {
  print(a + b);
}

add(b: 5, a: 10); // Output: 15
```

📍 Order does not matter — Dart matches the values based on the **name**.

By default, named parameters are **optional**. You can call a function without providing all the parameters:

```dart
add();        // a and b will be null
add(a: 7);    // b is still null
```

---

## 🔄 Optional Parameters

### 🔸 Optional Positional

Make a positional parameter optional by wrapping it in **`[]` (square brackets)**:

```dart
void add(a, [b]) {
  print(a + b);
}
```

You can also provide a **default value**:

```dart
void add(a, [b = 5]) {
  print(a + b);
}

add(10);    // Output: 15 (because b defaults to 5)
add(10, 6); // Output: 16
```

### 🔸 Optional Named

Named parameters are **optional by default**, but you can also assign **default values**:

```dart
void add({a, b = 5}) {
  print(a + b);
}

add(b: 10); // a is null, b is 10 => error because null + 10
```

To make named parameters required, use the `required` keyword:

```dart
void add({required a, required b}) {
  print(a + b);
}

add(a: 3, b: 7); // Output: 10
```

---

## 💡 Conclusion

| Parameter Type        | Key Characteristic          | Default   | Can Have Default? | Can Be Required? |
|-----------------------|-----------------------------|-----------|-------------------|------------------|
| Positional            | Based on order              | Required  | ✅ Yes            | ✅ (default)     |
| Optional Positional   | Wrapped in `[]`             | Optional  | ✅ Yes            | ❌ No            |
| Named                 | Wrapped in `{}`             | Optional  | ✅ Yes            | ✅ with `required` |

Dart gives you high flexibility in designing functions. But it's important to understand when and how to use each type to write **clear**, **reusable**, and **safe** code.

---

> 🧵 *"Understand parameters, understand your purpose within a function."* — Dokja 2025

