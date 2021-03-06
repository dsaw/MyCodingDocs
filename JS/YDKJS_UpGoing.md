
## YDKJS 
* Up & Going - Part 1
  * Try it yourself - Start a blank browser tab and open developer console. This plain console is where the Javaascript code is run.
  * Javascript is commonly called an interpreted language but it is not entirely accurate. Javascript engine makes use of a JIT compiler that will run compiled code *on the fly*.
  * To output on the console, type out `console.log(msg)`
  * To generate alert boxes, type out `alert(msg)`
  * To accept input from user, run `prompt(msg)`. The prompt will display a text box for user to fill in. Then the user input is returned as a string.
  * Defining a block also makes a *scope* with it aka *lexical scope*. A scope is a collection of variables and rules to show how to access those variables. 
    * Code inside a block can only access variables in its scope and the scope outside it. 
     
  * Javascript has the following built-in types: string, number, boolean, null and undefined, object and symbol in ES6. Only values have types in JS, variables are just containers.
  * There are other types - `function` and `array`  but these can be thought of specialized subtypes of `object`
  * Built-in types have associated methods to make operations like upper case conversion and setting precision.
    * `str.toUpperCase() , num.toFixed()` - These work by calling the object wrapper types for these built-in ones - called "natives" and then calling the associated method. All these happen under the hood.     

 * ### Coercion
   * Two types - implicit and explicit. Standard rules apply to coercion like any programming language.
   * `NaN, -0, +0, "", null, undefined` are falsy values. Everything else like functions, objects, arrays are true.
   * Two distinct forms of equality are there - `==` and `===`.
     * `==` is checking for equality and allowing coercion. `===` does strict equality checking.
     * If sure about what value types are being compared, then prefer `==`. It can improve readablity
   * For arrays, objects the value of references are compared, not the actual contents.
     * So two identical arrays will *not* be equal.
   * Inequality forms like `>,>=,<,<=` will compare strings lexicographically.
     * For expressions like ` 1 > "H" `, the string will be coerced into `NaN` which will return False.
 * ### Function Scopes
   * `var` keyword will define the variable in the current function scope or the global scope
   * **Hoisting** will make sure the variable declaration is '*hoisted*' its usage when the code is compiled. The `var` declarations are processed first in the compile phase before the usages.
   * #### Block Scopes
     * Variables can be declared in blocks such as while loops using `let`. The variable can't be used outside the block.
   
* ### Strict mode
   * `use strict` will ensure the code is put through the a tighter set of rules. This will improve code quality and optimization.
* ### Functions as values
   * Functions can be passed in like another variable. 
   * For example `function si() {..}` - si is just another variable that refers to the function declaration.
   * Functions could be thought as an expression. 
   * **Anonymous** Functions have no name. Eg. `var si = function() {...}`.
   * #### Immediately invoked function expressions
     * Eg. `(function IIFE() {console.log(3);})();` - The function is called immediately after its declaration. The ending brackets are important!.
   * #### Closures
     * It is a feature with which functions can obtain 'closure' over variables in the enclosing scope, even after the enclosing function has completed execution.
     * eg: ```
           function makeAdder(x) {
           function adder(y) { return y+x; };
             return adder;
           };
           >> one = makeAdder(1);
           >> two = makeAdder(2);
           >> one(2) == two(2) ## False
           ```
           
     * Above function will return the reference to the inner function. When it is called, it will remember the variable x and compute the result correctly even though `makeAdder` has already finished. 
     * Closures are commonly used to implement the Module pattern in JS.
* ### `this` Identifier
  * `this` is *not* the function or the object itself like in other OOP languages.
  * For eg: `function printVal() { console.log(this.val); }`
    * Now what `this` depends on how `printVal` is called.
      * `printVal();` - it is the global object in non-strict mode.
      * `obj1.printVal();` - it refers to `obj1`
      * `printVal.call(obj2);` - here it refers to `obj2`. The call method explicitly calls the function by setting `this` to the first argument.
      * `new printVal();` - `this` is a empty object.
* ### Prototype linkages
  * All objects have a prototype reference. When a property is get which the object itself does not have, then its prototype is checked if it has. This goes on and on the prototype chain.
  * Eg: `var b = {x:2}; var a = Object.create(b); a.y = 3; a.x`  a --> b --> Object.prototype --> null.
  * The prototypes act as a fallback and are used to simulate inheritance and in a pattern called behaviour delegation. Note this should not be confused with OOP class concept!
  * Each object by default points to the `Object.prototype` as its prototype.
* ### Backwards Compatibility
  * To ensure older browsers can run latest version JS code, _polyfilling_ and _transpiling_ is performed.
  * ### Polyfilling
    * Newer features and functions can be run in old browsers by adding special code that is equivalent to that feature.
    * Eg. `Number.NaN()` is only in ES6.
  * ### Transpiling
    * Newer syntax cannot be polyfilled. To run the new syntax in older environments, a _transpiler_ is used which transforms and compiles the code.
    * There are benefits such as better readability, optimizations.
* ### Non JS
  * Some parts widely used in JS programs are not controlled by the JS spec.
  * Some DOM related manipulations are done using a `host object` which is not a JS object. It is implemented in C/C++.
  * Eg. `console.log()`, `alert()` are thin API's for browser actions.
