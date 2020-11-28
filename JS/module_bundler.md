## [] Kinds of module systems!

* ### Common JS
    * `var nodj = require('nodejs')` - designed for synchronous loading & Node.js style. 
    * `module.exports = {a: a}` - qualified imports have to be exported through an object.
    * every time something  is imported - for unqualified imports a new copy is made of the exported obj. For qualified imports, property lookup is done.
* ### Asynchronous Module Definition
    * `define(id?, dependencies?, factory);` - designed for asynchronous loading of modules.
* ### ES6 
    * imports and exports built into the language
    * `import defaultname, {n1,n2} from './module'` - supports default and named exports.
    * the modules are read only live bindings of exports, for both qualified and 'direct' imports.
    * supports cyclic dependencies because these imports are **indirections**.
    * Module imports can be statically analyzed and optimized (dead code elimination, tree shaking).
    * Support for **dynamic loading** using `module('identifier').then(...)` which returns a Promise.