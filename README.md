# Learn PHP

I use this repo to track all the lessons I learned about php

## Reference documents

* https://www.php.net/manual/en/

* https://www.w3schools.com/php/default.asp

* https://www.vietjack.com/php/index.jsp

* https://freetuts.net/hoc-php

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

### Echo Statement

The echo statement can be used with or without parentheses: echo or echo()

```php
echo "Hello";
// Same as:
echo("Hello");
```

#### Display Text

The following example shows how to output text with the echo command (notice that the text can contain HTML markup)

```php
echo "Hello, JiRim<br>";
echo "This ", "string ", "was ", "made ", "with multiple parameters.";
```

#### Display Variables & Using Single Quotes

The following example shows how to output text and variables with the echo statement

```php
$txt1 = "I'm learning PHP";
$txt2 = "JiRim";

echo "<h1>$txt1</h1>";
echo "<p>Hello, $txt2</p>";

// Same as:
echo '<h1>' . $txt1 . '</h1>';
echo '<p>Hello, ' . $txt2 . '</p>';
```

### Print Statement

The print statement can be used with or without parentheses: print or print()

```php
print "Hello";
// Same as:
print("Hello");
```

#### Display Text

The following example shows how to output text and variables with the echo statement

```php
print "Hello, JiRim<br>";
print "This ", "string ", "was ", "made ", "with multiple parameters.";
```

#### Display Variables & Using Single Quotes

The following example shows how to output text and variables with the echo statement

```php
$txt1 = "I'm learning PHP";
$txt2 = "JiRim";

print "<h1>$txt1</h1>";
print "<p>Hello, $txt2</p>";

// Same as:
print '<h1>' . $txt1 . '</h1>';
print '<p>Hello, ' . $txt2 . '</p>';
```

### Strings

A string is a sequence of characters, like "Hello, JiRim".

#### PHP Strings

Strings in PHP are surrounded by either double quotation marks, or single quotation marks:

```php
echo "Hello";
echo 'Hello';
```

#### Double or Single Quotes?

Double quoted string literals perform operations for special characters:

```php
$x = "JiRim";
echo "Hello $x"; // Hello JiRim
```

Single quoted string literals returns the string as it is:

```php
$x = "John";
echo 'Hello $x'; // Hello $x
```

#### String Length

Return the length of the string "Hello JiRim":

```php
echo strlen("Hello world!"); // 11
```

#### Word Count

The PHP str_word_count() function counts the number of words in a string.

```php
echo str_word_count("Hello JiRim"); // 2
```

#### Search For Text Within a String

The PHP strpos() function searches for a specific text within a string.

If a match is found, the function returns the character position of the first match. If no match is found, it will return FALSE.

```php
echo strpos("Hello Jirim", "Jirim"); // 6th character
echo strpos("Hello Jirim", "jirim"); // False because there are no characters in the string
```

#### Upper Case

The strtoupper() function returns the string in upper case:

```php
$x = "Hello JiRim";
echo strtoupper($x); // HELLO JIRIM
```

#### Lower Case

The strtolower() function returns the string in lower case:

```php
$x = "Hello JiRim";
echo strtolower($x); // hello jirim
```

#### Replace String

The PHP str_replace() function replaces some characters with some other characters in a string.

```php
// Replace the text "JiRim" with "World"
$x = "Hello JiRim";
echo str_replace("JiRim", "World", $x); // Hello World
```

#### Reverse a String

The PHP strrev() function reverses a string

```php
$x = "Hello JiRim";
echo strrev($x); // miRiJ olleH
```

#### Remove Whitespace

Whitespace is the space before and/or after the actual text, and very often you want to remove this space.

```php
// The trim() removes any whitespace from the beginning or the end
$x = " Hello JiRim ";
echo trim($x); // Hello JiRim
```

#### Convert String into Array

The PHP explode() function splits a string into an array

```php
$text = "Hello JiRim";
$convert_text = explode(" ", $text);

// Use the print_r() function to display the result:
print_r($convert_text); // Array ( [0] => Hello [1] => JiRim )
```

#### String Concatenation

To concatenate, or combine, two strings you can use the . operator:

```php
$a = "Hello";
$b = "JiRim";

$c = $a . $b;
echo $c; // HelloJiRim
// Same as
$c = $a . " " . $b;
echo $c; // Hello JiRim
// Same as
$c = "$a $b"; // Hello JiRim
```

#### Slicing

You can return a range of characters by using the substr() function.

