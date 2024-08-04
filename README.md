# Learn PHP

I use this repo to track all the lessons I learned about python

## Reference documents

* https://www.w3schools.com/php/default.asp

## Online playground tools

* https://php-play.dev/?c=DwfgDgFmBQD0sAICmAPAhgWzAGyQgxgPYAmS0kYAlgHYBmhAFAJQDcQA&v=8.3&f=html

## Main content

### Syntax

```php
<?php
// PHP code goes here
?>
```

### Comments

```php
// This is a single-line comment

# This is also a single-line comment

/* This is a
multi-line comment */
```

### Variables

Variables are "containers" for storing information

#### Creating (Declaring) Variables

In PHP, a variable starts with the $ sign, followed by the name of the variable

```php
$name = "JiRim";
$age = 24;
```

#### Output Variables

The PHP echo statement is often used to output data to the screen

```php
$name = "PHP";
echo "I love $name!"; // I love PHP
echo "I love " . $txt . "!"; // I love PHP
```

The following example will output the sum of two variables:

```php
$x = 5;
$y = 4;
echo $x + $y; // OUTPUT: 9
```

PHP supports the following data types:

String

* Integer
* Float (floating point numbers - also called double)
* Boolean
* Array
* Object
* NULL
* Resource

#### Get the Type

The var_dump() function returns the data type and the value

```php
var_dump(5); // int(5)
var_dump("John"); // string(4)
var_dump(3.14); // float(3.14)
var_dump(true); // bool(true)
var_dump([2, 3, 56]); // array(3) {[0]=> int(2) [1]=> int(3) [2]=> int(56) }
var_dump(NULL); // NULL
```

### Variables Scope

PHP has three different variable scopes:

* Local
* Global
* Static

#### Global and Local Scope

#### A variable declared outside a function has a GLOBAL SCOPE and can only be accessed outside a function

```php
$name = JiRim; // Global Scope

function myTest() {
  // using $name inside this function will generate an error
  echo "<p>My name is: $name</p>";
}
myTest(); // My name is:

echo "<p>My name is: $name</p>"; // My name is: JiRim
```

#### A variable declared within a function has a LOCAL SCOPE and can only be accessed within that function

```php
function myTest() {
  $name = JiRim; // Local Scope
  echo "<p>My name is: $name</p>";
}
myTest(); // My name is: JiRim

// using $name outside the function will generate an error
echo "<p>>My name is: $name</p>"; // My name is:
```

#### The global Keyword

The global keyword is used to access a global variable from within a function.

To do this, use the global keyword before the variables (inside the function):

```php
$x = 5;
$y = 10;

function plus() {
  global $x, $y;
  $y = $x + $y;
}

plus();
echo $y; // OUTPUT: 15
```

PHP also stores all global variables in an array called $GLOBALS[index]. The index holds the name of the variable.

This array is also accessible from within functions and can be used to update global variables directly


```php
$x = 5;
$y = 10;

function calPlus() {
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
}

calPlus();
echo $y; // OUTPUT: 15
```

#### The static Keyword

Normally, when a function is completed/executed, all of its variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.

```php
function myTest() {
  static $x = 0;
  echo $x;
  $x++;
}

myTest(); // 0
myTest(); // 1
myTest(); // 2
```