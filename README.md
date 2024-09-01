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

### Operators

Operators are used to perform operations on variables and values.

#### Arithmetic Operators

The PHP arithmetic operators are used with numeric values to perform common arithmetical operations, such as addition, subtraction, multiplication etc.

```php
$a = 4;
$b = 2;

// Addition
echo $a + $b; // 6

// Subtraction
echo $a - $b; // 2

// Multiplication
echo $a * $b; // 8

// Division
echo $a / $b; // 2

// Modulus (Chia lấy dư)
echo $a % $b; // 0

// Exponentiation (Luỹ thừa)
echo $a ** $b; // 16
```

#### Assignment Operators

The basic assignment operator in PHP is "=". It means that the left operand gets set to the value of the assignment expression on the right.

```php
$a = 4;

// x = y
echo $a; // 4

// x += y
$a += 2;
echo $a; // 6

// x -= y
$a -= 2;
echo $a; // 2

// x *= y
$a *= 2;
echo $a; // 8

// x /= y
$a /= 2;
echo $a; // 2

// x %= y
$a %= 2;
echo $a; // 0
```

#### Comparison Operators

The PHP comparison operators are used to compare two values (number or string):

```php
$a = 100;
$b = "100";

// ==
var_dump($a == $b); // returns true because values are equal

// ===
var_dump($a === $b); // returns false because types are not equal

// !=
var_dump($a != $b); // returns false because values are equal

// <>
var_dump($a <> $b); // returns false because values are equal

// !==
var_dump($a !== $b); // returns true because types are not equal


$x = 100;
$y = 50;

// >
var_dump($x > $y); // returns true because $x is greater than $y

// <
var_dump($x < $y); // returns false because $y is less than $x

// >=
var_dump($x >= $y); // returns true because $x is greater than $y

// <=
var_dump($x <= $y); // returns false because $y greater than $x

// <=>
var_dump($x <=> $y); // returns +1 because $x is greater than $y
```

#### Increment / Decrement Operators

The PHP increment/decrement operators are used to increment/decrement a variable's value.

```php
$x = 10;
echo ++$x; // 11
echo $x++; // 10
echo --$x; // 9
echo $x--; // 10
```

#### Logical Operators

The PHP logical operators are used to combine conditional statements.

```php
$x = 100;
$y = 50;

// $x and $y
if ($x == 100 and $y == 50) {
    echo "Hello world!"; // true
}

// $x or $y
if ($x == 100 or $y == 80) {
    echo "Hello world!"; // true
}

// $x xor $y
if ($x == 100 xor $y == 80) {
    echo "Hello world!"; // true
}

// $x && $y
if ($x == 100 && $y == 50) {
    echo "Hello world!"; // true
}

// $x || $y
if ($x == 100 || $y == 80) {
    echo "Hello world!"; // true
}

// !$x
if (!($x == 90)) {
    echo "Hello world!"; // true
}
```

#### String Operators

PHP has two operators that are specially designed for strings.

```php
$txt1 = "Hello";
$txt2 = " world!";

// .
echo $txt1 . $txt2; // Hello world!

// .=
$txt1 .= $txt2;
echo $txt1; // Hello world!
```

#### Array Operators

The PHP array operators are used to compare arrays.

```php
$x = array("a" => "red", "b" => "green");
$y = array("c" => "blue", "d" => "yellow");

// $x + $y
print_r($x + $y); // Array ( [a] => red [b] => green [c] => blue [d] => yellow )

// $x == $y
var_dump($x == $y); // false

// $x === $y
var_dump($x === $y); // false

// $x != $y
var_dump($x != $y); // true

// $x <> $y
var_dump($x <> $y); // true

// $x !== $y
var_dump($x !== $y); // true
```

#### Conditional Assignment Operators

The PHP conditional assignment operators are used to set a value depending on conditions:

```php
// if empty($user) = TRUE, set $status = "anonymous"
echo $status = (empty($user)) ? "anonymous" : "logged in"; // "anonymous"

$user = "JiRim";
// if empty($user) = FALSE, set $status = "logged in"
echo $status = (empty($user)) ? "anonymous" : "logged in"; // "logged in"

// variable $user is the value of $_GET['user']
// and 'anonymous' if it does not exist
echo $user = $_GET["user"] ?? "anonymous"; // "anonymous"

// variable $color is "red" if $color does not exist or is null
echo $color = $color ?? "red"; // "red"
```

### If Statements

```php
// Syntax
if (condition) {
  // code to be executed if condition is true;
}

$t = 14;
if ($t < 20) {
  echo "Have a good day!";
}
```

#### If Operators

If statements usually contain conditions that compare two values.

```php
// ==
$t = 14;
if ($t == 14) {
  echo "Have a good day!";
}

// ===
$x = 100;
$y = 100;

if ($x === $y) {
  echo "$x is identical to $y";
}

// !=
$x = 100;
$y = 50;

if ($x != $y) {
  echo "$x is not equal to $y";
}

// <>
$x = 100;
$y = 50;

if ($x <> $y) {
  echo "$x is not equal to $y";
}

// !==
$x = 100;
$y = 50;

if ($x !== $y) {
  echo "$x is not identical to $y";
}

// >
$x = 100;
$y = 50;

if ($x > $y) {
  echo "$x is greater than $y";
}

// <
$x = 100;
$y = 50;

if ($y < $x) {
  echo "$y is less than $x";
}

// >=
$x = 100;
$y = 100;

if ($x >= $y) {
  echo "$x is greater than, or equal to $y";
}

// <=
$x = 100;
$y = 100;

if ($y <= $x) {
  echo "$y is less than, or equal to $x";
}
```

#### Logical Operators

```php
$x = 100;
$y = 50;

// and
if ($x == 100 and $y == 50) {
    echo "Hello world!"; // true
}

// &&
if ($x == 100 && $y == 50) {
    echo "Hello world!"; // true
}

// or
if ($x == 100 or $y == 80) {
    echo "Hello world!"; // true
}

// ||
if ($x == 100 || $y == 80) {
    echo "Hello world!"; // true
}

// xor
if ($x == 100 xor $y == 80) {
    echo "Hello world!"; // true
}

// !
if (!($x == 90)) {
    echo "Hello world!"; // true
}
```

#### Short Hand If

To write shorter code, you can write if statements on one line.

```php
$a = 5;

if ($a < 10) $b = "Hello";
echo $b
```

#### Short Hand If...Else

if...else statements can also be written in one line, but the syntax is a bit different.

```php
$a = 13;

$b = $a < 10 ? "Hello" : "Good Bye";
echo $b;
```

#### Nested If

You can have if statements inside if statements, this is called nested if statements.

```php
$a = 13;

if ($a > 10) {
  echo "Above 10";
  if ($a > 20) {
    echo " and also above 20";
  } else {
    echo " but not above 20";
  }
}
```

### Switch Statement

Use the switch statement to select one of many blocks of code to be executed.

