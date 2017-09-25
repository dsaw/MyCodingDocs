

## Python 3.6 tutorial

* ### Invoking the interpreter
	* The python interpreter is usually installed as /usr/local/bin/python3.6. Putting it in your Unix search path makes it possible to start by just typing 'python3'
	* Typing an EOF character( Ctrl-D in Unix, Ctrl-Z on Windows) will exit the interpreter with zero exit status. Use 'quit()' alternatively.
	* Python command line arguments  - python3 [ -c command | -m modulename | script | - ] [args]
		* The _-c command_ option will execute the newline seperated command strings as Python code.
		* _-m modulename_  will execute the module with given name but no '.py'. Search sys.path for the *named module* and execute its contents as the __main__ module.
		* - will read command  fromt the standard input. 
		* _script_ will execute the code contained in script. It should be a filesystem path or a directory containing a __main__.py file
	* _-i_ option can be used when executing module or script to enter interactive mode after execution is complete.
	* Arguments can be passed and are stored in sys.argv. 
		* sys.argv[0] contains -c,loaded module path, - and empty string for -c command, -m, - option and no arguments.
		* sys.argv[0] is the script name for script loading option.
	* When commands are read from the tty, said to be in interactive mode
	* By default, source code encodings are in UTF-8. Can be changed by specifying _# -*- coding: encoding -*-_ in Python file.
	
* ### Basics of Python
	* Two ways to represent strings:
		* Enclosing single quotes - _'dev'_ Can enclose double quotes in it but single quotes and special characters need to be escaped. 
		* Enclosing double quotes - _"veg"_ Can enclose single quotes in it but double quotes and special characters need to be escaped.
	* Raw string - Use _r'dev/e'_, the string is printed as is without escaping.
	* String literals - use '''...''' or """...""" that will _span multiple lines. Add \ to not add a newline when printing a string.
	* _+_ concatenation operator and string literals concatenate automatically with 'Py' 'thon' = 'Python'
	* *String subscript operator* use str[first:last] where the str[first:last-1] is printed.
	* String is immutable
	
	* Lists
		* A compound data type used to group together values.
		* Lists are a mutable type.
	
* ### Control flow
	* Defining functions
		* Function is defined by _def funcname(param1,param2...): functionbody_
		* First line of function body can contain a string literal called docstring.
		* When entering a function for the first time, the arguments are stored as local variables in a new symbol table.
			* All variable references in a function first look in the symbol table,then the enclosing function symbol table, and so on till the global symbol table and then the table of built-in names.
			* All parameters are passed as call by object reference.
		* Default arguments are specified by adding a value after following a '=' 
		* Keyword arguments are specified by 'kwarg=val'
		* Positional arguments should be mentioned before the keyword arguments.
		* _*name_ argument accepts a tuple of a list of keyword arguments specified after the formal parameter list. Similarly __**kdict__ accepts a dictionary of keyword value list mentioned after the formal parameter list.
			* Arbitrary argument lists are described as above. They are scooped up after the normal paramaters are passed in (positional and keyword arguments).
		* _Unpacking arg lists_ - A tuple can be passed in a function call and unpacked into separate arguments by _funcname(op1,*tup)_
			* Similarly, dictionaries can be unpacked using _ **dict _ operator.
		
		* **Lambda functions**
			* These are function objects that have no function name associated with it.
			* They are restricted to a single expression and can use names from the _containing scope_.
			* Semantically identical to a function definition.
			* Eg: _lambda x: x+n_
			* Use: used as a function callback, return specific functions
			
		* **Multi-line docstring**
			* First line is a short,concise description of what the function does
			* Second line should be blank.
			* Next lines have more details like calling conventions, side effects etc.
			* Tools that process docstring check the amount of whitespace in the second line and set as the benchmark.
				The following lines indent is stripped off by this amount.
			* _func.__doc___ is the docstring.
		
		* ** Functional annotations**
			* Optional metadata information about the data types of parameters and function return types.
			* Eg: _ def sum(x : int, who : str) -> int: ... _
			* Can be accessed with _sum.__annotations _. It is a dictionary of paramaters as keys and types as values.


