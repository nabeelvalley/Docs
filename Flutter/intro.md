> Notes from the [The Net Ninja Youtube Series](https://www.youtube.com/watch?v=1ukSR1GRtMU&list=PL4cUxeGkcC9jLYyp2Aoh6hcWuxFDX6PBJ)

# What is it

Flutter is a way to build native, cross-platoform applications using the `dart` language

- Easy to build respoonsive applications
- Smooth and responsive applications
- Material design and iOS Cupertino pre-implemented

# Install Flutter

[Documentation](https://flutter.dev/docs/get-started/install/windows?gclid=Cj0KCQjwzN71BRCOARIsAF8pjfhZOA-znjAzldU6xu_LNnlgYa6Cio_Jb17P8Uuq4UcKCQlk0ycePb0aAqLoEALw_wcB&gclsrc=aw.ds)

To install Flutter you need to:

- Download the [Flutter SDK](https://flutter.dev/docs/get-started/install)
- Extract into your 'C:\flutter' directory. Any directory that does not require elevated permissions should work
- Add the `flutter\bin` directory to your System `PATH` (possibly also User Path, I had some issues with the VSCode Extension so maybe both?)
- Close and reopen any Powershell Windows

You should then be able to run the `flutter doctor` command to verify the installation, you may see something like this:

```
[√] Flutter (Channel stable, v1.17.0, on Microsoft Windows [Version 10.0.18363.778], locale en-US)
[X] Android toolchain - develop for Android devices
    X Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/docs/get-started/install/windows#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, set ANDROID_SDK_ROOT to that location.
      You may also want to add it to your PATH environment variable.

[!] Android Studio (not installed)
[!] VS Code (version 1.45.0)
    X Flutter extension not installed; install from
      https://marketplace.visualstudio.com/items?itemName=Dart-Code.flutter
[!] Connected device
    ! No devices available
```

You can address any of the issus that flutter identified during the previous

# Dart Overview

To get started with Dart you can use [DartPad](https://dartpad.dev/)

## Hello World

A simple Hello World in dart looks like so:

```dart
void main() {
  print("Hello World");
}
```

In Dart we require semicolons and the entrypoint is the `main` function

## Variables

We declare variables like this:

```dart
int age = 5;
print(age);
```

Some data types are:

- `int`
- `String` which can use a `'` or a `"`
- `bool`
- `dynamic`

We can also define variables as `dynamic` which means that their type can be changed

String interpolation can also be done like so:

```dart
int age = 5;
String name = "John";
String person = "My name is $name and I am $age years old";
```

## Functions

Functions make use of the following structure:

```dart
MyType fName() {
  ...//do stuff

  return thing; //type of MyType
}
```

If a function has a single line we can also make use of an arrow function which looks like this:

```dart
MyType getThing() => thing;
```

A function with inputs is defined and used like so:

```dart
int add(int x, int y) => x + y;
```

And used as you'd expect:

```dart
int result = add(1,3);
```

Functions can also take in optional params, there are two methods for this, named and unnamed params:

```dart
// unnamed
int sumUN(int a, int b, [int c, int d]) => ....

//named
int sumN(int a, int b, {int c, int d}) => ...
```

The way we call these functions differ

````dart
// unnamed
sumUN(1,2)
sumUN(1,2,3)
sumUN(1,2,3,4)

//named
sumN(1,2)
sumN(1,2, {c: 3})
sumN(1,2, {c: 3, d: 4})
```

## Lists

Lists in Dart are defined using the `[]` notation

```dart
List names = ['john', 'jeff', 'johnny'];
````

We can also use list methods to work with the list

```dart
names.add('sally');
names.add(12); // not a string

names.remove('john');
```

The list as defined above does not have a defined type, usually we want to specify the allowable types (coz obviously). We can set the type using the `<T>` notation like so:

```dart
List<String> names = ['john', 'jeff', 'johnny'];
```

## Classes

Classes are defined using the `class` keyword, with the properties defined within the class. The `new` keyword is not needed

```dart
void main() {
  Person john = Person("John", 3);
  john.greet();

  john.setAge(5);

  print(john.getAge());
}

class Person {
  String name; // public by default
  int _age; // private if starts with _

  Person(String name, int age){
    this.name = name;
    this._age = age;
  }

  void greet() =>
    print("Hello, I am " + name);

  void setAge(int newAge) {
    this._age = newAge;
  }


  int getAge() => this._age;
}
```

> Private properties start with `_` and cannot be accessed from outside the class

We can also initialize class variables like this:

```dart
class Person {
  String name = "Person";
  int _age = 1;
  ...
}
```

We can use inheritance using the `extends` keyword:

```dart
class NotCat {
  bool isCat = false;
  String description = "Not a Kitty";

  NotCat(bool isCat){
    // we don't care
  }
}

class Person extends NotCat {
  String name; // public by default
  int _age; // private if starts with _

  Person(String name, int age): super(false){
    this.name = name;
    this._age = age;
  }
}
```

When using the above we need to be sure to also call the constructor of the base class from the inheriting class using `super`

## Const and Final

A `const` variable is one that's value is constant at compile time, a `final` variable is one that is only assigned to once

In dart we can also define constants using the `const` and `final` keywords like so:

```dart
const int age = 12;
final String name= "John";
final Person myPerson = Person(name, age);
```

You can also create constant instances of objects but that requres a `const` constructor

# Setting Things Up

## General Setup

> Install the Flutter SDK as described above

1. You will need to install Android Studio (so that you have an android debugger)
2. Once installed, on the Android Studio start screen (bottom right) click on `configure > AVD Manager > Create Virtual Device` and then download the `Pie` system image and once that's done select it
3. Set a name for your virtual device (you can leave this as is)
4. Click Finish and the virtual device will be created

## Android Studio

Next, if using Android Studio as the editor install the following plugins:

1. `configure > Plugins > Marketplace` and search for `Flutter`
2. Install the `Flutter` plugin and ask if it should install the `Dart` plugin as well
3. Restart Android Studio, you should now have a `Start a new Flutter project` option on the start menu

## VSCode

Install the Flutter Extension (that should be it)