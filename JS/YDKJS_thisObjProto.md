## YDKJS - part 3
* this & Object Prototypes.
  * The `this` mechanism is interesting and different from the lexical scope mechanism of JS. Its use confuses many developers, since it changes in runtime.
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
     * 
