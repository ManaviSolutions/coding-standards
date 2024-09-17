# coding-standards
This coding standard guideline is established to be used for all Manavi Solution repositories.

## Commenting Guidelines
```PHP
//
//  For all commenting there is an extra // added to the top and bottom of
//  comment content. The first letter of each new line is capitalized, and
//  the space between // and the text for each line must be with a \t(tab)
//
//  Also, notice how the comment block is justified. The text in a comment
//  block needs to be edited and adjusted as needed to be justified.  Also
//  the length of the lines should be kept to a size that does not require
//  scrolling to be able to view the full comment block
//
```
The use of ```@TODO:``` in a comment block can be used to identify code sections pending changes.

The use of ```@NOTE:``` in a comment block can be used to identify special cases - not very common.

In some instances, adding a comment block on a logical section that has shown to change multiple times in the past is recommended.
```PHP
//
//  This is a comment for peice of code that has some logic that changes alot
//
//  2024-01-01 - Bob Manavi - A change was made to this logic to ...
//
```

## General Guidelines
- All spacing used for lines must be with \t(tab)
- Camel notation should be used for all variable and function names
- Within ```()``` a single \s(space) must be used pad around parameters, and a space after each ```,``` separator ```( a, b, c )```
- Within ```[]``` for Array access
  - No spacing is added when accessing an index with standard data types such as string or integer ```["index"] or [0]```
  - Space is padded when accessing via a variable or function ```[ $i ]```
- There must be a space added before operators and opening ```(``` such as ```if (``` or ```foreach (```
- ```String``` concatnation should use \s(space) between each segment and operator
- All opening ```{``` and ```[``` should start within the line called ```function foo() {``` or ```$array = [```

## Variable Guidelines
Following the general guidelines, all variables should be declared using camel case notation. In this case all variables are written in lowercase and if the variable has more than one word in its name then each word following the first word will have its first letter written in upper case.
```PHP
$var      = true;
$varName  = false;
```
### Variable Scope
The scope of a variable will determine certain prefixes and notation for a given variable name:
- **Global** - Generally global variables are considered to be unaceptable in the code, but in some cases they are a necessary evil, so in these instances a global variable can be declared using the ```$g_```
- **Define** - It is strongly recommended for ```define()``` to be used instead of global variables when possible, and if necessary. In this case, defines should use all CAP letters and _ for spacing between words
- **Local** - Local variable definitions should follow the standard guideline and simply be in camel case notation
- **Member** - Member variables or class member variables are variables defined within the scope of a class.
  - **Public** - In this case the prefix ```$m_``` is required
  - **Private** - (Optional) For private members the prefix ```$mp_``` can be used
  - **Static** - Static members should use the prefix ```$ms_``` on private members and no prefix on public members

```PHP
//
//  Example of a global variable
//
$g_variableName    = null;

//
//  Prefered method to using global variables
//
define( "GLOBAL_VAR", null );

//
//  Using a class example to demonstrate all cases for local and member
//
class foo() {

  $m_publicVariable;

  private $m_privateVariable;

  static public $variableName;
  static private $ms_variableName;

  function bar() {

    //
    //  @NOTE: This is not same as self::$variableName which is static and
    //  should be called in a static function
    //
    $variableName;

  }

}
```

It is absolutely OK to use simple variables such as ```$i, $j, $k``` in the context of loops and other logical blocks if it is clear how it is used and does not cause conflict. It is still recommended to be used sparingly and only when necessary.

## Class & Function Guidelines
general
class functions
  general
  private

## Assignment Alignment
variables
arrays and functions
- Tertiary operators should be aligned within a logical block
  ```PHP
  //
  //  Notice how the ? and : align in each line
  //
  $a = $var === 1        ? true            : false;
  $b = $longerVar === 2  ? "result found"  : "error"; 
  ```