```php
$favcolor = "red";

switch ($favcolor) {
  case "red":
    echo "Your favorite color is red!";
    break;
  case "blue":
    echo "Your favorite color is blue!";
    break;
  case "green":
    echo "Your favorite color is green!";
    break;
  default:
    echo "Your favorite color is neither red, blue, nor green!";
}
```

#### The default Keyword

The default keyword specifies the code to run if there is no case match:

```php
$d = 4;

switch ($d) {
  case 6:
    echo "Today is Saturday";
    break;
  case 0:
    echo "Today is Sunday";
    break;
  default:
    echo "Looking forward to the Weekend";
}
```

Putting  the default block elsewhere than at the end of the switch block is allowed, but not recommended.

```php
$d = 4;

switch ($d) {
  default:
    echo "Looking forward to the Weekend";
    break;
  case 6:
    echo "Today is Saturday";
    break;
  case 0:
    echo "Today is Sunday";
}
```

#### Common Code Blocks

If you want multiple cases to use the same code block, you can specify the cases like this:

```php
$d = 3;

switch ($d) {
  case 1:
  case 2:
  case 3:
  case 4:
  case 5:
    echo "The weeks feels so long!";
    break;
  case 6:
  case 0:
    echo "Weekends are the best!";
    break;
  default:
    echo "Something went wrong";
}
```

### Loops

Loops are used to execute the same block of code again and again, as long as a certain condition is true.

Loops Type:

* while - loops through a block of code as long as the specified condition is true

* do...while - loops through a block of code once, and then repeats the loop as long as the specified condition is true

* for - loops through a block of code a specified number of times

* foreach - loops through a block of code for each element in an array

#### While Loop

```php
// Print $i as long as $i is less than 6:
$i = 1;
while ($i < 6) {
  echo $i;
  $i++;
} // 1,2,3,4,5
```

##### Break Statement

With the break statement we can stop the loop even if the condition is still true:

```php
$i = 1;
while ($i < 6) {
  if ($i == 3) break;
  echo $i;
  $i++;
} // 1,2
```

##### The continue Statement

With the continue statement we can stop the current iteration, and continue with the next:

```php
$i = 0;
while ($i < 6) {
  $i++;
  if ($i == 3) continue;
  echo $i;
} // 1,2,4,5,6
```

##### Alternative Syntax

The while loop syntax can also be written with the endwhile statement like this

```php
$i = 1;
while ($i < 6):
  echo $i;
  $i++;
endwhile; // 1,2,3,4,5
```

#### Do While Loop

```php
$i = 1;

do {
  echo $i;
  $i++;
} while ($i < 6); // 1,2,3,4,5

// Let us see what happens if we set the $i variable to 8 instead of 1, before execute the same do...while loop again:
$i = 8;

do {
  echo $i;
  $i++;
} while ($i < 6);
```

##### The break Statement

With the break statement we can stop the loop even if the condition is still true:

```php
$i = 1;

do {
  if ($i == 3) break;
  echo $i;
  $i++;
} while ($i < 6); // 1,2
```

##### The continue Statement

With the continue statement we can stop the current iteration, and continue with the next:

```php
$i = 0;

do {
  $i++;
  if ($i == 3) continue;
  echo $i;
} while ($i < 6); // 1,2,4,5,6
```

#### The PHP for Loop

The for loop is used when you know how many times the script should run.

##### Syntax

```php
for (expression1, expression2, expression3) {
  // code block
}
```

* expression1 is evaluated once

* expression2 is evaluated before each iteration

* expression3 is evaluated after each iteration

```php
for ($x = 0; $x <= 10; $x++) {
  echo "The number is: $x <br>";
}
```

##### The break Statement

With the break statement we can stop the loop even if the condition is still true:

```php
for ($x = 0; $x <= 10; $x++) {
  if ($x == 3) break;
  echo "The number is: $x <br>";
} // 0,1,2
```

##### The continue Statement

With the continue statement we can stop the current iteration, and continue with the next:

```php
for ($x = 0; $x <= 10; $x++) {
  if ($x == 3) continue;
  echo "The number is: $x <br>";
}
```

#### Foreach Loop

##### The foreach Loop on Arrays

The most common use of the foreach loop, is to loop through the items of an array.

```php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) {
  echo "$x <br>";
}
```

##### Keys and Values

```php
$members = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach ($members as $x => $y) {
  echo "$x : $y <br>";
}
```

##### The foreach Loop on Objects

The foreach loop can also be used to loop through properties of an object:

```php
class Car {
  public $color;
  public $model;
  public function __construct($color, $model) {
    $this->color = $color;
    $this->model = $model;
  }
}

$myCar = new Car("red", "Volvo");

foreach ($myCar as $x => $y) {
  echo "$x: $y <br>";
}
```

##### The break Statement

With the break statement we can stop the loop even if it has not reached the end:

```php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) {
  if ($x == "blue") break;
  echo "$x <br>";
}
```

##### The continue Statement

With the continue statement we can stop the current iteration, and continue with the next:

```php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) {
  if ($x == "blue") continue;
  echo "$x <br>";
}
```

##### Foreach Byref

When looping through the array items, any changes done to the array item will, by default, NOT affect the original array:

```php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) {
  if ($x == "blue") $x = "pink";
}

var_dump($colors); // "red", "green", "blue", "yellow"
```

##### Alternative Syntax

The foreach loop syntax can also be written with the endforeach statement like this

```php
$colors = array("red", "green", "blue", "yellow");

foreach ($colors as $x) :
  echo "$x <br>";
endforeach;
```

### Functions

#### Create a Function

A user-defined function declaration starts with the keyword function, followed by the name of the function:

```php
function myMessage() {
  echo "Hello world!";
}

// Call a Function
myMessage()
```

#### PHP Function Arguments

Arguments are specified after the function name, inside the parentheses. You can add as many arguments as you want, just separate them with a comma.

```php
function color($cname) {
  echo "$cname<br>";
}

color("Red");
color("Blue");
color("Green");
color("White");
color("Black");
```

#### PHP Default Argument Value

The following example shows how to use a default parameter. If we call the function setHeight() without arguments it takes the default value as argument:

```php
function setHeight($minheight = 50) {
  echo "The height is : $minheight <br>";
}

setHeight(350);
setHeight(); // default value of 50
setHeight(135);
setHeight(80);
```

#### Functions - Returning values

To let a function return a value, use the return statement:

```php
function sum($x, $y) {
  $z = $x + $y;
  return $z;
}

echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "7 + 13 = " . sum(7, 13) . "<br>";
echo "2 + 4 = " . sum(2, 4);
```

#### Passing Arguments by Reference

```php
function add_five(&$value) {
  $value += 5;
}

$num = 2;
add_five($num);
echo $num;
```

#### Variable Number of Arguments

By using the ... operator in front of the function parameter, the function accepts an unknown number of arguments. This is also called a variadic function.

```php
function sumMyNumbers(...$x) {
  $n = 0;
  $len = count($x);
  for($i = 0; $i < $len; $i++) {
    $n += $x[$i];
  }
  return $n;
}

$a = sumMyNumbers(5, 2, 6, 2, 7, 7);
echo $a; // 29
```

#### Return Type Declarations

