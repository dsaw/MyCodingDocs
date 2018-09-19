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
    * Using above constructs results in  reduced performance. Compiler uses optimizations when standard lexical scoping is used to speed up processing. However, whith the above it has to drop them and analyze code at runtime for scope changes. 
