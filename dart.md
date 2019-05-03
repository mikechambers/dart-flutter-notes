# Dart


## Data Structures

### Lists

Lists are mutable Arrays

```dart
var list = [1, 2, 3];

var l2 = List();
l2.add(1);
l2.add(2);

print(l2.length);

print(list[0]);
```

Two main ways to loop through a list:

```dart
for(var i = 0; i < l2.length; i++){
  print(l2[i]);
}

for(final value in l2) {
  print(value);
}
```

### Maps

Maps are Dictionaries of name / value pairs

```dart
var foo = {
  "a":1,
  "b":2,
  "c":3
};

var foo2 = Map();
foo2["a"] = 1;
foo2["b"] = 2;
foo2["c"] = 3;

print(foo2["a"]);
```

Keys and Values can be any type of object and they can be mixed.

```dart
var foo3 = Map();
foo3["a"] = 1;
foo3[1] = "a";
```
To iterate through a Maps keys / values, use 'Map.forEach':

```dart
foo2.forEach((key, value) {
  print("$key = $value");
});
```