* ### Data structures in Python
	* ## List comprehensions
		* Concise and readable way to generate lists from other iterables or obtaining subsets of other lists.
		* Lambda use possible with no side effects.
		* Expression with one or more for loops and zero or more if conditions following it that act as filters. 
		* Eg: _[ x**2 for x in v]_
		* A  list comprehension has the for loop in the same order as the equivalent  nested for expression.
		* # Nested List comprehensions
		* _del_ statement will remove slices and also delete entire variables.
		
	* ## Tuple
		* Immutable sequence data type - hetereogenous sequence of elements that are accessed via unpacking.
		* Sequence unpacking - _x,y,z = t_
		* One element tuple - _(obj,)_
	* ## List
		* Mutable seqeunce type - accessed via iteration
		
	* ## Set
		* Unordered collection with no duplicate elements. Basic uses are membership testing and eliminating duplicate entries.	
		* Sets are specified using _set()_, NOT _{}_ which are used for dict types.
		* Like list comprehensions, set comprehensions are supported too.
			* Eg: _ s = {x for x in range(20)}_
			
		
	* ## Dictionary
		* It stores a unordered collection of key value pairs.
		* The keys should be **immutable** i.e. tuples with immutable elements, strings are allowed but not lists!
		* Syntax to define a new dict - _d = dict()_ and _d = {}_
			* Sometimes, string keys can be specified like keyword arguments.
			
		* It is an error to extract a value of a non-existent key.
		* To get a sequence of keys / values, run _list(d.keys())_ / _list(d.values())_
		* Use the _in_ operator to check if a key exists in the dictionary.
	* ## Looping techniques.
		* Dictionaries can be looped over using the _items()_ method.
			* Eg: _for k,v in d.items(): ..._
		* Sequences can be looped over using the _enumerate()_ method.
			* Eg: _for index, val in l.enumerate(): ..._
			
		* Multiple sequences can be paired together using the _zip()_ function.
			* Eg: _for q,a in zip(qu,an): ..._
		
	* ## Comparisons 
		* _in_ and _not in_ are allowed to be used in _if_ and _while_ statements.
		* _is, is not_ compare whether two objects are equal. Mainly for mutable objects like lists.
		* _and_ & _or_ are short circuit operators in boolean expressions. 
			* If not used with booleans, the last evaluated argument in the expression is returned.
			
			
	* ## Sequence comparisons
		* Sequence objects can be compared and are evaluated in lexicographic order.
		* If a sequence is a sub sequence of another candidate sequence, this sequence is  of lower order.
		
		
* ### Modules 
	* ## Modules
		* A module is a file containing Python definitions and statements. 
		* Within the module, _ __name__ _ defines the name of the module loaded.
		* If the module is run as a script, _ __name__ _ is '__main__', the top-level module.
		* While importing the module, the module name is imported in the symbol table.
		* To import specific names, add _from mod import d1,d2_ which will directly add the names in the importing module's symbol table.
	* ## Modules as scripts
		* The code in the module can be run, just as if you imported it by calling _python mod.py <arguments>_
	* ## Module search path
		* When importing some module, it will check if there are built-in modules with the same name.
		* The list of directories _sys.path_ is initialized. It contains the following directories
		* Then checks the current directory/input script directory and PYTHONPATH.
		* If module not found, returns _ModuleNotFoundError_
	* ## Compiled Python files
		* To speed up loading of modules, Python supports caching of compiled modules.
		* They are files with _.pyc_ extension, stored in __pycache__ directory.
	* ## Standard Modules
		* __dir()__ will return the names the modules defines.
		* __builtins_ module will list the names of built-in functions and variables.
		
	* ## Packages
		* It is a way of structuring Python's module namespace by using "dotted module names".
		* __init.py__ is compulsory in a package for treating the directories as subpackages.
			* Avoids accidental module name clashes.
			* Initialisation code can be added.
		* _import sound.effects.echo_ - Imports submodule, which is referenced using whole name.
		* _ from sound.effects import echo_ - Also imports submodule, but no need to reference the whole prefix.
		* Also possible to import the function or variable directly.
		
		* Form _from package import item_ - item could be submodule or subpackage or even a function,variable or class defined in a module.
			* The statement first tests whether the item exist in the package. If not found, assumes its a module and tries to load it.
				* If not found, raises _ImportError_.
		* _import item.subitem.subsubitem_ - all items except last item should be a package. Last item can be a module or package.
		
	* ## Import * from package
		* By default, it will import all modules listed in _ __all__ _ in the __init__.py file of the package.
			* _from sound.effects import *_ --> _sound/effects/__init__.py 
		* If __all__ not defined
			* Imports the package and all names defined in the package, also includes submodules imported.
		* Import * is bad practise! Avoid using it in production code.
	
	
* ### Input and Output
	* There are two ways of printing strings that are:
		* Doing string slicing and concatenation yourself. Like methods on string objects.
		* Formatting string literals or the str.format() method.
		
	* Python can convert any values to string using _str()_ or _repr()_ method.
		* _str()_ - Returns a fairly human-readable representation of the string
		* _repr()_ - Returns a interpreter-readable representation
		* For some objects like lists and dictionaries, repr and str is the same.
		* For strings they are different.
	
	* ## String methods
		* _str.rjust(n)_ - Right justifies the string in fields of length n.
		* _str.ljust(n)_ - Left justifies the string in fields of length n.
		* _str.center(n)_  -Centers the string like before.
		* Note if str is longer than n, it is returned as is.
		* _str.zfill(n)_ - Fills the left with 0s. Also recognizes + and - signs.
		
	
	* ## Basic format string usage
		* _" xxxx {0} {1}".format(m,n)"_ - passes in positional arguments accessed using index.
		* _" xxxx {k} {m}".format(k=1,m=2)"_ - keyword arguments accessed using keys.
		* _" xxxx {['color']} ".format(dct)"_ - Dictionary is passed in then its value is accessed using the square bracket notation.
		* _" xxx {!a} {!s} {!r} .".format(a,b,c)"_ - _!a_, _!s_, _!r_ will convert the value to ascii, string, repr respectively.
		* _"string.. {:3d} {:3.5f}"_ - format specifier indicates the number of characters to be printed 
		 
	* ## Reading and writing files
		* _open(filename,mode)_ - it returns a file object opened in modes like 'r','w','a'.
		* Files are opened in text mode or binary mode.
			* Text mode have strings stored in specific encodings.
			* In binary mode, data is read and written in the form of byte objects.
			
	* ## Reading and writing structured data using json.
		* Uses json libraries to serialize and deserialize objects.
			* Convert data hierarchies to string representations. Process is called serializing.
			* Reconstructing the data from the string representation is called deserializing.
		* _json.dumps(obj)_ - Returns a json representation of the object (lists,dictionaries)
		* _json.dump(f,obj)_ - Same as dumps, just stores the representation in file object f.
		* _x = json.load(f)_ - Decodes the data in file and returns the object.
		* Difficult to handle arbitrary class instances.
		
		