```php
$a = "Hello JiRim";
echo substr($a, 6, 5); // JiRim
```

##### Slice to the End

By leaving out the length parameter, the range will go to the end:

```php
$a = "JiRim is so handsome";
echo substr($a, 6); // is so handsome
```

##### Slice From the End

Use negative indexes to start the slice from the end of the string:

```php
$a = "Hello JiRim";
echo substr($a, -5, 3); // JiR
```

##### Negative Length

Use negative length to specify how many characters to omit, starting from the end of the string

```php
$a = "Hi, how are you?";
echo substr($a, 5, -3); // ow are y
```

#### Escape Character

To insert characters that are illegal in a string, use an escape character.

An escape character is a backslash \ followed by the character you want to insert.

An example of an illegal character is a double quote inside a string that is surrounded by double quotes:

```php
$a = "We are the so-called "Vikings" from the north.";
// Same as
$a = "We are the so-called \"Vikings\" from the north.";
```

### Numbers

There are three main numeric types in PHP:

* Integer

* Float

* Number Strings

In addition, PHP has two more data types used for numbers:

* Infinity

* NaN

```php
$a = 5; // int
$b = 5.34; // float
$c = "25"; // number string
```

#### Integers

Here are some rules for integers

* An integer must have at least one digit

* An integer must NOT have a decimal point

* An integer can be either positive or negative

* Integers can be specified in three formats: decimal (base 10), hexadecimal (base 16 - prefixed with 0x), octal (base 8 - prefixed with 0) or binary (base 2 - prefixed with 0b)

PHP has the following predefined constants for integers:

* PHP_INT_MAX - The largest integer supported

* PHP_INT_MIN - The smallest integer supported

* PHP_INT_SIZE -  The size of an integer in bytes

PHP has the following functions to check if the type of a variable is integer : 

* is_int()

* is_integer()

* is_long()

```php
// Check if the type of a variable is integer
$a = 1234;
var_dump(is_int($a)); // true

$a = 12.34;
var_dump(is_int($a)); // false
```

#### Floats

PHP has the following predefined constants for floats (from PHP 7.2):

* PHP_FLOAT_MAX - The largest representable floating point number

* PHP_FLOAT_MIN - The smallest representable positive floating point number

* PHP_FLOAT_DIG - The number of decimal digits that can be rounded into a float and back without precision loss

* PHP_FLOAT_EPSILON - The smallest representable positive number x, so that x + 1.0 != 1.0

PHP has the following functions to check if the type of a variable is float:

* is_float()

* is_double()

```php
$x = 10.365;
var_dump(is_float($x)); // true
```

#### Infinity

PHP has the following functions to check if a numeric value is finite or infinite:

* is_finite()

* is_infinite()

```php
// finite
$number1 = 1234.56; // số hữu hạn
$number2 = log(0); // -INF không phải là số hữu hạn

if (is_finite($number1)) {
    echo "$number1 là một số hữu hạn.\n";
} else {
    echo "$number1 không phải là một số hữu hạn.\n";
}

if (is_finite($number2)) {
    echo "$number2 là một số hữu hạn.\n";
} else {
    echo "$number2 không phải là một số hữu hạn.\n";
}

// infinite
$number1 = 1.0 / 0.0; // INF là số vô cực
$number2 = 1234.56; // không phải là số vô cực

if (is_infinite($number1)) {
    echo "$number1 là một số vô cực.\n";
} else {
    echo "$number1 không phải là một số vô cực.\n";
}

if (is_infinite($number2)) {
    echo "$number2 là một số vô cực.\n";
} else {
    echo "$number2 không phải là một số vô cực.\n";
}
```

#### NaN

NaN stands for Not a Number.

PHP has the following functions to check if a value is not a number:

* is_nan()

```php
$number1 = acos(1.01); // NaN, vì cos^-1 của giá trị lớn hơn 1 không tồn tại
$number2 = sqrt(-1); // NaN, vì không thể lấy căn bậc hai của số âm
$number3 = 1234.56; // một số thông thường

if (is_nan($number1)) {
    echo "number1 là NaN.\n";
} else {
    echo "number1 không phải là NaN.\n";
}

if (is_nan($number2)) {
    echo "number2 là NaN.\n";
} else {
    echo "number2 không phải là NaN.\n";
}

if (is_nan($number3)) {
    echo "number3 là NaN.\n";
} else {
    echo "number3 không phải là NaN.\n";
}
```

#### Numerical Strings

