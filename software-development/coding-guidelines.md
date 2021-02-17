---
Title: Coding guidelines
Description: Javascript coding guidelines
Date: 2020-03-19T13:27:24.414Z
References: 
Tags: #javascript
---

# Javascript Coding Guidelines
Javascript is a very flexible language which gives you as a developer a lot of freedom. this freedom makes JavaScript fun to develop with, however this also means that as a developer you must know what you are doing, and how JavaScript behaves differently compared to other languages like C#. To avoid unexpected issues, and to help you write the best code, keep in mind the following coding guidelines

## Language features

### Use const and let (ES6)
With ES6, declare all local variables with either const or let. Use const by default, unless a variable needs to be reassigned. The **var** keyword must **not** be used. 

### Array
**Do not use the variadic Array constructor.**

<span style="color:red">Illegal:</span>
```javascript
 const a1 = new Array(x1, x2, x3);
 const a2 = new Array();
``` 
<span style="color:forestgreen">Correct:</span>
```javascript
	const a1 = [x1,x2,x3];
  const a2 = [];
```
#### Array properties
Do not define or use non-numeric properties on an array (other than *length*). Use a Map (ES6) instead.

## If statements
### Truthy vs falsy
It is not required to check on a boolean condition, for example it is possible to use: if(array.length) instead of if(array.length > 0). The if block will execute if the condition is truthy. Since 0 is equal to false.

A truthy value is a value that is considered *true* when evaluated in a Boolean context. All values are truthy unless they are defined as falsy.

examples of thruty values:
```javascript
	if (true)
  if ({})
  if ([])
  if (42)
  if (-42)
  if (3.14)
  if (-3.14)
  if ("foo")
  if (new date())
  if (Infinity)
  if (-Infinity)
```

Falsy values:
```javascript
	if (false)
  if (null)
  if (undefined)
  if (0)
  if (NaN)
  if ('')
```

### For loops
With ES6, the language now has three different kinds of for loops. All may be used, though for-of loops should be preferred when possible. 

for-in loops may only be used on dict-style objects, and should not be used to iterate over an array. Object.prototype.hasOwnProperty should be used in for-in loops to exclude unwanted prototype properties. Prefer for-of and Object.keys over for-in when possible. 

### Switch statements
#### Fall-through: commented
Within a switch block, each statement group either terminates abruptly (with a break, return or thrown exception), or is marked with a comment to indicate that execution will or might continue into the next statement group. Any comment that communicates the idea of fall-through is sufficient (typically // fall through). This special comment is not required in the last statement group of the switch block. 

Example:
```javascript
	switch (input) {
  	case 1:
    case 2:
    	prepareOneOrTwo();
      // fall through
    case 3:
    	handleOneTwoOrThree();
      break;
   	default:
    	handleLargeNumber()
  }
```

### Disallowed features
#### With
Do not use the with keyword. It makes your code harder to understand has been banned in strict mode since ES5. 
#### Dynamic code evaluation
Do not use eval or the Function(...string) constructor. These features are potentially dangerous and simply do not work in CSO evironments. 

### Exceptions
Exceptions are an important part of the language and should be used whenever exceptional cases occur. Always throw *Errors* or subclasses of Error: never throw string literals or other objects. Always use new when constructing an Error. 

Custom exceptions provide	a great way to convey additional error information from functions. They should be defined and used wherever the native Error type is insufficient. Prefer throwing exceptions over ad-hoc error-handling approaches (such as passing an error container reference type, or returning an object with an error property). 

## Naming
### Code
* Use *lowerCamelCase* for method names, field names, parameter names and local variable names. All private and protected variables and methods should start with an underscore. 
* For class names, interface names, record names, typedef names and enum names: use UpperCaseCamel
* For constants: use ALL_UPPER_CASE
* Public properties on which can be subscribed should end with a $.
* Class names for services, components, modules should end with *Service, *Component, *Module

### Folders
Folder names should always be *kebab-case*. For folders that contain a component, the name should be the same as the component it contains. 
### Files
File names should always be UpperCaseCamel
some files have a separate suffix, stating their type:
  * components: *.component.ts
  * services: *.services.ts
  * modules: *.modules.ts

## Files
### Source file
JavaScript file names (.js) must be all lowercase and may include underscore (_) or dashes (-). Do not uses spaces. Encoding should be UTF-8.
  
## Documentation
Document methods, fields, and classes, in the JSDoc style (especially when expsoing public methods and fields towards other components). The JSDoc style is supported in Visual Studio 2015 (and higher) to provide IntelliSense in JavaScript files.

#### More information
* [http://usejsdoc.org/](http://usejsdoc.org)
* [https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense)
* [https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-Javascript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-Javascript)

## Dangerous situations

### Always use strict equality
JavaScript is a loosely-typed language. When comparing values using (==) and (!=), the equality operator converts the operands if they are not of the same type.

For example:
```javascript
	1 === 1 // true
	'5' ==  5 // true
  0 == false // true
  0 == null // false
```
This can be dangerous as something might be equal after the conversion while this was not expected, and this conversion also reduces the performance. 

Thefore always us strict equality === and strict inequality !==.

### Difference between null and undefined
A variable is said to be undefined if it has been declared, but no value has been given to it. contrary to this, null is a value that can be assigned to a variable and represents "no value". Therefore, *undefined* is a variable type whereas null is an object value. 

In JavaScript, null is an object!

```javascript
	console.log(5 + null) // 5
  console.log(5+ undefined) // NaN
  
  console.log(null == undefined) // true
  console.log(null === undefined) // false!!
  
  var var1;
  console.log(var1); // undefined
  console.log(typeof var1); // undefined
  
  var var2 = null
  console.log(var2) // null
  console.log(typeof var2) // object!
  if (typeof var2 === 'object) {
   // is truthy when var2 is null!!
  }
```

### Always use isNan() when checking on NaN
when converting a string to a number using parseInt, the result will be NaN (Not a Number) in case the conversion fails. So it is important to check for NaN:

```javascript
var number = parseInt('??', 10);
console.log(number); // false!!
console.log(number == NaN); // false!!
console.log(isNan(number)) // true
```

<span style="color:red">Illegal:</span>
```javascript
	if (number === NaN) // false
```

<span style="color:forestgreen">Correct:</span>
```javascript
	if (isNaN(number)) // true
```

### Careful when using the TouchAPI
By default Microsoft Edge does not make use of the Touch API, so the TouchEvent interface is not recognized in Edge.

Do **not** do this:
```javascript
	if (e instanceof TouchEvent) // breaks
  	// touch handle
  else
  	// Mouse handle
```
instead:
```javascript
	if (e instanceof MouseEvent)
  	// Mouse handle
  else
  	// Touch handle
```
<br/>





