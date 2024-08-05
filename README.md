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