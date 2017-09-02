

## Python 3.6 tutorial

* ### Invoking the interpreter
	* The python interpreter is usually installed as /usr/local/bin/python3.6. Putting it in your Unix search path makes it possible to start by just typing 'python3'
	* Typing an EOF character( Ctrl-D in Unix, Ctrl-Z on Windows) will exit the interpreter with zero exit status. Use 'quit()' alternatively.
	* Python command line arguments  - python3 [ -c command | -m modulename | script | - ] [args]
		* The _-c command_ option will execute the newline seperated command strings as Python code.
		* _-m modulename_  will execute the module with given name but no '.py'. Search sys.path for the *named module* and execute its contents as the __main__ module.
		* - will read command  fromt the standard input. 
		* _script_ will execute the code contained in script. It should be a filesystem path or a directory containing a __main__.py file
	* _-i _ option can be used when executing module or script to enter interactive mode after execution is complete.
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
			* _func.__doc__ _ is the docstring.
		
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
		* Sequence unpacking - x,y,z = t
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
		* Syntax to define a new dict - _ d = dict()_ and _ d = {} _
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
		* _ is, is not_ compare whether two objects are equal. Mainly for mutable objects like lists.
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
		* _ from sound.effects import echo_ - Also imports submodule, but  no need to reference the whole prefix.
		* Also possible to import the function or variable directly.
		
		* Form _from package import item_ - item could be submodule or subpackage or even a function,variable or class defined in a module.
			* The statement first tests whether the item exist in the package. If not found, assumes its a module and tries to load it.
				* If not found, raises _ImportError_.
		* _import item.subitem.subsubitem_ - all items except last item should be a package. Last item can be a module or package.
		
	* ## Import * from package
		* By default, it will import all modules listed in _ __all__ _ in the __init__.py file of the package.
			* _from sound.effects import *_ --> _sound/effects/__init__.py 
		* #If __all__ not defined
			* Imports the package and all names defined in the package, also includes submodules imported.
		* #Import * is bad practise! Avoid using it in production code.
	
	
* ### Input and Output

		
		
