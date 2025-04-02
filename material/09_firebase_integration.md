# Firebase Integration in Flutter 🔥

## Introduction
Firebase is a **powerful backend solution** for Flutter apps. It provides authentication, real-time database, cloud storage, and more.

In this guide, we’ll cover:

- **Setting up Firebase** ⚙️
- **Authentication (Sign-in, Sign-up, Sign-out)** 🔐
- **Firestore (Storing and fetching data)** 📂
- **Firebase Storage (Uploading files)** 📦

---

## 1. Setting up Firebase ⚙️
### Steps:
1. Go to **[Firebase Console](https://console.firebase.google.com/)**.
2. Create a new Firebase project.
3. Add an **Android** or **iOS** app.
4. Download `google-services.json` (for Android) or `GoogleService-Info.plist` (for iOS) and place it in your Flutter project.
5. Add Firebase dependencies in `pubspec.yaml`:
   ```yaml
   dependencies:
     firebase_core: ^2.15.0
     firebase_auth: ^4.6.0
     cloud_firestore: ^4.8.3
     firebase_storage: ^11.2.4
   ```
6. Initialize Firebase in `main.dart`:
   ```dart
   import 'package:firebase_core/firebase_core.dart';
   import 'package:flutter/material.dart';

   void main() async {
     WidgetsFlutterBinding.ensureInitialized();
     await Firebase.initializeApp();
     runApp(MyApp());
   }
   ```

---

## 2. Firebase Authentication 🔐
### Purpose:
Authenticate users using **email & password**.

### Sign-Up:
```dart
import 'package:firebase_auth/firebase_auth.dart';

Future<void> signUp(String email, String password) async {
  try {
    await FirebaseAuth.instance.createUserWithEmailAndPassword(
      email: email,
      password: password,
    );
    print("User registered successfully!");
  } catch (e) {
    print("Error: $e");
  }
}
```

### Sign-In:
```dart
Future<void> signIn(String email, String password) async {
  try {
    await FirebaseAuth.instance.signInWithEmailAndPassword(
      email: email,
      password: password,
    );
    print("User signed in successfully!");
  } catch (e) {
    print("Error: $e");
  }
}
```

### Sign-Out:
```dart
Future<void> signOut() async {
  await FirebaseAuth.instance.signOut();
  print("User signed out");
}
```

---

## 3. Firestore Database 📂
### Purpose:
Store structured data in **Cloud Firestore**.

### Adding Data:
```dart
import 'package:cloud_firestore/cloud_firestore.dart';

Future<void> addUser(String name, int age) async {
  await FirebaseFirestore.instance.collection('users').add({
    'name': name,
    'age': age,
  });
}
```

### Fetching Data:
```dart
Future<void> fetchUsers() async {
  QuerySnapshot snapshot = await FirebaseFirestore.instance.collection('users').get();
  for (var doc in snapshot.docs) {
    print("User: ${doc['name']}, Age: ${doc['age']}");
  }
}
```

### Real-Time Listener:
```dart
void listenToUsers() {
  FirebaseFirestore.instance.collection('users').snapshots().listen((snapshot) {
    for (var doc in snapshot.docs) {
      print("Updated User: ${doc['name']}");
    }
  });
}
```

---

## 4. Firebase Storage 📦
### Purpose:
Upload and retrieve files (e.g., images, PDFs).

### Uploading a File:
```dart
import 'package:firebase_storage/firebase_storage.dart';
import 'dart:io';

Future<void> uploadFile(File file) async {
  try {
    Reference storageRef = FirebaseStorage.instance.ref().child("uploads/${file.path.split("/").last}");
    await storageRef.putFile(file);
    print("File uploaded successfully!");
  } catch (e) {
    print("Error: $e");
  }
}
```

### Downloading a File URL:
```dart
Future<String> getFileUrl(String fileName) async {
  Reference storageRef = FirebaseStorage.instance.ref().child("uploads/$fileName");
  String url = await storageRef.getDownloadURL();
  return url;
}
```

---

## Summary 📌
| Feature | Description |
|---------|-------------|
| **Authentication** 🔐 | User login, registration, and logout using Firebase Auth |
| **Firestore** 📂 | Store and fetch structured data in Firestore |
| **Storage** 📦 | Upload and retrieve files in Firebase Storage |

---

🚀 Now you can integrate Firebase into your Flutter apps! Happy coding! 🎉

