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
- Within ```()``` a single \s(space) must be used pad around parameters, and a space after each ```,``` separator ```( a, b, c )```
- Within ```[]``` for Array access
  - No spacing is added when accessing an index with standard data types such as string or integer ```["index"] or [0]```
  - Space is padded when accessing via a variable or function ```[ $i ]```
- There must be a space added before operators and opening ```(``` such as ```if (``` or ```foreach (```
- ```String``` concatnation should use \s(space) between each segment and operator
- Tertiary operators should be aligned within a logical block
  ```PHP
  //
  //  Notice how the ? and : align in each line
  //
  $a = $var === 1        ? true            : false;
  $b = $longerVar === 2  ? "result found"  : "error"; 
  ```
- All opening ```{``` and ```[``` should start within the line called ```function foo() {``` or ```$array = [```
- 

## Variable
global
define
member
  public
  private
OK to use $i, $j

## Function
general
class functions
  general
  private

## Assignment Alignment
variables
arrays and functions