PHP 7 also supports Type Declarations for the return statement. Like with the type declaration for function arguments, by enabling the strict requirement, it will throw a "Fatal Error" on a type mismatch.

```php
declare(strict_types=1); // strict requirement
function addNumbers(float $a, float $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
```

### Global Variables - Superglobals

#### Global Variables

To use a global variable inside a function you have to either define them as global with the global keyword, or refer to them by using the $GLOBALS syntax.

```php
$x = 75;

function myfunction() {
  echo $GLOBALS['x'];
}

myfunction() // 75
```

You can also refer to global variables inside functions by defining them as global with the global keyword.

```php
$x = 75;

function myfunction() {
  global $x;
  echo $x;
}
myfunction() // 75
```

#### $_SERVER

Is a PHP super global variable which holds information about headers, paths, and script locations.

```php
echo $_SERVER['PHP_SELF']; // Returns the filename of the currently executing script

echo $_SERVER['GATEWAY_INTERFACE']; // Returns the version of the Common Gateway Interface (CGI) the server is using

echo $_SERVER['SERVER_ADDR']; // Returns the IP address of the host server

echo $_SERVER['SERVER_NAME']; // 	Returns the name of the host server

echo $_SERVER['SERVER_SOFTWARE']; // Returns the server identification string (such as Apache/2.2.24)

echo $_SERVER['SERVER_PROTOCOL']; // Returns the name and revision of the information protocol (such as HTTP/1.1)

echo $_SERVER['REQUEST_METHOD']; // Returns the request method used to access the page (such as POST)

echo $_SERVER['REQUEST_TIME']; // Returns the timestamp of the start of the request (such as 1377687496)

echo $_SERVER['QUERY_STRING']; // Returns the query string if the page is accessed via a query string

echo $_SERVER['HTTP_ACCEPT']; // Returns the Accept header from the current request

echo $_SERVER['HTTP_ACCEPT_CHARSET']; // Returns the Accept_Charset header from the current request (such as utf-8,ISO-8859-1)

echo $_SERVER['HTTP_HOST']; // Returns the Host header from the current request

echo $_SERVER['HTTP_REFERER']; // Returns the complete URL of the current page (not reliable because not all user-agents support it)

echo $_SERVER['HTTPS']; // Is the script queried through a secure HTTP protocol

echo $_SERVER['REMOTE_ADDR']; // Returns the IP address from where the user is viewing the current page

echo $_SERVER['REMOTE_HOST']; // Returns the Host name from where the user is viewing the current page

echo $_SERVER['REMOTE_PORT']; // Returns the port being used on the user's machine to communicate with the web server

echo $_SERVER['SCRIPT_FILENAME']; // Returns the absolute pathname of the currently executing script

echo $_SERVER['SERVER_ADMIN']; // Returns the value given to the SERVER_ADMIN directive in the web server configuration file

echo $_SERVER['SERVER_PORT']; // Returns the port on the server machine being used by the web server for communication (such as 80)

echo $_SERVER['SERVER_SIGNATURE'];// Returns the server version and virtual host name which are added to server-generated pages

echo $_SERVER['PATH_TRANSLATED']; // Returns the file system based path to the current script

echo $_SERVER['SCRIPT_NAME']; // Returns the path of the current script

echo $_SERVER['SCRIPT_URI']; // Returns the URI of the current page
```

#### $_REQUEST

Is a PHP super global variable which contains submitted form data, and all cookie data.

##### Using $_REQUEST on $_POST Requests

```php
<html>
<body>

<form method="post" action="demo_request.php">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

</body>
</html>

$name = $_REQUEST['fname'];
echo $name;
```

##### Using $_REQUEST on $_GET Requests

GET request can be form submissions as in the example above, with the method attribute of the HTML <form> element set to GET.

```php
<html>
<body>

<a href="demo_phpfile.php?subject=PHP&web=W3schools.com">Test $GET</a>

</body>
</html>
```

#### $_POST

A HTML form submits information via the HTTP POST method if the form's method attribute is set to "POST".

```php
<html>
<body>

<form method="POST" action="demo_request.php">
  Name: <input type="text" name="fname">
  <input type="submit">
</form>

</body>
</html>

// When a user clicks the submit button, the form data is sent to a PHP file specified in the action attribute of the <form> tag.
$name = $_POST['fname'];
echo $name;
```

#### $_GET

In the PHP file we can use the $_GET variable to collect the value of the query string.

```php
<a href="demo_phpfile.php?name=JiRim&email=jirim@example.com">Test $GET</a>

echo "Study " . $_GET['name'] . " at " . $_GET['email'];
```

##### $_GET in HTML Forms

A HTML form submits information via the HTTP GET method if the form's method attribute is set to "GET".

```php
<form action="welcome_get.php" method="GET">
  Name: <input type="text" name="name">
  E-mail: <input type="text" name="email">
  <input type="submit">
</form>

// data: welcome_get.php?name=JiRim&email=jirim@example.com
echo $_GET["name"]; // JiRim
echo $_GET["email"]; // jirim@example.com
```

### Regular Expressions

What is a Regular Expression?

A regular expression is a sequence of characters that forms a search pattern. When you search for data in a text, you can use this search pattern to describe what you are searching for.

#### Syntax

In PHP, regular expressions are strings composed of delimiters, a pattern and optional modifiers.

```php
$exp = "/jirim/i";
```
// In the example above, / is the delimiter, jirim is the pattern that is being searched for, and i is a modifier that makes the search case-insensitive.

#### Regular Expression Functions

PHP provides a variety of functions that allow you to use regular expressions.

* preg_match(): Returns 1 if the pattern was found in the string and 0 if not

* preg_match_all(): Returns the number of times the pattern was found in the string, which may also be 0

* preg_replace(): Returns a new string where matched patterns have been replaced with another string

#### Using preg_match()

The preg_match() function will tell you whether a string contains matches of a pattern.

```php
$str = "Hello JiRim";
$pattern = "/jirim/i";
echo preg_match($pattern, $str); // 1
```

#### Using preg_match_all()

The preg_match_all() function will tell you how many matches were found for a pattern in a string.

```php
$str = "Apples are red, and apples taste sweet.";
$pattern = "/apples/i";
echo preg_match_all($pattern, $str); // 2
```

### Using preg_replace()

The preg_replace() function will replace all of the matches of the pattern in a string with another string.

```php
$str = "Welcome to New York City!";
$pattern = "/new york city/i";
echo preg_replace($pattern, "Los Angeles", $str);
```

#### Regular Expression Modifiers

* i: Performs a case-insensitive search

* m: Performs a multiline search (patterns that search for a match at the beginning or end of a string will now match the beginning or end of each line)

* u: Enables correct matching of UTF-8 encoded patterns

#### Regular Expression Patterns

Brackets are used to find a range of characters:

