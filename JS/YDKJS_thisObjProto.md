## YDKJS - part 3
* this & Object Prototypes.
  * The `this` mechanism is interesting and different from the lexical scope mechanism of JS. It's use confuses many developers, since it changes in runtime.
  * A common example is to use it and expect it to refer to the function itself.
    * ```
       function blah() 
       { 
          count = 5;
          console.log("blah blah blah x" + this.count );
        }
       
          count = 0;
          
          blah(); // 0 ,not 5
          
      ```
  * The value of `this` depends on how the function is called. `this` refers to the global object in a  standard function.
  * There are ways to set `this` by using functions like apply,bind,call.
    * `apply` and `call` are same, except `apply` takes in an array of arguments.
    * `bind` returns a new function with `this` set to the first argument.
  * `this` entirely depends on how the function was called and from where - the call site.
  * `this` does not refer to the lexical scope.

*  The mechanism of `this`.
  * The default binding of `this` resolves to global variables. If strict mode is set, `this` resolves to `undefined`.
  * If the call site use the object context to call the function, then the `this` of function will be set to the object.
  *
  
   
