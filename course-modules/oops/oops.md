

Object Oriented Programming in JavaScript
==============================

Introduction
=============

1. Class: Defines the characteristics of the Object.
2. Constructor: A method called at the moment of instantiation.
3. Object: An Instance of a Class.
4. Method: An Object capability as walk.
5. Property: An Object characteristic, such as color.
6. Inheritance: A Class can inherit characteristics from another Class.
7. Encapsulation: A Class defines only the characteristics of the Object, a method defines only how the method executes.
8. Abstraction: The conjunction of complex inheritance, methods, properties of an Object must be able to simulate a reality model.
9. Polymorphism: Different Classes might define the same method or property.

What is Class in JavaScript?
===============
JavaScript does not contains class statement. JavaScript is a prototype-based language. JavaScript uses functions as classes. Defining a class is as easy as defining a function. In the example below we define a new class called Car.

```js
// Define the class Car 

	function Car() { } 
```

EXAMPLE

```js
function Box(){
	this.length=10;
	this.breadth=20;
	this.display= function display()
	{
		console.log("Iam inside a display method");
	}
};

var box1 = new Box();
console.log(box1.length);
console.log(box1.display());
```
Here 
Box is a **class**,
length and breadth are **property/variables** of Box class
display is a **method** of box class 
box1 is an **object**

Note: There is no keyword called as class in javascript same function keyword is used for class.
=========================================================================================

2.What is Object?

Objects are created by using the new keyword followed by the name of the class.
 
Syntax:
	var objectname=new objectname([arguments]);

Example
	 Creating an instance of String object:

	var StringObject1 = new String("Hello"); 


This statement creates an instance of StringObject1 and passes it the literal "Hello" .

 
The parentheses aren't required when the constructor doesn't require arguments, so these two lines could be rewritten as follows:
 
var oObject = new Object;
var oStringObject = new String; 


sample demo
=========
function Car() { } 

  var car1 = new Car(); 
  var car2 = new Car(); 
 

Dereferencing Objects
===============
JavaScript has a garbage collection routine.
 
When there are no remaining references to an object, the object is said to be dereferenced.
 
It is possible to forcibly dereference objects by setting all its references equal to null.
 
var oObject = new Object;

oObject = null; 
 

Native Objects(Some basic objects)
==========================
Object          Function      Array         String
Boolean       Number       Date           RegExp


3.Prototype Property
================
	Used to add object properties and methods to your classes.

Example:
======
<!--Prototype Proprty-->
<html>
<head>
<script type="text/javascript">
<!--function Gadget() which uses this to add two properties and one method to the objects it creates.-->

function Gadget(name, color) {
this.name = name;
this.color = color;
this.whatAreYou = function(){
return 'I am a ' + this.color + ' ' + this.name;


<!--Let's add two more properties, price and rating, and a getInfo() method. Since prototype contains an object, you can just keep adding to it like this:-->
Gadget.prototype.price = 100;
Gadget.prototype.rating = 3;

//add a method to your class

Gadget.prototype.getInfo = function() {
return 'Rating: ' + this.rating + ', price: ' + this.price;
};
}
}

<!--All the methods and properties you have added to the prototype are directly available as soon as you create a new object using the constructor. If you create a newtoy object using the Gadget() constructor, you can access all the methods and properties already defined.
-->
var newtoy = new Gadget('webcam', 'black');
alert(newtoy.name);
alert(newtoy.WhatAreYou());
alert(newtoy.price);
alert(newtoy.rating);
alert(newtoy.getInfo());
</script>
<body>
</body>
</html>

<!--Here factory is a function>



What is method?
A method is essentially a function that is found inside of an object.

Eg:
var current=new Date()   //the current date
var min=current.getMinutes()


Here getMinutes() is a method associated with objects.


Constructor functions
===============

There is another way to create objects: by using constructor functions.
 Let's see an example:
		function Hero() {
			this.occupation = 'Ninja';
		}

In order to create an object using this function, you use the new operator, like this:
		 var hero = new Hero();
		 hero.occupation;

Output:Ninja

Benefits of Constructor
------------------------------
=> The benefit of using constructor functions is that they accept parameters, which can be used when creating new objects. 

Let's modify the constructor to accept one parameter and assign it to the name property.

function Hero(name) {
	this.name = name;//This refers to global object
	this.occupation = 'Ninja';
	this.whoAreYou = function() {
		return "I'm " + this.name + " and I'm a " + this.occupation;
	}
}
Now you can create different objects using the same constructor:

		 var h1 = new Hero('Michelangelo');
 		 var h2 = new Hero('Donatello');
		 h1.whoAreYou();
		 h2.whoAreYou();
Output:
	I'm Michelangelo and I'm a Ninja"
 	"I'm Donatello and I'm a Ninja"