```php
// [abc]: Find one or many of the characters inside the brackets
$txt = "Hello, JiRim!";
$pattern = "/[li]/";
echo preg_match_all($pattern, $txt); // 4

// [^abc]: Find any character NOT between the brackets
$txt = "Welcome";
$pattern = "/[^eo]/";
echo preg_match_all($pattern, $txt); // 4

// [a-z]:	Find any character alphabetically between two letters
$txt = "Welcome";
$pattern = "/[e-o]/";
echo preg_match_all($pattern, $txt); // 5

// [A-z]: Find any character alphabetically between a specified upper-case letter and a specified lower-case letter
$txt = "Welcome to my home";
$pattern = "/[T-e]/";
echo preg_match_all($pattern, $txt); // 5

// [A-Z]: Find any character alphabetically between two upper-case letters.
$txt = "Welcome to my home";
$pattern = "/[A-Z]/";
echo preg_match_all($pattern, $txt); // 1

// [123]: Find one or many of the digits inside the brackets
$txt = "JiRim was born in 2001.";
$pattern = "/[123]/";
echo preg_match_all($pattern, $txt); // 2

// [0-5]: Find any digits between the two numbers
$txt = "Call 555-2368";
$pattern = "/[0-5]/";
echo preg_match_all($pattern, $txt); // 5

// [0-9]: Find any digits
$txt = "JiRim was born in 2001.";
$pattern = "/[0-9]/";
echo preg_match_all($pattern, $txt); // 4
```

#### Metacharacters

Metacharacters are characters with a special meaning:

```php
// | Find a match for any one of the patterns separated by | as in: cat|dog|fish
$txt = "We have three dogs, one fish, but no cats";
$pattern = "/cat|dog|fish/";
echo preg_match_all($pattern, $txt); // 3

// . Find any character
$txt = "JiRim was born in 2001.";
$pattern = "/./";
echo preg_match_all($pattern, $txt); // 23

// ^ Finds a match as the beginning of a string as in: ^Hello
$txt = "JiRim was born in 2001.";
$pattern = "/^Ji/";
echo preg_match_all($pattern, $txt); // 1

// $: Finds a match at the end of the string as in: World$
$txt = "Hello World";
$pattern = "/World$/";
echo preg_match_all($pattern, $txt); // 1

// \d: Find any digits
$txt = "JiRim was born in 2001.";
$pattern = "/\d/";
echo preg_match_all($pattern, $txt); // 4

// \D: Find any non-digits
$txt = "JiRim was born in 2001.";
$pattern = "/\D/";
echo preg_match_all($pattern, $txt); // 19

// \s: Find any whitespace character
$txt = "JiRim was born in 2001.";
$pattern = "/\s/";
echo preg_match_all($pattern, $txt); // 4

// \S: Find any non-whitespace character
$txt = "JiRim was born in 2001.";
$pattern = "/\S/";
echo preg_match_all($pattern, $txt); // 19

// \w: Find any alphabetical letter (a to Z) and digit (0 to 9)
$txt = "JiRim was born in 2001.";
$pattern = "/\w/";
echo preg_match_all($pattern, $txt); // 18

// \W	Find any non-alphabetical and non-digit character
$txt = "JiRim was born in 2001.";
$pattern = "/\W/";
echo preg_match_all($pattern, $txt); // 5

// \b: Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b
$txt = "Hello World";
$pattern = "/\bHel/";
echo preg_match_all($pattern, $txt); // 1

// \uxxxx: Find the Unicode character specified by the hexadecimal number xxxx
$txt = "JiRim was born in 2001.";
$pattern = "/\u{0030}/";
echo preg_match_all($pattern, $txt); // 2
```

#### Quantifiers

Quantifiers define quantities:

```php
// n+	Matches any string that contains at least one n
$txt = "JiRim was born in 2001.";
$pattern = "/n+/";
echo preg_match_all($pattern, $txt); // 2

// n*	Matches any string that contains zero or more occurrences of n
$txt = "Email của tôi là example@domain.com.";
$pattern = "/@domain\.com*/";
echo preg_match_all($pattern, $txt); // 1

// n?	Matches any string that contains zero or one occurrences of n
$txt = "The cats are playing.";
$pattern = "/cats?/";
echo preg_match_all($pattern, $txt); // 1

// n{3}	Matches any string that contains a sequence of 3 n's
$txt = "Mã bưu điện là 123.";
$pattern = "/\d{3}/";
echo preg_match_all($pattern, $txt); // 1

// n{2, 5}	Matches any string that contains a sequence of at least 2, but not more that 5 n's
$txt = "Tên tài khoản của bạn là user123.";
$pattern = "/user\d{2,5}/";
echo preg_match_all($pattern, $txt); // 1

// n{3,}	Matches any string that contains a sequence of at least 3 n's
$txt = "Họ của tôi là Nguyen.";
$pattern = "/\b\w{3,}\b/";
echo preg_match_all($pattern, $txt); // 2
```

#### Grouping

You can use parentheses ( ) to apply quantifiers to entire patterns. They also can be used to select parts of the pattern to be used as a match.

```php
$str = "Apples and bananas.";
$pattern = "/ba(na){2}/i";
echo preg_match($pattern, $str);
```

### Form Handling

#### A Simple HTML Form

The example below displays a simple HTML form with two input fields and a submit button:

```php
// POST
<form action="welcome.php" method="POST">
Name: <input type="text" name="name"><br>
E-mail: <input type="text" name="email"><br>
<input type="submit">
</form>

// When the user fills out the form above and clicks the submit button
Welcome <?php echo $_POST["name"]; ?><br> // Welcome JiRim
Your email address is: <?php echo $_POST["email"]; ?> // Your email address is: jirim@gmail.com

// GET
<form action="welcome_get.php" method="GET">
Name: <input type="text" name="name"><br>
E-mail: <input type="text" name="email"><br>
<input type="submit">
</form>

// Results
Welcome <?php echo $_GET["name"]; ?><br> // Welcome JiRim
Your email address is: <?php echo $_GET["email"]; ?> // Your email address is: jirim@gmail.com
```

#### When to use GET?

GET may be used for sending non-sensitive data.

Note: GET should NEVER be used for sending passwords or other sensitive information!

#### When to use POST?

Information sent from a form with the POST method is invisible to others (all names/values are embedded within the body of the HTTP request) and has no limits on the amount of information to send.

### Form Validation

#### Text Fields

The name, email, and website fields are text input elements, and the comment field is a textarea.

```php
Name: <input type="text" name="name">
E-mail: <input type="text" name="email">
Website: <input type="text" name="website">
Comment: <textarea name="comment" rows="5" cols="40"></textarea>
```

#### Radio Buttons

The gender fields are radio buttons and the HTML code looks like this:

```php
Gender:
<input type="radio" name="gender" value="female">Female
<input type="radio" name="gender" value="male">Male
<input type="radio" name="gender" value="other">Other
```

#### The Form Element

```php
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">

// The $_SERVER["PHP_SELF"] is a super global variable that returns the filename of the currently executing script.

// The htmlspecialchars() function converts special characters into HTML entities. This means that it will replace HTML characters like < and > with &lt; and &gt;. This prevents attackers from exploiting the code by injecting HTML or Javascript code (Cross-site Scripting attacks) in forms.
```

### Date and time

The PHP date() function formats a timestamp to a more readable date and time.

