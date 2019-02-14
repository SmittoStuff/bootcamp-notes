# Python/Django Full Stack Development

## Python
* Anaconda distribution: comes pre-packaged with additional useful libraries
* Miniconda: smaller and lighter version of Anaconda with the essentials
* `platformio-ide-terminal`: most popular terminal package for atom
* `autocomplete-python` package in atom for python code autocompletion

### Numbers/Strings
* Numbers in python: Integers and Floating Point numbers (decimal)
* Strings: can have either `'` or `"` to wrap, use one to wrap the other
* Can refer to individual characters of a String using index notation:
```
print(mystring[0])
```
* Supports negative indexing, can use `[-1]` to get last character of String
* To get all characters including and after the 2nd index and up to the 5th:
```
print(mystring[2:5])
```
* Slicing notation starts at 2, but only goes _up to_ 5, not including it!
* Step size: to skip every other character in string do 
```
print(mystring[::2])
```
* Strings are immutable, can't redefine certain indexes, can just redefine the entire variable 
* Can use `.upper()` and `.lower()` to set case of entire string, many other methods like `.capitalize()`
* Can use the `.split()` method to split each individual word on spaces into a list:
* Can specify the particular character to split on:
```
mystring.split('o')
```
* For String interpolation and formatting:
```
x = "Item One: {x}, Item Two: {y}".format(x="Big", y="Boi")
```

### Lists/Dictionaries
* Can put different data types in a List:
```
mylist = ['big',1,'boi',2,'swag']
```
* Refer to List elements with same indexing as Strings, including slicing
* Unlike Strings, Lists are mutable, can change independent elements of them
* Can user `.append()` to add a new item to the end of the list
* To add multiple new items to the end of the list, can use `extend()` method:
```
mylist.extend(['x','y','z'])
```
* Use `.pop()` to pop off the last element of the list and return that item, can also specify the index 
* Use `.reverse()` to reverse the elements of the list, no kidding! Can also use `.sort()`, etc
* Use multiple indexes to get an element from a nested list: `list[2][1]`
* List compregension:
```
matrix = [[1,2,3],[4,5,6],[7,8,9]]
first_col = [row[0] for row in matrix]
```
* Dictionaries: Python's version of Hash Tables/Objects in JS, create mappings with key-value pairs
* Can nest dictionaries, lists etc inside one another, and then call methods on the final assignment
* Existing elements are mutable, simply add new elements with:
```
mystuff['key'] = 'value'
```
* Booleans: `True` and `False` or `1` and `0`, need the capital!
* Tuples: immutable lists, such as `(1,2,3)`, can mix data types, slicing indexing etc are same as lists
* Sets: unordered collections of unique elements, adding multiple identical elements won't change it

### Control Flow 
* No type coercion in Python, `1 == "1"` will return false 
* Logical operators are `and` and `or`
* Python stresses readability due to white space, not as much `{}`, control flow statements are keyword, statement, and `:`
```
if 4<20:
 print("beast!")
```
* Use `elif` and `else` to follow up conditionals:
```
if 1>2:
 print("beast")
elif 2>3:
 print("mode")
else:
 print("swag")
```
* For loops/iterating:
```
seq = [1,2,3,4,5,6]
for item in seq:
  print(item)
```
* Tuple unpacking, iterating through tuples:
```
mypairs = [(1,2),(3,4),(5,6)]
for (tup1,tup2) in mypairs:
  print(tup1)
  print(tup2)
```
* Use `range` to define starting num, ending num, and step size. Range is a generator (function) that incrementally makes the next element:
```
for i in range(0,20,2):
  print(i)
```
* List comprehension:
```
x = [1,2,3,4]
out = [num**2 for num in x]
```

### Functions 
* Functions are formatted in snake case, can assign parameters with default values:
```
def my_func(param1='default'):
  """
  THIS IS THE DOCSTRING
  """
  print("My first python function is {a}!).format(a=param1))
  
my_func("beast")
```
* Python automatically checks for a docstring for the function, and will often display it when autocompleting depending on your IDE
* Use `type()` keyword to check for the type of the object:
```
def add_num(num1,num2):
  if type(num1) == type(num2) == type(10):
    return num1+num2 
  else:
    return "We need INTS!!"
```
* Can use `lambda` expressions for very small functions that don't require permanent declarations:
```
mylist = [1,2,3,4,5,6,7,8]
evens = filter(lambda num: num%2 == 0,mylist)
print(list(evens))
```
* Can use the `in` function to determine if an element is in a list:
```
print('x' in [1,2,3])
```

