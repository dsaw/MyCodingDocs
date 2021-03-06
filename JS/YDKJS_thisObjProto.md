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
  * Eg: ` var obj = { a:2, foo:foo}; obj.foo();  # 2`
* Implicit binding lost
  * `var bar = obj.foo; bar(); ` - `this` will refer to global context, not obj context when the function reference is called.
* new binding
  * The `new` operator acts like a constructor but is just a function in JS.
  * ```
    function bar(a) { this.a = a; }
    var baz = new bar(4);
    console.log(baz.a);  # 4
    ```
     * Above will create a brand new empty object and return it to the variable. The function is called with `this` set to the new object. The newly constructed object is prototype-linked.
     * In the `new` call, if the function does not return its own alternate object, then the new object is returned.
* Binding order
  * new binding takes precedence over explicit binding, which takes precedence over implicit binding.
  * new binding will override hard binding using `bind`.
    * The `bind` utility is sophisticated, it will pass in the arguments during the initial binding as default arguments of the returned function. Also known as **partial application**.
* Ignored `this`
  * In `call`, `apply` or `bind`, if `null` and `undefined` is passed as a binding parameter, these values are ignored and default binding rule is used.
  * To be safer, an empty object can be created using `Object.create()`, without delegation to prototype and passed in to the respective functions.
* Indirection
  * If the effective call site is just the function reference, even if that function is inside an object, the default binding rules will apply.
* Lexical `this`
  * Arrow functions have a different form of scoping. It's `this` adopts a value from enclosing function at call time.
  * This behaviour is more lexical and does not work based on the usual rules of `this`.
    * ```
      function foo() {  return () => {console.log(a)}; }
      var obj = {a:1};
      var a = 2;
      
      var bar = foo();
      bar();   // 2
      bar.call(obj); //  2, not 1
      ```
  * A rule of thumb, avoid using both styles of code. stick to either traditional `this` or lexical `this`.  
* Object
  * Objects come in literal form and constructed form. The constructed form is rarely used.
  * There are primary types and built in objects in JS. Many built in objects like `String`, `Number` are related to its primitive counterparts. They are just built-in functions.
  * Object contents can be accessed in two ways - "key" access `obj['a']` or "property" access `obj.a` . The former can take any UTF-8 compatible string as the "key".
  * There is no concept of a method in JS, if a function is 'part' of an object, it is just property access.
  * Properties can be added to `Array` type without changing the length of array.
* Duplicating objects.
  * Performing a shallow copy is done using `Object.assign(targ, src)`. It iterates over all the enumerable, owned keys of source object and copies it to the target object. The references are copied as is. Note that this is `=` style assignment.
* Descriptors
  * Property descriptors are descriptions of properties in JS. They can define what property name & value is of the given object, whether it can be writable, enumerable, configurable.
    * `Object.defineProperty(obj,name,{value:?,writable:?, enumerable:?, configurable:?} );`
    * `writable` defines if the property can be set to a value, otherwise it will fail.
    * `configurable` will ensure the property descriptor can be set again. if set to false, the property cannot be configured again nor deleted.
    * `enumerable` if set to True will make the property visible when the object is iterated over for..in loops.
      * `getOwnPropertyNames` will return **all** the properties of the object while `Object.keys(obj)` returns only enumerable properties.
  * Accessor 
    * `[[Get]]` operation happens when a property access is performed on an object. If the requested property does not exist, `undefined` is returned.
    * `[[Put]]` operation works a little more than just performing property setting. If the property is an accessor descriptor, the setter is called. Else if the property `writable` is false then it fails.
    * An accessor descriptor is a property with `get` and `set` methods that return and set values respectively.
      * The `value`, `writable` properties are moot.
      * `var myobj = { get a() { return 2} };`
  * Existence
    * `in` will check if property exists in given and object and continue up it's prototype chain.
    *  `hasOwnProperty` will only check for the given object.
  * Iterators
    * An object can be iterated over if it's `Symbol.iterator` property returns a function. This will be the iterator object whose `next` function will be called to return `{value: v, done: t}`. Once all the properties are iterated over the last next call will return the `done` set as `true`. Also known as `@@iterator` property.
    * `for (var v of obj) { console.log(v); }`
* Classes in JS
  * JS has no classes like in OOP languages. It has got elements that _simulate_ classes.
  * Class inheritance is done though object copying.
  * There are no relative references to the parent class like in OOP languages. A separate copy of parent class behaviour is maintained along with the child class behaviour. This has to be performed through explicit mechanisms.
  * Polymorphism in JS
    * Since there is no actual polymorphism in JS, it has to be performed using a function called a 'mixin'.
    * Mixins copy new properties from source object to return them in the target object. It is simple reference duplication.
      * Explicit pseudo-polymorphism
        * The mixin is called to copy properties from the parent object to the child object. The child object with the method to be "overidden" has got an explicit call to the method with the same name in the parent object. eg: `BaseObj.method.call(this)`.
      * Implicit mixin
        * In this the child object has the method defined in it as above, without the mixin call.
    * Mixins make code harder to maintain and read. Remember only the references are duplicated, there is no actual method and class copy like in OOP languages.
* Prototype.
  * Object prototypes are used to link objects.
  * Prototypes are just a form of object delegation. There is no class copying, only objects are linked to each other. 
  * Prototypes can act as fallbacks when the object doesn't have the particular method and field. 
  * One way to create an object that points to another object through a prototype is by using `create`. Eg: ` var o = Object.create(o2);`
  * Shadowing properties on object.
    * Shadowing means to add a new property of the same name of another property that exists of the object higher up on the prototype chain.
    * When an object property is set and the property does **not** exist on the object but is there on the prototype chain, then that property might be shadowed.
      * If the property is not read-only, then shadowing occurs.
      * Else if the property is read-only, then no operation is allowed.
      * If the property is a setter, than that property is set and no new property will be added. 
  * Avoid shadowing, it becomes unclear and confusing in practical life.
* Using prototype to simulate "class" functions
  * Creating another function and using it to create a new object using `new`, we can make multiple "copies" of objects. Though they aren't actually instances in the OOP sense, the prototype of those objects are linked to the prototype of the function.
* Constructor call.
  * The function used, its prototype has a property called `constructor`. This contains a reference to the code in function.
  * The constructor is easily settable and can become confusing if is changed because this is called when `new` is used.
  * Remember the constructor does not mean "constructed by".
* Class relationships.
  * To check if an object appears on the prototype chain of another object. `b.isPrototypeOf(c);`.
* Delegation
  * Using object links as fallbacks is not robust design. One way to improve upon it is using Delegation design pattern.
  * `myObject.doCool = function() { this.cool(); };`. There is a cool method up the chain.
* OLOO
  * Thinking in terms of delegation in Javascript is much more natural than forcing down object oriented programming on it.
  * Design is much simpler with object linking and code is reduced. 
  * Introspection is done with `isPrototypeOf` which makes it clearer instead of the `instanceof`.
  
 
  
    
     
    
  