```php
#Syntax
date(format,timestamp)
```

* format:	Required. Specifies the format of the timestamp

* timestamp:	Optional. Specifies a timestamp. Default is the current date and time

#### Get a Date

* d - Represents the day of the month (01 to 31)

* m - Represents a month (01 to 12)

* Y - Represents a year (in four digits)

* l (lowercase 'L') - Represents the day of the week

```php
echo "Today is " . date("Y/m/d") . "<br>"; // Today is 2024/08/18
echo "Today is " . date("Y.m.d") . "<br>"; // Today is 2020.08.18
echo "Today is " . date("Y-m-d") . "<br>"; // Today is 2020-08-18
echo "Today is " . date("l"); // Today is Sunday
```

#### Get a Time

* H - 24-hour format of an hour (00 to 23)

* h - 12-hour format of an hour with leading zeros (01 to 12)

* i - Minutes with leading zeros (00 to 59)

* s - Seconds with leading zeros (00 to 59)

* a - Lowercase Ante meridiem and Post meridiem (am or pm)

```php
echo "The time is " . date("h:i:sa"); // The time is 11:38:48pm
```

#### Get Your Time Zone

The example below sets the timezone to "America/New_York", then outputs the current time in the specified format:

```php
date_default_timezone_set("America/New_York");
echo "The time is " . date("h:i:sa"); // The time is 12:39:40pm
```

#### Create a Date With mktime()

The PHP mktime() function returns the Unix timestamp for a date. The Unix timestamp contains the number of seconds between the Unix Epoch (January 1 1970 00:00:00 GMT) and the time specified.

```php
// Syntax
mktime(hour, minute, second, month, day, year);

$d=mktime(11, 14, 54, 8, 12, 2014);
echo "Created date is " . date("Y-m-d h:i:sa", $d); // Created date is 2014-08-12 11:14:54am
```

#### Create a Date From a String With strtotime()

The PHP strtotime() function is used to convert a human readable date string into a Unix timestamp (the number of seconds since January 1 1970 00:00:00 GMT).

```php
// Syntax
strtotime(time, now);

$d=strtotime("10:30pm April 15 2014");
echo "Created date is " . date("Y-m-d h:i:sa", $d); // Created date is 2014-04-15 10:30:00pm

$d=strtotime("tomorrow");
echo date("Y-m-d h:i:sa", $d) . "<br>"; // 2024-08-19 12:00:00am

$d=strtotime("next Saturday");
echo date("Y-m-d h:i:sa", $d) . "<br>"; // 2024-08-24 12:00:00am

$d=strtotime("+3 Months");
echo date("Y-m-d h:i:sa", $d) . "<br>"; // 2024-11-18 04:42:34pm
```

### Include and Require Statements

#### The include and require statements are identical, except upon failure:

* require will produce a fatal error (E_COMPILE_ERROR) and stop the script

* include will only produce a warning (E_WARNING) and the script will continue

```php
// Syntax
include 'filename';

or

require 'filename';
```

Assume we have a standard footer file called "footer.php", that looks like this:

```php
echo "<p>Copyright &copy; 1999-" . date("Y") . " JiRim</p>";
```

To include the footer file in a page, use the include statement:

```php
<h1>Welcome to my home page!</h1>
<p>Some text.</p>
<p>Some more text.</p>
include 'footer.php';
```

#### Include vs Require

The require statement is also used to include a file into the PHP code.

However, there is one big difference between include and require; when a file is included with the include statement and PHP cannot find it, the script will continue to execute:

```php
<h1>Welcome to my home page!</h1>
include 'noFileExists.php';
echo "I have a $color $car."; // I have a .

require 'noFileExists.php';
echo "I have a $color $car."; // empty
```

### File Handling

File handling is an important part of any web application. You often need to open and process a file for different tasks.

#### readfile() Function

The readfile() function reads a file and writes it to the output buffer.

```php
// file webdictionary.txt
AJAX = Asynchronous JavaScript and XML
CSS = Cascading Style Sheets
HTML = Hyper Text Markup Language
PHP = PHP Hypertext Preprocessor
SQL = Structured Query Language
SVG = Scalable Vector Graphics
XML = EXtensible Markup Language

echo readfile("webdictionary.txt");
```

### File Open/Read/Close

#### Open File - fopen()

A better method to open files is with the fopen() function. This function gives you more options than the readfile() function.

```php
// file webdictionary.txt
AJAX = Asynchronous JavaScript and XML
CSS = Cascading Style Sheets
HTML = Hyper Text Markup Language
PHP = PHP Hypertext Preprocessor
SQL = Structured Query Language
SVG = Scalable Vector Graphics
XML = EXtensible Markup Language

$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fread($myfile,filesize("webdictionary.txt"));
fclose($myfile);
```

* r:	Open a file for read only. File pointer starts at the beginning of the file

* w: Open a file for write only. Erases the contents of the file or creates a new file if it doesn't exist. File pointer starts at the beginning of the file  

* a: Open a file for write only. The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist

* x: Creates a new file for write only. Returns FALSE and an error if file already exists

* r+: Open a file for read/write. File pointer starts at the beginning of the file

* w+: Open a file for read/write. Erases the contents of the file or creates a new file if it doesn't exist. File pointer starts at the beginning of the file

* a+: Open a file for read/write. The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist

* x+: Creates a new file for read/write. Returns FALSE and an error if file already exists

#### Read File - fread()

The fread() function reads from an open file.

The first parameter of fread() contains the name of the file to read from and the second parameter specifies the maximum number of bytes to read.

```php
fread($myfile,filesize("webdictionary.txt"));
```

#### Close File - fclose()

The fclose() function is used to close an open file.

```php
$myfile = fopen("webdictionary.txt", "r");
// some code to be executed....
fclose($myfile);
```

#### Read Single Line - fgets()

The fgets() function is used to read a single line from a file.

```php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
echo fgets($myfile); // AJAX = Asynchronous JavaScript and XML
fclose($myfile);
```

#### Check End-Of-File - feof()

The feof() function checks if the "end-of-file" (EOF) has been reached.

The feof() function is useful for looping through data of unknown length.

```php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
// Output one line until end-of-file
while(!feof($myfile)) {
  echo fgets($myfile) . "<br>";
  /* result: AJAX = Asynchronous JavaScript and XML
            CSS = Cascading Style Sheets
            HTML = Hyper Text Markup Language
            PHP = PHP Hypertext Preprocessor
            SQL = Structured Query Language
            SVG = Scalable Vector Graphics
            XML = EXtensible Markup Language */
}
fclose($myfile);
```

#### Read Single Character - fgetc()

The fgetc() function is used to read a single character from a file.

```php
$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");
// Output one character until end-of-file
while(!feof($myfile)) {
  echo fgetc($myfile);
  // result: AJAX = Asynchronous JavaScript and XML CSS = Cascading Style Sheets HTML = Hyper Text Markup Language PHP = PHP Hypertext Preprocessor SQL = Structured Query Language SVG = Scalable Vector Graphics XML = EXtensible Markup Language
}
fclose($myfile);
```

