## YDKJS - part 2
* Scopes and Closures 
  * Scopes are a set of rules used to determine where and how variables can be accessed. JS engine will refer to scope when compiling and executing code.
  * Javascript processing can be split into roles played by *compiler*, *engine* and *scope*. 
    * *Compiler* converts the tokens into a AST and performs intermediate code generation.
    * *Engine* will execute instructions generated  step by step.
    * In the process, these role players would talk to *Scope* for checking variable existence.
  * Two kinds of references are present in a program.
    * *LHS* - left hand reference wherein variable is looked up and value assigned to it `var a = 3;`.
    * *RHS* - right hand reference wherein the variable's value is retrieved.
    * Both require consultation with *Scope*.
  * ### Nested scopes
    * When *engine* does a lookup of a variable, it will consult the current scope. If not found, the variable is forwarded to the enclosing scope and so on till the global scope is reached.
  * ### Behaviour of declaration and assignment in JS
    * if in *non-strict* mode, a  LHS lookup is performed up the nested scope chain. If no variable found, then a variable is created and handed to the engine.
    * In *strict* mode, a `ReferenceError` is thrown. Automatic variable creation is not allowed.
    * For RHS lookup, if no declaration of the variable is found, then `ReferenceError` is thrown.
* Lexical scoping
  * Scope in JS is identified at lexing time. When the compiler processes the string of characters and assigns token, the scopes are determined. 
  * Thus at author time, variables are declared and their scopes identified. But there are ways to cheat this scoping in JS.
  * *Lookups* are done by consulting from the innermost scopes to the enclosing scopes, one after the other till the global scope is consulted.
  * Remember that lookups are only performed on first class variables. When a property is accessed using dot notation, lookup is performed on the first identifier. On the rest, the property resolution is applied. Eg: `console.log()`.
  * ### Cheating lexical scope
     * `eval` : Passing in declarations of variables as executable code in `eval` will modify the scope. This is a form of dynamic scope change. Eg: `eval('var a = 3')`.
     * `with` : The with statement block creates a whole new lexical scope out of the object passed in. It treats the properties of the object as variables in its own scope.
       * Eg: `with(obj) { a:4; b:5};` - If the object doesn't have the given property, then normal LHS lookup is done. Those properties will be defined in the global scope.
       * It is meant to be used as a shorthand for property references.
  * ### Pitfalls of dynamic scope changing
    * Using above constructs results in  reduced performance. Compiler uses optimizations when standard lexical scoping is used to speed up processing. However, with the above it has to drop them and analyze code at runtime for scope changes. 
* Function vs Block scope.
  * Javascript has both function and block based scope.
  * Hiding of identifiers in different scope is based on the application of the *least privilege principle*.
  * Only those identifiers should be exposed to the scope which are required for use. Avoid declaring extraneous identifiers.
  * Variables declared with `var` *do not have block scope*.
  * Collision can be avoided by declaring entirely different names for identifiers.
  * The way variable scopes are defined for ` var ` declarations are that the variables are scoped to the enclosing scope. It could be the closest enclosing function or the global scope.
    * ` for( var i = 0; i< 5; ++i) { ... }` - `i` would actually be scoped to the function wrapping the for loop. 
  * The ways in JS that implement block scoping are `let`, `catch` and `const`. 
    * `let` - It will attach itself to the block.
    * `catch` - variables are scoped to the `catch` block.
    * `const` - just like `let` but it cannot be edited later.
  * IIFE also define a function scope for the variables declared inside.
* Hoisting.
  * Javascript processes code in two phases as noted before, compiler phase and engine phase.
    * It interprets the following ` a = 2; var a;` as a declaration and an assignment. The declaration is processed first and *hoisted* to the top of the code. Assignments are processed later in the engine phase.
    * Function and variable declarations are hoisted but not function expressions.
      * `foo(); var foo = function() { ... }` - This will set the reference `foo` throw a `TypeError` since foo is `undefined`.
    * Functions are hoisted first when there are duplicate definitions.
    * A named function expression's name will not be available to the enclosing scope. It will be inside the function.
* Scope closure.
  * Closure is when a function is able to remember its lexical scope when it is executed outside its scope.
  * Closure is observed when an outer function returns an inner function that uses a variable of the outer function. Thus, the inner function maintains *closure* over the outer scope.
    * Eg. `function foo(i) { function bar() { console.log(i); } return bar;} var f = foo(5); f();  # print 5`
    * Examples of real world usage is in timers, ajax requests, web workers etc.
  * Per iteration scope
    * Closure property can be used to simulate per iteration scope. Some ways to try it out:
      * ```
        for( var i=1; i<=5; ++i) {
          setTimeout( function() { console.log(i); }, i*1000);
          }
        ```
      * The above would print 6 five times. It doesn't work as intended since the anonymous function has closure over the **global** variable i. The timer is executed after the loop is done, so i is 6 and is shared.
      * ```
        for( var i=1; i<=5; ++i) {
          let j = i;
          setTimeout( function() { console.log(j); }, j*1000);
          }
        ```
      * This works because there is a block scope variable with its own value in each iteration. The function will have closure over those differing values in each iteration.
      * Another way without block scope is to use IIFE's and declare its own variable inside it.
   * Module pattern
     * This can be implemented using closures. An outer function will define some inner functions and variables inside it. These "private" properties are returned in an object format.
     * ```
       function myModule() {
         var j=4;
         function foo() {
             console.log("what's this? " + j);
             }
         return
         {
           foo : foo
         }
       }
       ```
     * The returned object represents the public API of the module. Note that the module function needs to be called for those inner scopes to have data initialized.
       * ` var m = myModule(); m.foo(); # what's this? 4`
  * Module dependency manager 
   * The closure feature is used in many module dependency managers. A simple proof of concept uses a function definition wrapper and passes in a list of dependencies for the module to execute.
     * `function Manager() { var modules={}; function define(name, dependencies, implementation) { ...}  function get(name) { return modules[name]; } return { define: define, get: get}`
     * `define` passes in a dependencies list, calls the public API of each dependency and stores it in the list. The original module function is called with the API's of its dependencies as arguments and stored in the `module` object.
     * `get` will return the public API of the module stored in the object.
  * Future Modules
    * `import` - It will import one or more members of the modules API into the current scope. Each of them is bound to a variable.
    * `export` - The variable or function specified is made available to the file that imports this module.
    * `module` - This will import all the identifiers in the module under the name specified. ` module foo from "foo"; foo.func()`
    * ES6 modules are static, the API's can't be changed at runtime. The compiler can throw an error earlier when the reference doesn't  exist.
    * Modules need to be defined per file.
  * Lexical vs Dynamic scopes
    * Lexical scopes are defined based on _where_ the function was declared. It is static and does not change when the code is run.
    * Whereas dynamic scopes are determined based on *where and how* the function is called.
    * `function foo() { console.log(a)}; function bar() { var a = 3; foo(a);}  var a = 2; bar()`. It will return 2, not 3. Javascript has only lexical scope.
    
  
 
