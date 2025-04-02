# API & Networking 🌐

## Introduction
Fetching data from a REST API is essential for most mobile applications. In Flutter, we can use **`http`** package to handle network requests. In this section, we will cover:

- **Installing `http` package** 📦
- **Making GET requests** 🔍
- **Handling JSON responses** 🗄️
- **Displaying API data in a ListView** 📃
- **Making POST requests** 📝

Let’s get started! 🚀

---

## 1. Installing `http` Package 📦
Before making API requests, add the `http` dependency to your `pubspec.yaml` file:
```yaml
dependencies:
  http: ^0.13.5
```
Then, run:
```sh
flutter pub get
```

---

## 2. Making a GET Request 🔍
### Purpose:
Fetch data from an API and display it.

### Example API:
We will use **JSONPlaceholder** (a free fake API) to get a list of users:
```url
https://jsonplaceholder.typicode.com/users
```

### Implementation:
```dart
import 'package:flutter/material.dart';
import 'package:http/http.dart' as http;
import 'dart:convert';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: UserListScreen(),
    );
  }
}

class UserListScreen extends StatefulWidget {
  @override
  _UserListScreenState createState() => _UserListScreenState();
}

class _UserListScreenState extends State<UserListScreen> {
  List users = [];
  bool isLoading = true;

  @override
  void initState() {
    super.initState();
    fetchUsers();
  }

  Future<void> fetchUsers() async {
    final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/users'));
    if (response.statusCode == 200) {
      setState(() {
        users = json.decode(response.body);
        isLoading = false;
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("User List")),
      body: isLoading
          ? Center(child: CircularProgressIndicator())
          : ListView.builder(
              itemCount: users.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(users[index]['name']),
                  subtitle: Text(users[index]['email']),
                );
              },
            ),
    );
  }
}
```

### Output:
- Fetches a list of users from the API and displays their names and emails.
- Shows a **loading spinner** until the data is loaded.

### Explanation:
- `http.get()` fetches data from the API.
- `json.decode(response.body)` converts JSON to a Dart list.
- `setState()` updates the UI when data is available.

---

## 3. Making a POST Request 📝
### Purpose:
Send data to an API (e.g., creating a new user).

### Example API:
```url
https://jsonplaceholder.typicode.com/posts
```

### Implementation:
```dart
Future<void> createPost() async {
  final response = await http.post(
    Uri.parse('https://jsonplaceholder.typicode.com/posts'),
    body: json.encode({
      "title": "Flutter API",
      "body": "Learning API in Flutter",
      "userId": 1
    }),
    headers: {"Content-Type": "application/json"},
  );

  if (response.statusCode == 201) {
    print("Post created: ${response.body}");
  } else {
    print("Failed to create post");
  }
}
```

### Output:
- Sends a **new post** to the API.
- Prints **response data** if successful.

### Explanation:
- `http.post()` sends data.
- `json.encode()` converts Dart map to JSON.
- `headers` ensure the correct content type.

---

## Summary 📌
| API Operation | Method | Description |
|--------------|--------|-------------|
| Fetch Data | `GET` | Retrieve data from an API. |
| Send Data | `POST` | Send new data to an API. |
| Update Data | `PUT` | Modify existing data. |
| Delete Data | `DELETE` | Remove data from an API. |

---

🚀 Now you know how to fetch data from an API! Happy coding! 🎉