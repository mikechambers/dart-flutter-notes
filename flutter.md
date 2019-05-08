# Flutter

## Widgets

### App Boilerplate

```dart
import 'package:flutter/material.dart';
import "package:flutter/rendering.dart";

void main() {
  debugPaintSizeEnabled=false;
  runApp(MyApp());
}

class MyApp extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return MyAppState();
  }
}

class MyAppState extends State<MyApp> {
  @override
  void initState(){
    return;
  }

  @override
  Widget build(BuildContext content) {

    return MaterialApp(
      title:"Hello World!",
      home:Scaffold(
        appBar: appBar,
        body:Text("Hello World"),
      ),
    );
  }

  final AppBar appBar = AppBar(
    title: Text("Destiny 2 Status"),
  );

}
```

### Stateless Widgets

```dart
import 'package:flutter/material.dart';
import "package:flutter/rendering.dart";

void main() {
  debugPaintSizeEnabled = true;
  runApp(MyApp());
}
```

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Welcome to Flutter',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

### Stateful Widgets

```dart
class MyApp extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return _MyAppState();
  }
}

class _MyAppState extends State<MyApp> {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Welcome to Flutter',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

This is an example of implementing state for a DropdownButton component:

```dart
class _PlatformSelect extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return _PlatformSelectState();
  }
}

class _PlatformSelectState extends State<_PlatformSelect> {
  String dropdownValue = "Xbox";

  @override
  Widget build(BuildContext context) {
    return DropdownButton<String>(
        value:dropdownValue,
        onChanged: (String newValue) {
          setState(() {
            dropdownValue = newValue;
          });
        },
        items: <String>["Xbox", "PlayStation", "PC"].map<DropdownMenuItem<String>>((String value) {
          return DropdownMenuItem<String>(
            value: value,
            child: Text(value),
          );
        }).toList(),
      );
  }
}
```

## Layout Elements

*  Container : Customizes child widget. Use when you want to add padding, margins, borders or a background color.
*  Row : Lays out widgets horizontally.
*  Column : Lays out child widgets vertically.
*  Expanded
*  Center : Centers content horizontally and vertically
*  ListView : Lays widgets out as a scrollable list.
*  Stack
*  Card : Material widget that organizes related info into a box with rounded corners and a drop shadow.
*  ListTile : Material widget that organizes up to 3 lines of text and optional leading and trailing icons, into a row.

List of (all layout widgets)[https://flutter.dev/docs/development/ui/widgets/layout]

All layout widgets have either a `child` or `children` property.

### Row & Column

Used to layout children verticals or horizontally. Can specify alignment, and set to stretch of contain child widgets.

*mainAxisAlignment* / *crossAxisAlignment* : controls alignment for children, including things like spacing.

By default, a row or column occupies as much space along its main axis as possible. You can change this with 'mainAxisSize = MainAxisSize.min'.

### Container

Used to add padding, border, margins or background color to child widgets, r created rounded corners on backgrounds.

#### Take up all space, and dont collapse

```
constraints:BoxConstraint.expand()
```

### Expanded

Expands a child of a Row, Column or Flex (expands to fill available space on the main axis).

### GridView

Lays out widgets as a two dimensional list. Provides two-prefabricated lists, or you can build your own. If contents are too long to fit the render box, it will automatically scroll.

### ListView

 Column like widget that automatically scrolls when its content is too long for its render box.

 ### Stack

 Widget that allows you to overlay one widget on top of another.

## Tips & Tricks

### Scrolling textfield

```dart
Column(
  mainAxisSize: MainAxisSize.max,
  children: <Widget>[
    Expanded(
      child:Container(
        constraints: BoxConstraints.expand(),
        decoration: BoxDecoration(
          color: Colors.green,
        ),
        child:SingleChildScrollView(
          child:Text(out),
        ),
      )
    ),
  ],
),
```

### Expand and Position Containers

This positions a container anchored on the bottom, with the top container taking all avaliable space:

```dart
Column(
  mainAxisSize: MainAxisSize.max,
  children: <Widget>[
    Expanded(
      child: Container(
        child:Text("Foo2"),
        constraints: BoxConstraints.expand(),
        decoration: BoxDecoration(
          color:Colors.lightGreen,
        ),
      ),
    ),
 Container(
        child:Text("Foo2"),
        height: 100,
        alignment: Alignment.topLeft,

        decoration: BoxDecoration(
          color:Colors.lightBlue,
        ),
      ),

  ],
),
```

### Maintaining layout readability

For deeply nested UIs, break out and define individual sections into their own variables.

```dart
var stars = Row(
  mainAxisSize: MainAxisSize.min,
  children: [
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.black),
    Icon(Icons.star, color: Colors.black),
  ],
);

final ratings = Container(
  padding: EdgeInsets.all(20),
  child: Row(
    mainAxisAlignment: MainAxisAlignment.spaceEvenly,
    children: [
      stars,
      Text(
        '170 Reviews',
        style: TextStyle(
          color: Colors.black,
          fontWeight: FontWeight.w800,
          fontFamily: 'Roboto',
          letterSpacing: 0.5,
          fontSize: 20,
        ),
      ),
    ],
  ),
);
```

### Visual Debugging

To enabled visual debugging, which will display bonding boxes for Widgets, add the following to your flutter app:

```dart
//add import to rendering library
import 'package:flutter/rendering.dart';

void main() {
  debugPaintSizeEnabled=true;
  runApp(MyApp());
}
```