### File Create/Write

#### PHP Create File - fopen()

The fopen() function is also used to create a file. Maybe a little confusing, but in PHP, a file is created using the same function used to open files.

```php
$myfile = fopen("testfile.txt", "w")
```

#### PHP Write to File - fwrite()

The first parameter of fwrite() contains the name of the file to write to and the second parameter is the string to be written.

```php
$myfile = fopen("newfile.txt", "w") or die("Unable to open file!");
$txt = "John Doe\n";
fwrite($myfile, $txt);
$txt = "Jane Doe\n";
fwrite($myfile, $txt);
fclose($myfile);
```

#### PHP Overwriting

Now that "newfile.txt" contains some data we can show what happens when we open an existing file for writing. All the existing data will be ERASED and we start with an empty file.

```php
$myfile = fopen("newfile.txt", "w") or die("Unable to open file!");
$txt = "Mickey Mouse\n";
fwrite($myfile, $txt);
$txt = "Minnie Mouse\n";
fwrite($myfile, $txt);
fclose($myfile);
```

#### PHP Append Text

You can append data to a file by using the "a" mode. The "a" mode appends text to the end of the file, while the "w" mode overrides (and erases) the old content of the file.

```php
$myfile = fopen("newfile.txt", "a") or die("Unable to open file!");
$txt = "Donald Duck\n";
fwrite($myfile, $txt);
$txt = "Goofy Goof\n";
fwrite($myfile, $txt);
fclose($myfile);
```

### File Upload

#### Configure The "php.ini" File

First, ensure that PHP is configured to allow file uploads.

In your "php.ini" file, search for the file_uploads directive, and set it to On:

```php
file_uploads = On
```

#### Create The HTML Form

```php
<form action="upload.php" method="post" enctype="multipart/form-data">
  Select image to upload:
  <input type="file" name="fileToUpload" id="fileToUpload">
  <input type="submit" value="Upload Image" name="submit">
</form>
```

Some rules to follow for the HTML form above:

* Make sure that the form uses method="post"

* The form also needs the following attribute: enctype="multipart/form-data". It specifies which content-type to use when submitting the form

* The type="file" attribute of the <input> tag shows the input field as a file-select control, with a "Browse" button next to the input control

#### Create The Upload File PHP Script

The "upload.php" file contains the code for uploading a file:

```php
$target_dir = "uploads/";
$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$imageFileType = strtolower(pathinfo($target_file,PATHINFO_EXTENSION));
// Check if image file is a actual image or fake image
if(isset($_POST["submit"])) {
  $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);
  if($check !== false) {
    echo "File is an image - " . $check["mime"] . ".";
    $uploadOk = 1;
  } else {
    echo "File is not an image.";
    $uploadOk = 0;
  }
}
```

PHP script explained:

* $target_dir = "uploads/" - specifies the directory where the file is going to be placed

* $target_file specifies the path of the file to be uploaded

* $uploadOk=1 is not used yet (will be used later)

* $imageFileType holds the file extension of the file (in lower case)

* Next, check if the image file is an actual image or a fake image

#### Check if File Already Exists

First, we will check if the file already exists in the "uploads" folder. If it does, an error message is displayed, and $uploadOk is set to 0:

```php
// Check if file already exists
if (file_exists($target_file)) {
  echo "Sorry, file already exists.";
  $uploadOk = 0;
}
```

#### Limit File Size

Now, we want to check the size of the file. If the file is larger than 500KB, an error message is displayed, and $uploadOk is set to 0:

```php
// Check file size
if ($_FILES["fileToUpload"]["size"] > 500000) {
  echo "Sorry, your file is too large.";
  $uploadOk = 0;
}
```

#### Limit File Type

The code below only allows users to upload JPG, JPEG, PNG, and GIF files. All other file types gives an error message before setting $uploadOk to 0:

```php
if($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg" && $imageFileType != "gif" ) {
  echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";
  $uploadOk = 0;
}
```


#### Complete Upload File PHP Script

```php
$target_dir = "uploads/";
$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$imageFileType = strtolower(pathinfo($target_file,PATHINFO_EXTENSION));

// Check if image file is a actual image or fake image
if(isset($_POST["submit"])) {
  $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);
  if($check !== false) {
    echo "File is an image - " . $check["mime"] . ".";
    $uploadOk = 1;
  } else {
    echo "File is not an image.";
    $uploadOk = 0;
  }
}

// Check if file already exists
if (file_exists($target_file)) {
  echo "Sorry, file already exists.";
  $uploadOk = 0;
}

// Check file size
if ($_FILES["fileToUpload"]["size"] > 500000) {
  echo "Sorry, your file is too large.";
  $uploadOk = 0;
}

// Allow certain file formats
if($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg"
&& $imageFileType != "gif" ) {
  echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";
  $uploadOk = 0;
}

// Check if $uploadOk is set to 0 by an error
if ($uploadOk == 0) {
  echo "Sorry, your file was not uploaded.";
// if everything is ok, try to upload file
} else {
  if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target_file)) {
    echo "The file ". htmlspecialchars( basename( $_FILES["fileToUpload"]["name"])). " has been uploaded.";
  } else {
    echo "Sorry, there was an error uploading your file.";
  }
}
```

### Cookies

#### What is a Cookie?

A cookie is often used to identify a user. A cookie is a small file that the server embeds on the user's computer. Each time the same computer requests a page with a browser, it will send the cookie too. With PHP, you can both create and retrieve cookie values.

#### Create Cookies With PHP

A cookie is created with the setcookie() function.

```php
// Syntax
setcookie(name, value, expire, path, domain, secure, httponly);
```

#### Create/Retrieve a Cookie

```php
$cookie_name = "user";
$cookie_value = "JiRim";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/"); // 86400 = 1 day

if(!isset($_COOKIE[$cookie_name])) {
  echo "Cookie named '" . $cookie_name . "' is not set!";
} else {
  echo "Cookie '" . $cookie_name . "' is set!<br>";
  echo "Value is: " . $_COOKIE[$cookie_name]; // JiRim
}
```

#### Modify a Cookie Value

```php
$cookie_name = "user";
$cookie_value = "Do Phuong";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");

if(!isset($_COOKIE[$cookie_name])) {
  echo "Cookie named '" . $cookie_name . "' is not set!";
} else {
  echo "Cookie '" . $cookie_name . "' is set!<br>";
  echo "Value is: " . $_COOKIE[$cookie_name]; // Do Phuong
}
```

#### Delete a Cookie

To delete a cookie, use the setcookie() function with an expiration date in the past:

```php
setcookie("user", "", time() - 3600);
echo "Cookie 'user' is deleted.";
```

#### Check if Cookies are Enabled

The following example creates a small script that checks whether cookies are enabled. First, try to create a test cookie with the setcookie() function, then count the $_COOKIE array variable:

```php
setcookie("test_cookie", "test", time() + 3600, '/');

if(count($_COOKIE) > 0) {
  echo "Cookies are enabled.";
} else {
  echo "Cookies are disabled.";
}
```