The PHP is_numeric() function can be used to find whether a variable is numeric. The function returns true if the variable is a number or a numeric string, false otherwise.

```php
$x = 5985;
var_dump(is_numeric($x)); // true

$x = "5985";
var_dump(is_numeric($x)); // true
$x = "59.85" + 100;
var_dump(is_numeric($x)); // true

$x = "Hello";
var_dump(is_numeric($x)); // false
```

#### Casting Strings and Floats to Integers

Sometimes you need to cast a numerical value into another data type.

The (int), (integer), and intval() functions are often used to convert a value to an integer.

```php
// Cast float to int
$x = 23465.768;
$int_cast = (int)$x;
echo $int_cast; // 23465

// Cast string to int
$x = "23465.768";
$int_cast = (int)$x; // 23465
echo $int_cast;
```

### Math

#### pi() Function

The pi() function returns the value of PI:

```php
echo(pi()); // 3.1415926535898
```

#### min() and max() Functions

The min() and max() functions can be used to find the lowest or highest value in a list of arguments:

```php
echo(min(0, 150, 30, 20, -8, -200)); // -200
echo(max(0, 150, 30, 20, -8, -200)); // 150
```

#### abs() Function

The abs() function returns the absolute (positive) value of a number:

```php
echo(abs(-6.7)); // 6.7
```

#### sqrt() Function

The sqrt() function returns the square root of a number:

```php
echo(sqrt(64)); // 8
echo(sqrt(0)); // 0
echo(sqrt(1)); // 1
echo(sqrt(9)); // 3
```

#### round() Function

The round() function rounds a floating-point number to its nearest integer:

```php
echo(round(0.60)); // 1
echo(round(0.50)); // 1
echo(round(0.49)); // 0
```

#### Random Numbers

The rand() function generates a random number:

```php
echo(rand());
echo(rand(10, 100));
```

### Casting

Change Data Type

Casting in PHP is done with these statements:

* (string) - Converts to data type String

* (int) - Converts to data type Integer

* (float) - Converts to data type Float

* (bool) - Converts to data type Boolean

* (array) - Converts to data type Array

* (object) - Converts to data type Object

* (unset) - Converts to data type NULL

#### Cast to String

To cast to string, use the (string) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "hello"; // String
$d = true;    // Boolean
$e = NULL;    // NULL

$a = (string) $a;
$b = (string) $b;
$c = (string) $c;
$d = (string) $d;
$e = (string) $e;

var_dump($a); // string(1) "5"
var_dump($b); // string(4) "5.34"
var_dump($c); // string(5) "hello"
var_dump($d); // string(1) "1"
var_dump($e); // string(0) ""
```

#### Cast to Integer

To cast to integer, use the (int) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "25 kilometers"; // String
$d = "kilometers 25"; // String
$e = "hello"; // String
$f = true;    // Boolean
$g = NULL;    // NULL

$a = (int) $a; // int(5)
$b = (int) $b; // int(5)
$c = (int) $c; // int(25)
$d = (int) $d; // int(0)
$e = (int) $e; // int(0)
$f = (int) $f; // int(1)
$g = (int) $g; // int(0)
```

#### Cast to Float

To cast to float, use the (float) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "25 kilometers"; // String
$d = "kilometers 25"; // String
$e = "hello"; // String
$f = true;    // Boolean
$g = NULL;    // NULL

$a = (float) $a; // float(5)
$b = (float) $b; // float(5.34)
$c = (float) $c; // float(25)
$d = (float) $d; // float(0)
$e = (float) $e; // float(0)
$f = (float) $f; // float(1)
$g = (float) $g; // float(0)
```

#### Cast to Boolean

To cast to boolean, use the (bool) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = 0;       // Integer
$d = -1;      // Integer
$e = 0.1;     // Float
$f = "hello"; // String
$g = "";      // String
$h = true;    // Boolean
$i = NULL;    // NULL

$a = (bool) $a; // bool(true)
$b = (bool) $b; // bool(true)
$c = (bool) $c; // bool(false)
$d = (bool) $d; // bool(true)
$e = (bool) $e; // bool(true)
$f = (bool) $f; // bool(true)
$g = (bool) $g; // bool(false)
$h = (bool) $h; // bool(true)
$i = (bool) $i; // bool(false)
```

#### Cast to Array

To cast to array, use the (array) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "hello"; // String
$d = true;    // Boolean
$e = NULL;    // NULL

