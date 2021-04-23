# JavaScript

[<- Go Back](css.md)

## Definition
> JavaScript often abbreviated as JS, is a `high-level`, `interpreted` programming language. It is a language which is also characterized as `dynamic`, >  `weakly typed`, `prototype-based` and `multi-paradigm`. 

> As a `multi-paradigm` language, JavaScript supports `event-driven`, `functional`, and `imperative (including object-oriented and prototype-based)` > programming styles.

> `Initially only implemented client-side in web browsers`, JavaScript engines `are now embedded in many other types of host software, including server-side in web servers and databases`, and in non-web programs such as word processors and PDF software, and in runtime environments that make JavaScript viable for writing mobile and desktop applications, including desktop widgets.

```js
const person = {
  name: 'Nico',
  age: 38
}

const properties = Object.keys(person);

properties.forEach(function(property) {
  console.log(person[property]);
});
```

* This definition comes from [Wikipedia - JavaScript](https://en.wikipedia.org/wiki/JavaScript) document
* Over this course we'll try to figure out what this means and how it works
* By the end of the programing section we should be able to read this definition again and understand it

## JS History
* It's important to know the language's history to understand where it comes from and where it's going
* Read [auth0 - A brief history of JavaScript](https://auth0.com/blog/a-brief-history-of-javascript)
* Watch & Read [TXJS 2011 A6 – Brendan Eich – Ecma TC39: The Good, The Bad, and The Ugly.](https://brendaneich.com/2011/08/my-txjs-talk-twitter-remix)
* Watch [Tyler McGinnis - Computing Conversations with Brendan Eich](https://www.youtube.com/watch?v=IPxQ9kEaF8c)
* Watch [ECMAScript, TC39, and the History of JavaScript](https://www.youtube.com/watch?v=gytOcNFV1dM)
* Watch [How to fix the web | Brendan Eich | TEDxVienna](https://www.youtube.com/watch?v=zlcnOr81lPc)
* Watch [Brendan Eich on JavaScript at 17 - O'Reilly Fluent 2012](https://www.youtube.com/watch?v=Rj49rmc01Hs)
* Watch [ECMAScript Harmony: Rise of the Compilers - Brendan Eich keynote](https://www.youtube.com/watch?v=PlmsweSNhTw)

## JS Environments
* JavaScript now runs Client and Server side
* Using a Web Browser is one of the easiest way to execute JS Client side
* Using Node.js we can execute JS Server side
* JavaScript is no longer a scripting language to create interactive browser animations

### Client Side - Browser
* Open Chrome
* Open Devtools
* Select the console tab inside Devtools

![Devtools](./resources/images/js/show_devtools.png)

* Write the following code and press enter to execute it:

```javascript
2 + 2
```

```js
console.log(2 + 2);
```

![Devtools](./resources/images/js/devtools.png)

* Now run the following code:

```javascript
console.log('Congrats!!!, you just ran your first JS code');
```

### Node.js - Server Side

* [Node.js®](https://nodejs.org/) is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.
* It was created by [Ryan Dahl](https://wikipedia.org/wiki/Node.js) in 2009
* We'll use Node.js from now on to learn the language and run our JavaScript exercises
* Once we know the language core concepts we'll learn about the Browsers API's
* [Download & install Node.js](https://nodejs.org/en/download/)
* [Install Node.js & npm Windows](http://blog.teamtreehouse.com/install-node-js-npm-windows)

* After installing Node.js open a terminal window and run the following command:

```bash
node --version
v8.11.11
```

* Also check that you have npm installed too:

```bash
npm --version
5.6.0
```

* Now that we know that we have installed Node.js & npm we can use it
* Execute the following command:

```bash
node
>
```

* It looks like nothing happened but in reality we are executing Node.js JavaScript console
* The **>** symbol means that we opened the Node.js console and it's waiting for us to input JS code
* Now we can write JS code and execute it the same way we did using the browser
* This console is called `REPL("Read-Eval-Print-Loop")`

### Using Node.js REPL
* Open your terminal
* Execute the `node` command
* If you do not see the **>** symbol (and you are using Windows) try `winpty node` instead
* Write the following sentence once you see the **>** symbol:

```javascript
2 + 2
```
* Press the enter key to see the following result:

```javascript
> 2+2
4
>
```

* Press CTRL + C to quit
* You'll see the following message:

```bash
(To exit, press ^C again or type .exit)
```

* So you need to press CTRL + C twice to exit
* In this exercise we added two numbers and Node.js output the result
* It's nice to be able to try code using Node.js console but for longer programs it's better to use a JS files
* To execute a JS program we'll use the node command and the name of the file that we want to execute

```bash
node program.js
```

* Once we execute this command Node.js will read and interpretate our JS code
* We use the `.js` extension for our JavaScript code

### Using a Node.js file
* Create a folder with the name `js`
* Create a new file `index.js` inside the js folder
* Write the following code into the index.js file

```javascript
2 + 2
```

* Open the console and change directory to the `js` folder
* Execute the program using the node command:

```bash
node index.js
```

* Check out the output!!
* Don't worry if you don't see an output, Node.js executes our code but it's only adding both values together
* To show the result as output we need to use the `console.log()` object and method
* The `log()` method accepts any value to show as output
* Now add `console.log` and execute the program again

```js
console.log(2 + 2);
```

```bash
node index.js
```

* Now we see the expected output!!!

### Conclusion
* Browser and Node.js internaly use the V8 JavaScript engine to run JavaScript code
* We can use the Browser or Node.js console to try out JavaScript code
* V8 is maintained by Google
* We'll use browser to run JavaScript client side and Node.js for Server side

## Variables declaration & assignment operators

## Variables declaration

* Many times when coding we need to store a value to interact with it
* This value is stored in our computer memory
* As this values might change over time we'll call this memory position a `variable` 
* We can assign variables a `name` to identify them
* It's a good practice to use descriptive names to define our variables
* If we use names like a, b, foo they don't add any context about what we're coding
* We can then define that variables are named memory positions where we can assign different values and override them when needed

### ES5
* To define a variable in JavaScript we just need a variable name
* The variable statement **var** declares a variable, optionally initializing it to a value
* Also end each statement with `;`
* [MDN var doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)

**Example:**
```js
var variableName;
```

* For example we can define name and age variables to use in our program

**Example:**
```js
var name;
var age;
```

* Not using **var** is a bad coding practice
* To avoid  unexpected errors use var to declare your variables
* Variable names must start with a letter
* Use descriptive variable names to keep your code [smelling nice](https://en.wikipedia.org/wiki/Code_smell)
* In JavaScript it's common to use camel case to define variable names
* In camel case the first word is written in lower case and the rest of the words start with a capitalize letter

**Example:**
```js
var healthInsuranceNumber;
```

#### Practice
[Exercise 1](./exercises/js/ex_1.md)

## Assignment operator
* Once we defined a variable name we can assign a value
* As we have a memory space reserved we can store a value 
* The **=** assigns a value from right to left

**Example:**
```js
var name;
name = 'Pablo';
```

* We can define all the variables first and then assign the values:
* Variables in JS can be of different [types](https://www.w3schools.com/js/js_datatypes.asp)

**Example:**
```js
var name;
var age;
name = 'Pablo';
age = 20;
```

#### Practice
[Exercise 2](./exercises/js/ex_2.md)

* Also we can declare all variables using a single line:

**Example:**
```js
var name, age;
name = 'Pablo';
age = 20;
```

#### Practice
[Exercise 3](./exercises/js/ex_3.md)

* We can declare a variable and assign a value in the same line:
* Multiple assignment doesn't work in JavaScript (only one variable and one value)

**Example:**
```js
var name = 'Pablo';
var age = 20;
```

#### Practice
[Exercise 4](./exercises/js/ex_4.md)

* Using `console.log()` we can output the variable value

**Example: index.js (filename)**
```js
var name = 'Pablo';
var age = 20;
console.log(name);
console.log(age);
```

**Execute the program using node.js:**
```bash
node index.js
```

#### Practice
[Exercise 5](./exercises/js/ex_5.md)

* After executing the program we should see pablo & 20 as output
* `console.log()` accepts multiple comma separated values 
* We can show a message and the variable value

**Example: index.js (filename)**
```js
var name = 'Pablo';
var age = 20;
console.log('name: ', name);
console.log('age: ', age);
```

**Execute the program using node.js:**
```bash
node index.js
```

* Now our output looks like: **name: Pablo** and **age: 20**
* This is an easy way to debug our variable values

#### Practice
[Exercise 6](./exercises/js/ex_6.md)

### ES6
* In version 6 of the language we can use **let** to define variables
* This statement declares a **block scope local variable**, optionally initializing it to a value
* Using **let** will help us scope our variables in a better way
* [MDN let doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)

**Example:**
```js
let variable = value;
```

#### Practice
[Exercise 7](./exercises/js/ex_7.md)

* When the value of a variable is always the same we can define it as a **constant**
* In ES6 we can declare constants using the reserved word **const** 

**Example:**
```js
const constantVariable = value;
```

#### Practice
[Exercise 8](./exercises/js/ex_8.md)

* We'll get an error if we try to change a constant value

**Example:**
```js
const constantVariable = value;
constantVariable = otherValue;
// TypeError: Assignment to constant variable.
```

#### Practice
[Exercise 9](./exercises/js/ex_9.md)

### var vs let & const
* [Medium - Eric Elliot - JavaScript ES6 var, let or const](https://medium.com/javascript-scene/javascript-es6-var-let-or-const-ba58b8dcde75)
* [StackOverflow - Difference between using let and var](https://stackoverflow.com/questions/762011/whats-the-difference-between-using-let-and-var-to-declare-a-variable-in-jav)
* [JS Tips - Keyword var vs let](http://www.jstips.co/en/javascript/keyword-var-vs-let)

### Memory Management
* If you're wondering how JavaScript memory and variables work you can read the following guide to know more about it and JS Garbage collection
* [MDN Memory management doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management)

## Data types
* In JavaScript we can use different types of values to represent different things

  **Example:**
  ```js
  var name = 'Pablo';
  var age = 20;

  console.log('name: ', name);
  console.log('age: ', age);
  ```

* In this example we use different types of values:
  * For the name variable we use a value between quotes
  * For age we use a number

* JavaScript has the following different base types that we can use:
  * **string:** this type is used to represent textual data
  * **number:** there is only one number type the `double-precision 64-bit binary format IEEE 754 value`. There is no specific type for integers. In addition to being able to represent floating-point numbers, the number type has three symbolic values: +Infinity, -Infinity, and NaN (not-a-number)
  * **boolean:** represents a logical entity and can have two values: `true or false`
  * **undefined:** A variable that has not been assigned a value has the value `undefined`.
  * **null:** this type has exactly one value: `null`. It represents the intentional absence of any object value

* As programmers it's going to be our responsibility to choose the right data type for each variable depending the type of value that we need
* The operations that we'll be able to do are going to be related to the data type we choose
* There exists many more types of values in JavaScript (and we can even create our own) but these are the primitive ones
* A primitive (primitive value, primitive data type) is data that is not an object and has no methods
* [MDN primitive doc](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)
* [MDN data structures doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

### String
* String represents a text value, we can use them for names, last name, address, etc
* String values are enclosed between single or double quotes
* By default we use single quotes for strings but there are some special cases
* [MDN string doc](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

  **Example:**
  ```js
  let firstname = 'Juan';
  let lastname = "Perez";

  console.log(firstname);
  console.log(lastname);
  ```

* In this example we defined two variables (firstname and lastname) and assigned them string values ('Juan', 'Perez')
* We can also use this type of value for messages

  **Example:**
  ```js
  let message = 'Welcome to JavaScript!!!';
  console.log(message);
  ```

* We can use primitives without having them assigned to a variable

  **Example:**
  ```js
  console.log('Welcome to JavaScript!!!');
  ```

* In this example we use a literal **string** as `console.log()` parameter

#### Practice
[Exercise 10](./exercises/js/ex_10.md)

[Exercise 11](./exercises/js/ex_11.md)

### String concatenation
* The `+` operator allows us to concat two or more strings together

  **Example:**
  ```js
  let name = 'Juan';
  let space = ' ';
  let lastname = 'Perez';

  console.log(name + space + lastname);
  ```

* In this example we concat all values using the `+` operator
* We might not need to use a variable for the space and we can use a string literal instead

  **Example:**
  ```js
  let name = 'Juan';
  let lastname = 'Perez';

  console.log(name + ' ' + lastname);
  ```

* In this example we see how to use a literal value without being assigned to a variable

#### Practice
[Exercise 12](./exercises/js/ex_12.md)

[Exercise 13](./exercises/js/ex_13.md)

[Exercise 14](./exercises/js/ex_14.md)

### Template literals
* In ES6 we have `template literals` that will help us write better string templates
* To write a template literal we use **``** (back-tick)
* Then we use the following syntax to add template values `${variable}`
* Once the code gets executed the JavaScript engine will replace the variable value inside the string one
* Take a look at the following example to better understand this concept
* [MDN template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

  **Example:**
  ```js
  var name = 'Pedro';
  var template = `Welcome ${name} to this great site`

  console.log(template);
  ```

* In this example we defined a name variable and assigned the Pedro value
* Then we create a template variable with a message and the name variable
* Once we execute this code we'll get `Welcome Pedro to this great site`
* We can add all the variables that we need to a template
* Templates can be multiline

  **Example:**
  ```js
  let mom = 'Marta';
  let dad = 'Martín';
  let template = `My mother\'s name is ${mom} & my dad\'s name is ${dad}`;

  console.log(template);
  ```

* We'll get as result: My mother's name is Marta & my dad's name is Martín
* We will explain the backslash quote thing later ;)
* Using string concatenation we can get the same result

  **Example:**
  ```js
  let mom = 'Marta';
  let dad = 'Martín';
  let message = 'My mother\'s name is ' + mom + ' & my dad\'s name is ' + dad;

  console.log(message);
  ```

* We can get the same result using templates or string concat
* Using templates looks like an easier way to do it!!

#### Practice
[Exercise 15](./exercises/js/ex_15.md)

[Exercise 16](./exercises/js/ex_16.md)

[Exercise 17](./exercises/js/ex_17.md)

### Single or double quotes
* In JavaScript we can choose between single or double quotes
* There're some cases where we need to use one or the other

  **Example:**
  ```js
  let text = 'text using "double quotes"';
  let otherText = "text using 'simple quotes'";

  console.log(text);
  console.log(otherText);
  ```

* In this case single or double quotes are part of the value
* When using quotes as part of the value we have to choose between escaping the quotes or just using the quote type that is not part of the content:
  * Use double quotes if the text has single quote content
  * Use singe quotes if the text has double quote content

#### Practice
[Exercise 18](./exercises/js/ex_18.md)

[Exercise 19](./exercises/js/ex_19.md)

### Numbers
* JavaScript also supports number type
* This type of value doesn't use quotes

  **Example:**
  ```js
  let age = 38;
  let capacity = 50;

  console.log(age);
  console.log(capacity);
  ```

#### Practice
[Exercise 20](./exercises/js/ex_20.md)

[Exercise 21](./exercises/js/ex_21.md)

* A common mistake is to code numbers as strings

  **Example:**
  ```js
  let age = 38;
  let capacity = "50";
  ```

  > In this example we have two variables that it looks like we are assigning number values. 
  > Age has a number type and capacity has a string value with the representation of a number.
  > Having different types allows us to do different types of operations, for example we can add or subtract numbers but not strings

* We'll talk later about doing math using number type values

### Boolean
* This type of value only accepts `true or false` as value

  **Example:**
  ```js
  let on = true;
  let voted = false;
  let married = false;

  console.log(on);
  console.log(voted);
  console.log(married);
  ```

#### Practice
[Exercise 22](./exercises/js/ex_22.md)

### Undefined
* A variable that has not been assigned a value is of type **undefined**
* A method or statement also returns undefined if the variable that is being evaluated does not have an assigned value
* A function returns undefined if a value was not returned
* Also we can assign it as a value to a variable

  **Example:**
  ```js
  let variableWithoutDefinition = undefined;

  console.log(variableWithoutDefinition);
  ```

* We might need to assign **undefined** in some special cases

#### Practice
[Exercise 23](./exercises/js/ex_23.md)

### Null
* In JavaScript we also have a **null** value
* We can assign a variable a null value

  **Example:**
  ```js
  let nullVariable = null;

  console.log(nullVariable);
  ```

#### Practice
[Exercise 24](./exercises/js/ex_24.md)

* At the beginning **null** & **undefined** look similar but they are different
* We can assign a null value and know that the variable has been defined but it has no value

### typeof
* The **typeof** operator returns a string indicating the type of the unevaluated operand

  **Example:**
  ```js
  let name = 'Marta';
  let age = 30;
  let married = false;
  let undefinedVar = undefined;
  let nullVar = null;

  console.log(typeof name); // string
  console.log(typeof age); // number
  console.log(typeof married); // boolean
  console.log(typeof undefinedVar); // undefined
  console.log(typeof nullVar); // object
  ```

* In this example we can see that typeof will return different values for different data types
* For **null** it will return `object`! Now that was unexpected...
* Object is a different type of JavaScript data value and we'll talk more about it in a different section

#### Practice
[Exercise 25](./exercises/js/ex_25.md)

[Exercise 26](./exercises/js/ex_26.md)