### Sessions

#### What is a PHP Session?

When you work with an application, you open it, do some changes, and then you close it. This is much like a Session. The computer knows who you are. It knows when you start the application and when you end. But on the internet there is one problem: the web server does not know who you are or what you do, because the HTTP address doesn't maintain state.

Session variables solve this problem by storing user information to be used across multiple pages (e.g. username, favorite color, etc). By default, session variables last until the user closes the browser.

So; Session variables hold information about one single user, and are available to all pages in one application.

#### Start a PHP Session

A session is started with the session_start() function.

```php
// Start the session
session_start();

// Set session variables
$_SESSION["favcolor"] = "green";
$_SESSION["favanimal"] = "cat";
echo "Session variables are set.";

// Get PHP Session Variable Values
echo "Favorite color is " . $_SESSION["favcolor"] . ".<br>"; // Favorite color is yellow.
echo "Favorite animal is " . $_SESSION["favanimal"] . "."; // Favorite animal is cat.

// Modify a PHP Session Variable
$_SESSION["favcolor"] = "yellow";
print_r($_SESSION); // Array ( [favcolor] => yellow )

// Destroy a PHP Session
// remove all session variables
session_unset();

// destroy the session
session_destroy();
```

### Filters

#### The PHP Filter Extension

The filter_list() function can be used to list what the PHP filter extension offers

```php
<table>
  <tr>
    <td>Filter Name</td>
    <td>Filter ID</td>
  </tr>
  foreach (filter_list() as $id => $filter) {
    echo '<tr><td>' . $filter . '</td><td>' . filter_id($filter) . '</td></tr>';
  }
</table>
```

#### Why Use Filters?

Many web applications receive external input. External input/data can be

* User input from a form

* Cookies

* Web services data

* Server variables

* Database query results

#### filter_var() Function

The filter_var() function both validate and sanitize data.

##### Sanitize a String

The following example uses the filter_var() function to remove all HTML tags from a string

```php
$str = "<h1>Hello World!</h1>";
$newstr = filter_var($str, FILTER_SANITIZE_STRING);
echo $newstr; // Hello World!
```

##### Validate an Integer

```php
$int = 100;

if (!filter_var($int, FILTER_VALIDATE_INT) === false) {
  echo("Integer is valid");
} else {
  echo("Integer is not valid");
}
// Integer is valid
```

#### Validate an IP Address

```php
$ip = "127.0.0.1";

if (!filter_var($ip, FILTER_VALIDATE_IP) === false) {
  echo("$ip is a valid IP address");
} else {
  echo("$ip is not a valid IP address");
}
// 127.0.0.1 is a valid IP address
```

#### Sanitize and Validate an Email Address

```php
$email = "john.doe@example.com";

// Remove all illegal characters from email
$email = filter_var($email, FILTER_SANITIZE_EMAIL);

// Validate e-mail
if (!filter_var($email, FILTER_VALIDATE_EMAIL) === false) {
  echo("$email is a valid email address");
} else {
  echo("$email is not a valid email address");
}
// john.doe@example.com is a valid email address
```

#### Sanitize and Validate a URL

```php
$url = "https://www.jirimschools.com";

// Remove all illegal characters from a url
$url = filter_var($url, FILTER_SANITIZE_URL);

// Validate url
if (!filter_var($url, FILTER_VALIDATE_URL) === false) {
  echo("$url is a valid URL");
} else {
  echo("$url is not a valid URL");
}

// https://www.jirimschools.com is a valid URL
```

### Filters Advanced

#### Validate an Integer Within a Range

The following example uses the filter_var() function to check if a variable is both of type INT, and between 1 and 200

```php
$int = 122;
$min = 1;
$max = 200;

if (filter_var($int, FILTER_VALIDATE_INT, array("options" => array("min_range"=>$min, "max_range"=>$max))) === false) {
  echo("Variable value is not within the legal range");
} else {
  echo("Variable value is within the legal range");
} // false
```

#### Validate IPv6 Address

The following example uses the filter_var() function to check if the variable $ip is a valid IPv6 address

```php
$ip = "2001:0db8:85a3:08d3:1319:8a2e:0370:7334";

if (!filter_var($ip, FILTER_VALIDATE_IP, FILTER_FLAG_IPV6) === false) {
  echo("$ip is a valid IPv6 address");
} else {
  echo("$ip is not a valid IPv6 address");
} // true
```

#### Validate URL - Must Contain QueryString

The following example uses the filter_var() function to check if the variable $url is a URL with a querystring

```php
$url = "https://www.jirimschools.com";

if (!filter_var($url, FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED) === false) {
  echo("$url is a valid URL with a query string");
} else {
  echo("$url is not a valid URL with a query string");
} // true
```

#### Remove Characters With ASCII Value > 127

The following example uses the filter_var() function to sanitize a string. It will both remove all HTML tags, and all characters with ASCII value > 127, from the string

```php
$str = "<h1>Hello WorldÆØÅ!</h1>";

$newstr = filter_var($str, FILTER_SANITIZE_STRING, FILTER_FLAG_STRIP_HIGH);
echo $newstr; // Hello World!
```

### Callback Functions

A callback function (often referred to as just "callback") is a function which is passed as an argument into another function

Any existing function can be used as a callback function. To use a function as a callback function, pass a string containing the name of the function as the argument of another function

```php
function my_callback($item) {
  return strlen($item);
}

$strings = ["apple", "orange", "banana", "coconut"];
$lengths = array_map("my_callback", $strings);
print_r($lengths); // 5, 6, 6, 7

// Use an anonymous function as a callback for PHP's array_map() function
$strings = ["apple", "orange", "banana", "coconut"];
$lengths = array_map( function($item) { return strlen($item); } , $strings);
print_r($lengths); // 5, 6, 6, 7
```

#### Callbacks in User Defined Functions

```php
function exclaim($str) {
  return $str . "! ";
}

function ask($str) {
  return $str . "? ";
}

function printFormatted($str, $format) {
  // Calling the $format callback function
  echo $format($str);
}

// Pass "exclaim" and "ask" as callback functions to printFormatted()
printFormatted("Hello world", "exclaim"); // Hello world!
printFormatted("Hello world", "ask"); // Hello world?
```

### JSON

#### What is JSON?

JSON stands for JavaScript Object Notation, and is a syntax for storing and exchanging data.

Since the JSON format is a text-based format, it can easily be sent to and from a server, and used as a data format by any programming language.

First, we will look at the following two functions:

* json_encode()

* json_decode()

#### json_encode()

The json_encode() function is used to encode a value to JSON format.

```php
// Encode an associative array into a JSON object
$age = array("Peter"=>35, "Ben"=>37, "Joe"=>43);
echo json_encode($age); // {"Peter":35,"Ben":37,"Joe":43}

// Encode an indexed array into a JSON array
$cars = array("Volvo", "BMW", "Toyota");
echo json_encode($cars); // ["Volvo","BMW","Toyota"]
```

#### json_decode()

The json_decode() function is used to decode a JSON object into a PHP object or an associative array

