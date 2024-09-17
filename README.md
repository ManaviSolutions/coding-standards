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

    //
    //  A public variable
    //
    $m_publicVariable;
  
    //
    // Can use $mp_ also
    //
    private $m_privateVariable;
  
    //
    //  Example for static variables within a class
    //
    static public $variableName;
    static private $ms_variableName;
  
    function bar() {
  
        //
        //  @NOTE: This is not same as self::$variableName which is static and
        //  should be called in a static function
        //
        $variableName  = null;
  
    }

}
```

It is absolutely OK to use simple variables such as ```$i, $j, $k``` in the context of loops and other logical blocks if it is clear how it is used and does not cause conflict. It is still recommended to be used sparingly and only when necessary.

## Function & Class Guidelines
```PHP
//
//  The best way to show the guidelines is  to show it in the context of a 
//  function. When declaring functions the name should follow the standard
//  guideline provided, which is to use camel notation.
//
//  Also, following the standard guideline the opening { should be in line
//  with the function declaration. If the function uses parameters the ( )
//  needs to be padded with \s(space), and a \s(space) between each of the
//  parameters.
//
//  Finally, there should be a  line space after the opening { and closing
//  }, while ensuring the } is inline with the function
//
function someFunctionName( $arg1, $arg2 ) {

    //
    //  Notice the space above and below this section
    //  
    ...

}
```

When declaring functions within classes the standard guideline for functions is used except in cases where ```private/protected``` member functions are defined. In this case a prefix of ```_``` is added to the function name. Also, in some limited cases inline function can be declared and implemented in a single line.
```PHP
class foo {

    private $m_someVariable;
  
    //
    //  Some inline functions are also allowed in classes where the function
    //  body is no more than a single line,  and it is not using any complex
    //  logic that would require the function to be expanded
    //
    function getSomething() { return $m_someVariable; }
  
    function normalFunction() {
  
        ...
    
    }
  
    //
    //  Notice the _ in the name
    //
    private function _someFunctionName() {
  
        ...
  
    }

}
```

## Assignment Alignment
The assignment alignment guidelines may seem a bit complicated, but in reality the goal is to be able to easily see blocks of similar code that perform assignments - or change a variable. This can be for variables, arrays, and other sections in the code where providing a similar spacing for all lines of code in the block would allow the developer's eye to see the common pattern. In this section we will look at some guideline, but it will not be considered a hard rule as the spacing and alignment can change depending on the context of the code.  Generally the alignment happens within a ```{}``` or ```[]``` section.

### Variables
For variables the goal is to show the change and assignment. This is demonstrated in the code below
```PHP
function foo() {

    //
    //  These variables' = is aligned with the = 'b' assignment
    //
    $someVariable1        = 0;
    $someVariable2        = '';
    $someVairable3        = '';
  
    //
    //  Also pay attention to the {} alignment for the if statement
    //  where the closing } aligns with the opening if
    //
    if ( ... ) {
  
        //
        //  This variable's = is aligned with the = 'b' assignment
        //
        $someVariable1      = 1;
    
        while ( ... ) {
    
            if ( ... ) {
      
                $someVariable2  = 'b'
      
            }    
      
            //
            //  This variable's = is aligned with the = 'b' assignment
            //
            $someVariable3    = 'a';
    
        }
  
    }

}
```

arrays and functions
- Tertiary operators should be aligned within a logical block
  ```PHP
  //
  //  Notice how the ? and : align in each line
  //
  $a = $var === 1        ? true            : false;
  $b = $longerVar === 2  ? "result found"  : "error"; 
  ```