* ### Errors & Exceptions
	* Two distinct types of errors:
		* Syntax Errors : also known as parsing errors are the most common.
		* Exceptions: errors detected during execution that are usually not fatal and are handled by programs
		
	* Exceptions can be handled by _try...except_ statements:
		* The try clause is executed.
		* If no exception is caused, the execution of try is finished.
		* If exception occurs, the corresponding except statement clause is executed.
		* If no such except clause exists that handles the corresponding exception class, the exception is passed on to outer try statements.
			If no handler is found, it is an **unhandled exception** and the execution stops.
		
		* Note the class in an except clause is compatible with a class if it is the same class or the base class.
		* _Else_ clause will be executed if no exception was raised.
		* _finally_ clause will be executed no matter whether exception was raised or not.
		* If an exception is raised but no corresponding handler is there, _finally_ clause is executed after which the exception is raised.
		
	* Exception instances:
		* The exception object has its arguments stored in _inst.arg_.
		* _ print(inst)_ - will print the arguments directly as _str_ is returned. Can be overriden in other subclasses.
	* Raise exceptions
		* _ raise ValueError_ - will throw an exception instance. No brackets required.
		* _ except Error: raise _ - Simplet form will re-raise the actual exception of the clause.
		
	* User defined exceptions:
		* Programs may name their own exceptions by creating a new exception class. They should be derived from _Exception_ class.
	* With statement:
		* Block of code can be run and any resource opened is released promptly when the 'with' block is executed.
		* Commonly used for closing file objects.
		
		
* ### Classes
		* All members are _public_ and methods are _virtual_!
		* Classes can be modified at runtime. 
		* Objects have individuality and multiple objects can be bound to multiple names can be bound to the same object.
			Also known as aliasing.
	* ## Scope and Namespaces
		* Namespace is a mapping from names to objects in Python.
			* Implemented as a _dict_, though could change in future.
			* When a class definition is read, module is executed,function is called, corresponding new namespaces are defined promptly.
			* Any assignment of a variable will update it in the corresponding namespaces.
			* There is a namespace of built in variables called built-in that exists in the lifetime of the Python interpreter.
			* Lifetime of namespaces vary: A function namespace is defined during the first time the function is entered and deleted when function returns or exception is raised not handled by the function.
		* Scope is a textual region in Python where namespace is directly accessible i.e referenced without qualification.
			* Atleast three scopes exist at one point in a program
				* Innermost local scope, enclosing scopes and global scope(module)
				* Any variable handling happens in the local scope, unless _nonlocal_ statement is used, in which case the name is rebound in the outer scope.
					Similarly for the _global_ statement, the module level names are bound.
					* Non-local names are read-only.
			* Scopes are generated statically, but searched dynamically.
				* innermost scope, contains local names
				* scopes of enclosing functions, which are started with the nearest enclosing scope.
				* next-to-last scope, current modules global names.
				* outermost scope contains built-in names.
			* _del x_ removes the binding from the namespace referenced by the local scope.
		* Class definition syntax
			* _class ClassName:
				<stmt-1>
				...
				<stmt-n>
				_
			* Like a function definition, has to be executed.
			* When a class definition is entered, a new namespace is created and used as  a local scope.
			* When a class definition is exited, a class object is created.
		* Class objects support two kinds of operations: attribute references & instantiation.
			* Instantiation involves calling the class object like a parameterless function.
				* _ c = MyClass()_ - The _init_ method is called with the newly created object with arguments passed to that method.
			* Any valid attribute can be referred to when the attribute has been defined in the class definition.
		* Two kinds of attributes, data attributes and methods. A method is a function that 'belongs' to an object.
			* myclass.f is a function, while x.f is a method. Method object can be stored away in a variable.
			* A method _x.f()_ is called as _Class.f(x)_, where the first argument is the instance variable itself.
		* Two kinds of variables, class variables and instance variables.
			* Class variables shared by all instances in a class.
			* Instance variables are only unique to each instance.
			* Remember, a mutable object for a class variable has got quirks.
		* Data attributes override method attributes for the same name, to prevent name conflicts
			
