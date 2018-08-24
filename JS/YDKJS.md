
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
   
