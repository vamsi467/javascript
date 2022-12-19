---
title: Javascript OOPS
layout: template
filename: regex.md
--- 

What is RegExp?
------------------------
A regular expression is an object that describes a pattern of characters.

When you search in a text, you can use a pattern to describe what you are searching for.

A simple pattern can be one single character.

A more complicated pattern can consist of more characters, and can be used for parsing, format checking, substitution and more.

Regular expressions are used to perform powerful pattern-matching and "search-and-replace" functions on text


Syntax
-----------
```javascript
var patt=new RegExp(pattern,modifiers);

or 

var patt=/pattern/modifiers;

```
  *pattern specifies the pattern of an expression
  *modifiers specify if a search should be global, case-sensitive, etc.

RegExp Modifiers
-----------------------
Modifiers are used to perform case-insensitive and global searches.

The i modifier is used to perform case-insensitive matching.

The g modifier is used to perform a global match (find all matches rather than stopping after the first match).

the modifier m is used to Perform multiline matching. 

/-start and end of expression.
^ and $ represent start and end of line.
\d-single digit.

eg: var pattern=/^\d$/;-it would only match one character string containing a number from 0 to 9.
  
var pattern=/^\d{3}$/;---- represent 3 matching nos

To write a patter for this 999-999-9999

var pattern=/^\d{3}-\d{3}-\d{4}$/;
Brackets
-----------
Brackets are used to find a range of characters:

Expression 	Description 
--------------------------------------------------------------------------------
[abc] 		Find any character between the brackets 
[^abc] 		Find any character not between the brackets 
[0-9] 		Find any digit from 0 to 9 
[A-Z] 		Find any character from uppercase A to uppercase Z 
[a-z] 		Find any character from lowercase a to lowercase z 
[A-z] 		Find any character from uppercase A to lowercase z 
[adgk] 		Find any character in the given set 
[^adgk] 		Find any character outside the given set 
(red|blue|green) 	Find any of the alternatives specified 

Metacharacters
===========
	Metacharacters are characters with a special meaning

Metacharacter 		Description 
----------------------------------------------------------------------------------------------------------------
. 			Find a single character, except newline or line terminator 
\w 			Find a word character 
\W 			Find a non-word character 
\d 			Find a digit 
\D 			Find a non-digit character 
\s			Find a whitespace character 
\S 			Find a non-whitespace character 
\b 			Find a match at the beginning/end of a word 
\B 			Find a match not at the beginning/end of a word 
\0 			Find a NUL character 
\n 			Find a new line character 
\f 			Find a form feed character 
\r			Find a carriage return character 
\t 			Find a tab character 
\v 			Find a vertical tab character 
\xxx 			Find the character specified by an octal number xxx 
\xdd 			Find the character specified by a hexadecimal number dd 
\uxxxx 			Find the Unicode character specified by a hexadecimal number xxxx 


Quantifiers

Quantifier 			Description 
--------------------------------------------------------------
n+ 			Matches any string that contains at least one n 
n* 			Matches any string that contains zero or more occurrences of n 
n? 			Matches any string that contains zero or one occurrences of n 
n{X} 			Matches any string that contains a sequence of X n's 
n{X,Y} 			Matches any string that contains a sequence of X to Y n's 
n{X,} 			Matches any string that contains a sequence of at least X n's 
n$ 			Matches any string with n at the end of it 
^n			Matches any string with n at the beginning of it 
?=n 			Matches any string that is followed by a specific string n 
?!n 			Matches any string that is not followed by a specific string n 

RegExp Object Properties
---------------------------------
Property 			Description 
----------------------------------------------------------------------------------
global 			Specifies if the "g" modifier is set 
ignoreCase 		Specifies if the "i" modifier is set 
lastIndex 			The index at which to start the next match 
multiline 			Specifies if the "m" modifier is set 


RegExp Object Methods
=================
Method 			Description 
===============================
exec() 	Tests for a match in a string. Returns the first match 
test() 	Tests for a match in a string. Returns true or false 




Examples1
-------------
```html
<!DOCTYPE html>
<html>
<body>

<script>
var str = "Welcome to TechMahindra";
var patt1 = /Techmahindra/i;
document.write(str.match(patt1));
</script>

</body>
</html>
```

Example 2
--------------
<!DOCTYPE html>
<html>
<body>

<script>

var str="ALL is Well and is good to see you hear?";
var patt1=/is/g;
document.write(str.match(patt1));

</script>

</body>
</html>


Example 3
-------------
<html>
<SCRIPT LANGUAGE='JavaScript'>
<!--
    var str = "A BC 5 DEF 135 Abc.<BR>"

    var span3to5 = new RegExp("[3-5]","g");
    document.write(str);
    document.write("Replace digits 3 to 5 with nines.<BR>");
    document.write(str.replace(span3to5,"9"));
    //-->
</SCRIPT>
</html>

Methods used in RegularExpression
----------------------------------------------
test()
====
  -The test() method searches a string for a specified value, and returns true or false, depending on the result.

Example 4
========
<!DOCTYPE html>
<html>
<body>

<script>
var patt1=new RegExp("e");

document.write(patt1.test("The best thing in my life is childhood"));
</script>

</body>
</html>

Output:Since there is an "e" in the string, the output of the code above will be:

true will be printed.


exec()
=====
The exec() method searches a string for a specified value, and returns the text of the found value. If no match is found, it returns null.

Example 5
========
<!DOCTYPE html>
<html>
<body>

<script>
var patt1=new RegExp("e");

document.write(patt1.test("The best thing in my life is childhood"));
</script>

</body>
</html>


replace()
======

Example 6
=======
<html>
<SCRIPT LANGUAGE='JavaScript'>
<!--
    var str = "A BC 5 DEF 135 Abc.<BR>"

    var span3to5 = new RegExp("[3-5]","g");
    document.write(str);
    document.write("Replace digits 3 to 5 with nines.<BR>");
    document.write(str.replace(span3to5,"9"));
    //-->
</SCRIPT>
</html>
 


match(regExpObj) 		Searches for regExpObj pattern in string and returns result. 
replace(reqExpObj,str) 	Replaces all occurrences of the regExpObj pattern with str. 
search(reqExpObj) 		Returns the position of matching regExpObj pattern within the string. 
split(regExpObj,max) 	Splits string everywhere there is a matching regExpObj pattern up to max splits. The substrings are returned in an array. 
 

example
	Check whether the given string is Numeric or not.

Regular expression  /^[0-9]+$/ is used to find a string is numeric. In this

� [0-9] � represents numeric digits only allowed.
� + � matches any number of characters.
� ^ � matches beginning of the line
� $ � matches end of the line

Sample code
----------------
function isNumeric(input)
{
var regexp = /^[0-9]+$/;
if(regexp .test(input))
{
return true;
}
return false;
}

Example 2: Replace all occurrences of a string with substring
------------------------------------------------------------------------------
Suppose if you want to replace all hypen (-) characters with space in input string s = �12-November-2008?
Below code will replace it.

replace - method used to search and replace for a matching string with substring.

regular expression:  /-/g

/- matches the string hypen(-)
/g � matches all occurrences of the string.

var s = �12-November-2008?;
s = s.replace(/-/g,� �);

output : �12 November 2008?





====================================END============================
