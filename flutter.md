# Flutter

## Layout Elements

*  Container : Customizes child widget. Use when you want to add padding, margins, borders or a background color.
*  Row : Lays out widgets horizontally.
*  Column : Lays out child widgets vertically.
*  Expanded
*  Center : Centers content horizontally and vertically
*  ListView
*  Stack

List of (all layout widgets)[https://flutter.dev/docs/development/ui/widgets/layout]

All layout widgets have either a `child` or `children` property.

### Row & Column

Used to layout children verticals or horizontally. Can specify alignment, and set to stretch of contain child widgets.

*mainAxisAlignment* / *crossAxisAlignment* : controls alignment for children, including things like spacing.

By default, a row or column occupies as much space along its main axis as possible. You can change this with 'mainAxisSize = MainAxisSize.min'.

### Expanded

Expands a child of a Row, Column or Flex (expands to fill available space on the main axis).

## Tips & Tricks

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