$a = (array) $a; // array(1) { [0]=> int(5) }
$b = (array) $b; // array(1) { [0]=> float(5.34) }
$c = (array) $c; // array(1) { [0]=> string(5) "hello" }
$d = (array) $d; // array(1) { [0]=> bool(true) }
$e = (array) $e; // array(0) { }
```

#### Cast to Object

To cast to object, use the (object) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "hello"; // String
$d = true;    // Boolean
$e = NULL;    // NULL

$a = (object) $a;
$b = (object) $b;
$c = (object) $c;
$d = (object) $d;
$e = (object) $e;

var_dump($a); // object(stdClass)#1 (1) { ["scalar"]=> int(5) }
var_dump($b); // object(stdClass)#2 (1) { ["scalar"]=> float(5.34) }
var_dump($c); // object(stdClass)#3 (1) { ["scalar"]=> string(5) "hello" }
var_dump($d); // object(stdClass)#4 (1) { ["scalar"]=> bool(true) }
var_dump($e); // object(stdClass)#5 (0) { }
```

#### Cast to NULL

To cast to NULL, use the (unset) statement:

```php
$a = 5;       // Integer
$b = 5.34;    // Float
$c = "hello"; // String
$d = true;    // Boolean
$e = NULL;    // NULL

$a = (unset) $a; // NULL
$b = (unset) $b; // NULL
$c = (unset) $c; // NULL
$d = (unset) $d; // NULL
$e = (unset) $e; // NULL
```

### Constants

To create a constant, use the define() function.

Syntax:

```php
define(name, value, case-insensitive);
```

Parameters:

* name: Specifies the name of the constant

* value: Specifies the value of the constant

* case-insensitive: Specifies whether the constant name should be case-insensitive. Default is false. Note: Defining case-insensitive constants was deprecated in PHP 7.3. PHP 8.0 accepts only false, the value true will produce a warning.

```php
// Create a constant with a case-sensitive name
define("GREETING", "Welcome to my home!");
echo GREETING; // Welcome to my home!

// Create a constant with a case-insensitive name
define("GREETING", "Welcome to my home!", true);
echo greeting; // Welcome to my home!
```

#### Const Keyword

You can also create a constant by using the const keyword.

```php
const MYCAR = "Volvo";
echo MYCAR; // Volvo
```

#### Constant Arrays

From PHP7, you can create an Array constant using the define() function.

```php
define("cars", [
  "Alfa Romeo",
  "BMW",
  "Toyota"
]);
echo cars[0]; // Alfa Romeo
```

#### Constants are Global

Constants are automatically global and can be used across the entire script.

```php
define("GREETING", "Welcome to my home!");

function myTest() {
  echo GREETING;
}

myTest(); // Welcome to my home!
```

### Predefined Constants

PHP has nine predefined constants that change value depending on where they are used, and therefor they are called "magic constants".

These magic constants are written with a double underscore at the start and the end, except for the ClassName::class constant.

#### Magic Constants

Here are the magic constants

```php
// __CLASS__ : If used inside a class, the class name is returned.
class Color {
  public function myValue(){
    return __CLASS__;
  }
}
$red = new Color();
echo $red->myValue(); // Color

// __DIR__ : The directory of the file.
echo __DIR__; // C:\xampp\htdocs\learn-php

// __FILE__ : The file name including the full path.
echo __FILE__; // C:\xampp\htdocs\learn-php\README.md

// __FUNCTION__ : If inside a function, the function name is returned.
function welcome(){
  return __FUNCTION__;
}
echo welcome(); // welcome

// __LINE__ : The current line number.
echo __LINE__; // 956

// __METHOD__ : If used inside a function that belongs to a class, both class and function name is returned.
class Color {
  public function myValue(){
    return __CLASS__;
  }
}
$red = new Color();
echo $red->myValue(); // Color::myValue

// __NAMESPACE__ : If used inside a namespace, the name of the namespace is returned.
namespace myArea;
function myValue(){
  return __NAMESPACE__;
}
echo myValue(); // myArea

// __TRAIT__ : If used inside a trait, the trait name is returned.
trait message1 {
  public function msg1() {
    echo __TRAIT__;
  }
}

class Welcome {
  use message1;
}

$obj = new Welcome();
$obj->msg1(); // message1

// ClassName::class : Returns the name of the specified class and the name of the namespace, if any.
namespace myArea;

class Fruits {
  public function myValue(){
    return Fruits::class;
  }
}

$kiwi = new Fruits();
echo $kiwi->myValue(); // myArea\Fruits
```