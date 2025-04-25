# lab7.3
import 'package:flutter/material.dart';

void main() {
  runApp(MyDatabaseApp());
}

class MyDatabaseApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DatabaseScreen(),
    );
  }
}

class DatabaseScreen extends StatefulWidget {
  @override
  _DatabaseScreenState createState() => _DatabaseScreenState();
}

class _DatabaseScreenState extends State<DatabaseScreen> {
  List<String> data = [];
  bool isLoading = true;

  Future<void> fetchData() async {
    await Future.delayed(Duration(seconds: 3)); // Simulated delay
    setState(() {
      data = ['Apple', 'Banana', 'Cherry', 'Date', 'Elderberry'];
      isLoading = false;
    });
  }

  @override
  void initState() {
    super.initState();
    fetchData();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Simulated DB Query")),
      body: isLoading
          ? Center(child: CircularProgressIndicator())
          : ListView.builder(
              itemCount: data.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(data[index]),
                );
              },
            ),
    );
  }
}