Note
====
A class name is the name of the constructor.
 
A constructor 'acts as' a factory function.
 
No object is created inside the constructor.
 
this keyword is used in constructor.
 
When a constructor is called with the new operator, an object is created before the first line of the constructor.
 
Constructors create a separate copy for each object.

Example:
======
<html>
<head>
<title>Constructor Example</title>
</head>
<body>
<script type="text/javascript">
function Car(sColor, iDoors, iMpg) {
    this.color = sColor;
    this.doors = iDoors;
    this.mpg = iMpg;
    this.showColor = function () {
        alert(this.color)
    };
}

var oCar1 = new Car("red", 4, 23);
var oCar2 = new Car("blue", 3, 25);
oCar1.showColor();
oCar2.showColor();


</script>

</body>
</html>


//Adding method to a class using prototype

<HTML>
<HEAD>
<TITLE>Instance method demo</TITLE>
</HEAD>
   <BODY>
   <H1>
   <SCRIPT>
   // constructor function
   function Rectangle(height, width){
      this.height =  height;
      this.width = width;
   }
  
   function getArea () {
      return this.height * this.width;
   }
   // turn the function into an object method
   Rectangle.prototype.calcArea = getArea;

   var theRectangle = new Rectangle (3, 5);
   theRectangle.width = 10;

   document.write("The rectangle instance height is: " + theRectangle.height + "<br>");
   document.write("The rectangle instance width is: " + theRectangle.width  + "<br>");
   document.write ("The calcArea method returns: " + theRectangle.calcArea());
   </SCRIPT>
   </H1>
   </BODY>
</HTML>

Functions
-------------

The following three ways of defining a function

1st method
--------------
 	
	function sum(a, b) {return a + b;};
	sum(1, 2);

Output 3

2nd Method
---------------
	 var sum = function(a, b) {return a + b;};
	sum(1, 2);

Output 3

3rd method
---------------

	var sum = new Function('a', 'b', 'return a + b;');
	 sum(1, 2)
 
inheritence in JavaScript
================
(inheritanceDemo.html)


prototype chaining
=============
	Prototype chaining is the default way to implement inheritance.


<script>
//parent class
function pclass(){
this.parent_property1= "TechMahindra";
this.parent_method1=function parent_method1(arg1)
{
return arg1+"parent method data";
};
}


//establish child class
function Cclass(){
this.child_property1="TechMahindra";
this.child_method1=function child_method1(arg1)
{
return arg1+"child method data";
};
}

//make child to inherit parent class
Cclass.prototype=new pclass();
var instance1=new Cclass();
alert(instance1 instanceof pclass);
alert(instance1 instanceof Cclass);

alert(instance1.parent_method1("Result"));

</script>

Demo 2(6_inheritance)
=====
<!--inheritence in javascript -->
<html>
<head>
<script type="text/javascript">
function Shape(){}

// augment prototype
Shape.prototype.name = 'shape';
Shape.prototype.toString = function() {return this.name;};

function TwoDShape(){}

// take care of inheritance
TwoDShape.prototype = new Shape();
TwoDShape.prototype.constructor = TwoDShape;

// augment prototype
TwoDShape.prototype.name = '2D shape';

function Triangle(side, height) {
this.side = side;
this.height = height;
}
// take care of inheritance
Triangle.prototype = new TwoDShape();
Triangle.prototype.constructor = Triangle;

// augment prototype
Triangle.prototype.name = 'Triangle';
Triangle.prototype.getArea = function(){return this.side * this.height / 2;};

var my = new Triangle(5, 10);
alert(my.getArea());

</script>
<body>

</body>
</html>

Inheriting the Prototype Only
====================
It is probably a good idea to inherit only the prototype, because all the reusable code is there. This means that inheriting the object contained in Shape.prototype is better than inheriting the object created with new Shape(). After all, new Shape() will only give you own shape properties which are not meant to be reused (otherwise they would be in the prototype). You gain a little more efficiency by:

Not creating a new object for the sake of inheritance alone, and
Having less lookups during runtime when it comes to searching for toString() for example.


function Shape(){}
// augment prototype
Shape.prototype.name = 'shape';
Shape.prototype.toString = function() {return this.name;};
function TwoDShape(){}
// take care of inheritance

TwoDShape.prototype = Shape.prototype;//using prototype

TwoDShape.prototype.constructor = TwoDShape;
// augment prototype
TwoDShape.prototype.name = '2D shape';
function Triangle(side, height) {
this.side = side;
this.height = height;
}
// take care of inheritance

Triangle.prototype = TwoDShape.prototype;//using prototype

Triangle.prototype.constructor = Triangle;
// augment prototype
Triangle.prototype.name = 'Triangle';
Triangle.prototype.getArea = function(){return this.side * this.height / 2;}