### Scope 
* Python scope follows the LEGB rule:
  * Local: names assigned in any way within a function, and not declared global in that function
  * Enclosing Function locals: names in the local scope of any and all enclosing functions, from inner to outer
  * Global: names assigned at the top-level of a module file, or declared global in a def within the file
  * Built-in: names preassigned in the built-in names module: open, range, SyntaxError, etc
* When you redefine `x = 50` in a function, that reassignment is limited to the scope of the function (EFL level)

### Object Oriented Programming
* In Python, everything is an object, you can check its type with `type(thing)`
* `__init__` method is called automatically after an object is created, begins with a reference to the instance object, `self`, followed by arguments that are passed:
```
class Dog():
  def __init__(self,breed,name):
    self.breed = breed
    self.name = name
```
* Class Object Attributes: always the same for any instance of the class, declare before init method
* Instance attributes are referred to with `self`, while class object attributes are referred to with the class name:
```
class Circle():
  pi = 3.14
  def __init__(self,radius=1):
    self.radius = radius  

  def area(self):
    return self.radius*self.radius*Circle.pi
```
* Inheritance: one class can inherit/derive from another class, declared like:
```
class Dog(Animal):
```
* Special Methods: always denoted with `__` on each side of method name, such as `__str__` for what to return when printing the object

### Errors and Exceptions 
* Opening files: first argument is file path, second is if reading, writing, or both:
```
open("myfile.txt",'r')
```
* Error handling follows a try, except sequence:
```
try:
  f = open('simepl.txt','w')
  f.write("Test writing to file")
except IOError:
  print("Error: could not find file or read data!")
except:
  print("Error!")
else:
  print("Success!")
  f.close()
```
* Can use a `finally` block that prints regardless of if there's an exception at the end of a try/except/finally statement

### Regular Expressions 
* Allow us to search for patterns in Python strings, imported as `re` 
* `re.search(pattern,text)`: pass in the pattern you're looking for and the text to parse through, returns match object
* Match object holds the starting index of where the pattern is found, `match.start()`
* `re.split(split_term,email))`: used to split a string into a list on a particular pattern, such as `@`
* `re.findall(match_term,text)`: returns a list of all instances of the match_term in the input string
* `sd*` represents an s followed by 0 or more d's
* `sd+` represents an s followed by 1 or more d's
* `sd?` represents an s followed by 0 or 1 d's
* `sd{2,3}` represents an s followed by 2 or 3 d's
* `s[sd]+` represents an s followed by 1 or more s's or one or more d's
* `[^!.?]+` represents removing instances of !, ., or ?
* `[a-z]+` and `[A-Z]+` represents sequences of lower case or upper case characters
* `[r'\d+']` represents a sequence of digits, `[r'\D+']` represents a sequence of non-digits, `\s` is whitespace and `\S` is non-whitespace, `\w` is alphanumeric, `\W` is non-alphanumeric

### Modules and Packages 
* Can save a file with functions, and reference it as a module with `import file_name`, then call `filename.func_in_module()`
* This will generate a `_pycache_` folder, as the interpreter compiles code you run to bytecode and stores it there as `pyc` files
* Can rename a module with `import mymodule as mm`
* Can import certain functions: `from mymodule import func_in_module`
* Can import all functions as `from mymodule import *`, this is wasteful and should be avoided!

### Decorators
* Can get all local variables with the `locals()` call, and all globals with `globals()`
* Returning functions: can return functions that are defined within the current scope, and can be assigned to variables
* Can pass a function as an argument, and then call that function:
```
def hello():
  return "Hi Nathan!"
  
 def other(func):
  print("Hello!")
  print(func())
```
* Can replace passing a function into another function with the `@func`:
```
def new_decorator(func):
  def wrap_func():
    print("CODE HERE BEFORE EXECUTING FUNC")
    func()
    print("FUNC() HAS BEEN CALLED")
  return wrap_func

@new_decorator
def func_needs_decorator():
  print("THIS FUNCTION NEEDS A DECORATOR!")
  
func_needs_decorator()
> CODE HERE BEFORE EXECUTING FUNC
> THIS FUNCTION NEEDS A DECORATOR!
> FUNC() HAS BEEN CALLED
```

### Name and Main
* Sometimes when importing from a module, you would like to know whether a module's function is being used as an import, or if you are using the original `.py` file of that module
```
if __name__ == '__main__':
  print("one.py is being run directly")
else:
  print("one.py has been imported")
```

## Django
* Django overview:
  * User requests a URL
  * This goes to `urls.py` file, which calls `views.py` file
  * This calls `models.py`, which interacts with database and feeds back to `views.py`
  * views.py uses html/css/js templates to fill out view, then sent back to use