```php
// Decodes JSON data into a PHP object
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
var_dump(json_decode($jsonobj)); // object(stdClass)#1 (3) { ["Peter"]=> int(35) ["Ben"]=> int(37) ["Joe"]=> int(43) }

// Decodes JSON data into a PHP associative array
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
var_dump(json_decode($jsonobj, true)); // array(3) { ["Peter"]=> int(35) ["Ben"]=> int(37) ["Joe"]=> int(43) }
```

#### Accessing the Decoded Values

Here are two examples of how to access the decoded values from an object and from an associative array:

```php
// Access the values from a PHP object
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
$obj = json_decode($jsonobj);

echo $obj->Peter; // 35
echo $obj->Ben; // 37
echo $obj->Joe; // 43

// Access the values from a PHP associative array
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
$arr = json_decode($jsonobj, true);

echo $arr["Peter"]; // 35
echo $arr["Ben"]; // 37
echo $arr["Joe"]; // 43
```

#### Looping Through the Values

```php
// Loop through the values of a PHP object
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
$obj = json_decode($jsonobj);

foreach($obj as $key => $value) {
  echo $key . " => " . $value . ", ";
} // Peter => 35, Ben => 37, Joe => 43

// Loop through the values of a PHP associative array
$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
$arr = json_decode($jsonobj, true);

foreach($arr as $key => $value) {
  echo $key . " => " . $value . ", ";
} // Peter => 35, Ben => 37, Joe => 43
```

### Exceptions

#### What is an Exception?

An exception is an object that describes an error or unexpected behaviour of a PHP script.

Exceptions are thrown by many PHP functions and classes.

#### Throwing an Exception

The throw statement allows a user defined function or method to throw an exception. When an exception is thrown, the code following it will not be executed.

```php
function divide($dividend, $divisor) {
  if($divisor == 0) {
    throw new Exception("Division by zero");
  }
  return $dividend / $divisor;
}

echo divide(5, 0);

/* result
Fatal error: Uncaught Exception: Division by zero in C:\webfolder\test.php:4
Stack trace: #0 C:\webfolder\test.php(9):
divide(5, 0) #1 {main} thrown in C:\webfolder\test.php on line 4
*/
```

#### The try...catch Statement

To avoid the error from the example above, we can use the try...catch statement to catch exceptions and continue the process.

```php
// Syntax
try {
  // code that can throw exceptions
} catch(Exception $e) {
  // code that runs when an exception is caught
}

// Example
function divide($dividend, $divisor) {
  if($divisor == 0) {
    throw new Exception("Division by zero");
  }
  return $dividend / $divisor;
}

try {
  echo divide(5, 0);
} catch(Exception $e) {
  echo "Unable to divide."; /// false
}
```

#### The try...catch...finally Statement

The try...catch...finally statement can be used to catch exceptions. Code in the finally block will always run regardless of whether an exception was caught. If finally is present, the catch block is optional.

```php
// Syntax
try {
  // code that can throw exceptions
} catch(Exception $e) {
  // code that runs when an exception is caught
} finally {
  // code that always runs regardless of whether an exception was caught
}

// Example
function divide($dividend, $divisor) {
  if($divisor == 0) {
    throw new Exception("Division by zero");
  }
  return $dividend / $divisor;
}

try {
  echo divide(5, 0);
} catch(Exception $e) {
  echo "Unable to divide. ";
} finally {
  echo "Process complete.";
}
// Results: Unable to divide. Process complete.
```

### OOP - Classes and Objects

#### Define a Class

A class is defined by using the class keyword, followed by the name of the class and a pair of curly braces ({}). All its properties and methods go inside the braces:

```php
class Fruit {
  // code goes here...
}
```

Below we declare a class named Fruit consisting of two properties ($name and $color) and two methods set_name() and get_name() for setting and getting the $name property:

```php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}
```

### Define Objects

Classes are nothing without objects! We can create multiple objects from a class. Each object has all the properties and methods defined in the class, but they will have different property values.

```php
class Fruit {
  // Properties
  public $name;
  public $color;

  // Methods
  function set_name($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}

$apple = new Fruit();
$banana = new Fruit();
$apple->set_name('Apple');
$banana->set_name('Banana');

echo $apple->get_name();
echo "<br>";
echo $banana->get_name();
```

### The $this Keyword

The $this keyword refers to the current object, and is only available inside methods.

```php
class Fruit {
  public $name;
  function set_name($name) {
    $this->name = $name;
  }
}
$apple = new Fruit();
$apple->set_name("Apple");

echo $apple->name;
```

### Instanceof

You can use the instanceof keyword to check if an object belongs to a specific class:

```php
$apple = new Fruit();
var_dump($apple instanceof Fruit);
```

### OOP - Constructor

#### The __construct Function

A constructor allows you to initialize an object's properties upon creation of the object.

If you create a __construct() function, PHP will automatically call this function when you create an object from a class.

```php
class Fruit {
  public $name;
  public $color;

  function __construct($name) {
    $this->name = $name;
  }
  function get_name() {
    return $this->name;
  }
}

$apple = new Fruit("Apple");
echo $apple->get_name();
```

### OOP - Destructor

#### The __destruct Function

A destructor is called when the object is destructed or the script is stopped or exited.

If you create a __destruct() function, PHP will automatically call this function at the end of the script.

```php
class Fruit {
  public $name;
  public $color;

  function __construct($name, $color) {
    $this->name = $name;
    $this->color = $color;
  }
  function __destruct() {
    echo "The fruit is {$this->name} and the color is {$this->color}.";
  }
}

$apple = new Fruit("Apple", "red");
```

### OOP - Access Modifiers

#### Access Modifiers

Properties and methods can have access modifiers which control where they can be accessed.

There are three access modifiers:

* public: The property or method can be accessed from everywhere. This is default

* private: The property or method can ONLY be accessed within the class

* protected: The property or method can be accessed within the class and by classes derived from that class

```php
// public
class Car {
    public $brand;

    public function setBrand($brand) {
        $this->brand = $brand;
    }

    public function getBrand() {
        return $this->brand;
    }
}

$car = new Car();
$car->setBrand("Toyota");
echo $car->getBrand();

// private
class Car {
    private $engineNumber;

    public function setEngineNumber($engineNumber) {
        $this->engineNumber = $engineNumber;
    }

    private function getEngineNumber() {
        return $this->engineNumber;
    }
}

$car = new Car();
$car->setEngineNumber("ABC123");
// $car->getEngineNumber(); // Lỗi: Không thể truy cập từ bên ngoài class

// protected
class Car {
    protected $fuelType;

    protected function setFuelType($fuelType) {
        $this->fuelType = $fuelType;
    }

    protected function getFuelType() {
        return $this->fuelType;
    }
}

class ElectricCar extends Car {
    public function setAndDisplayFuelType($fuelType) {
        $this->setFuelType($fuelType);
        echo $this->getFuelType();
    }
}

$electricCar = new ElectricCar();
$electricCar->setAndDisplayFuelType("Electric");
// $electricCar->getFuelType(); // Lỗi: Không thể truy cập từ bên ngoài class

```