[← back to *Main Page*](https://github.com/dawkiny/Python3/blob/master/README.md)

---
# Functions

---
# Basics on Functions

## Defining Functions

A **Fuction** has 2 steps;_Define_ & _Call_.
It operates when it is _called_.



### ```def ``` Statements

```python
# Define
def func_name():
    operation

# Call
func_name()
```

* Example
```python
def printer():
    print("Python!")

printer()
#'Python!'
```



### ```return``` Statements

It returns the result object of a _Fcuntion_ When the _Function_ is called.  
Using ```return``` can assign the result of a _Function_ as an _object_.

Look at the difference between ```print``` and ```return```

With ```print```, it just prints the result.
```python
def adder(a, b):
    print(a + b)

res = adder(1, 2)
#3 (print operation)
res
#Nothing is shown!
```

With ```return``` Statements:
```python
def adder(a, b):
    return a + b

res = adder(1, 2)
#Nothing is shown, but assignment is done!
res
#3
```





---
## Local & Global Variables



### Local Variables

When Using a _Function_, the variables inside of the _Function_ and ones outside of the _Function_ are separate.  

_Inside of Objects like Classes or Functions_ are called **_Local Environments_**,  
and _Outside of Objects_ is called **_Global Environment_**.  

The variables belong to **_Local Environments_** are called **_Local Variables_**,  
and the variables belong to **_Global Environment_** are called **_Global Variables_**.  

**_Local Variables_** cannot affected to **_Global Variables_**
```python
x = 2        # 'x' is a global variable.
def funct():
    x = 10   # This 'x' is a local variable.
    print(x)

funct()
10          # It's about the local.

x
2           # It's about the global.
```


But in Local(in this case, inside of Functions), you can use Global Variables.  
This way is _**not recommended_** because operations in the local environments get affected to the **_Global Environment_** and throw _Errors & Exceptions_, despite Local operations are **CORRECT**!.  
_That's why we should use **Arguments**._

```python
x = 2        # 'x' is a global variable.
def funct():
    print(x)
```
funct()
2           # Local 'x' is not defined: then it refers to Global.
```



### ```global``` Statements

To change **_Global Variables_** in **_Local Environments_**, use ```global``` Statements.  
```python
x = 2        # 'x' is a global variable.
def funct():
    global x # For now, we use this 'x' as a global variable.
    x = 10   # Assign 10 to 'x' in the global environment.
    print(x)

funct()
#10

x
#10
```




---
## Arguments

A **Function** can have _arguments_.
```python
def adder(a, b):
    return(a + b)

adder(1, 2)
#3
```

Using _arguments_ should be careful, because of its **data type**.  
If you don't you would encounter many _Errors_ & _Exceptions_.
```python
adder('q', 2)
#Trackback (most recent call last):'
#TypeError: Can't convert 'int' object to str implicitly
```





---
### Positional Arguments

The way to use _arguments_ depending on its **order**.
```python
def adder(string, num1, num2):
    print(string, ': ', num1 + num2)

adder('Result', 2, 3)
#'Result :  5'
```




---
### Keyword Arguments

The way to use _arguments_ depending on its keyword(parameter).(Don't need to keep _arguments_ in order!)  
When using _Keyword Arguments_, you can set default values.  
The default values should be **_Constants_**  
```python
def adder(srt=string, num1=1, num2=2):
    print(srt, ': ', num1 + num2)

adder(num1=4, str='Result')
#'Result :  6'
```

**_Keyword Arguments_** should be defined behind **_Positional Arguments_**.
This is correct:
```python
def func(a, b=1):
```
The following is wrong:
```python
def func(a=1, b):
```




---
### VarArges: Arbitrary Arguments Lists

Using **_\*_**, you can express variable numbers of **_Positional Arguments_**.  
At this time, ```*args```are gathered as a **_Tuple_**.  
It should be the end of the **_Positional Arguments_** lists.

* Example: ```*args```

```python
def printer(num1, num2, *args):
    print('num1:', num1)
    print('num2:', num2)
    print(args)

printer(2, 3, 4, 5, 7, 24)
num1: 2
num2: 3
(4, 5, 7, 24)   # a tuple
```

Using **_\*\*_**, you can express variable numbers of **_Keyword Arguments_**.  
At this time, ```*args```are gathered as a **_Dictionary_**.  
It should be the end of the **_Keword Arguments_** lists.

* Example: ```**kwargs```

```python
def printer(num1, num2=11, **args):
    print('num1:', num1)
    print('num2:', num2)
    print(kwargs)

printer(2, num2=4, num7=5, num8=7, num9=24)
num1: 2
num2: 4
{'num8': 7, 'num9': 24, 'num7': 5)   # a dict
```

* Order of Arguments: ```(arg, *args, kwarg, **kwargs)```

```python
def printer(num1, num2=11, **args):
    print('num1:', num1)
    print(args)
    print('num2:', num2)
    print(kwargs)

printer(1, 2, 3, num2=4, num7=5, num8=7, num9=24)
num1: 1
(2, 3)                              # a tuple
num2: 4
{'num8': 7, 'num9': 24, 'num7': 5)  # a dict
```




---
## Docstrings

For _Readability_, You can attach **_Documentation Strings_**.  
Just put the strings at the beginning of the function body; the first line of it!  


```python
def adder(a, b):
    'This function operates addition.'
    return(a + b)

adder(1, 2)
```

You can make multilined-Docstrings.
```python
def adder(a, b):
    '''
    This function
    operates
    addition.
    '''
    return(a + b)
```

**_Docstrings doesn't appear when the function is called.
```python
adder(1, 2)
3
```

To show **_Docstrings_**(if it exists), call the ```help()``` function.
```python
help(adder)
Help on function adder in module __main__:

adder(a, b)
    This function operates addition.
```

To show the raw **_Docstrings_**, call the ```__doc__``` variable.  
It is the internal name of **_Docstrings_** within the function.

```python
adder.__doc__
'This function operates addition.'

print(adder.__doc__)
'This function operates addition.'
```




---
# Advances in Functions  


## Functions as an _Object_

**_Functions_** can be **_Arguments_**.

```python
def adder(a, b):
    return a + b

def runfunc_and_double(func, a, b):
    res = func(a, b)
    return res * 2

runfunc_and_double(adder, 3, 5)
16 # res = adder(3, 5) = 3+5, and res*2 = 8*2 = 16
```




---
## Nested Functions(Inner Functions)

You can define a **_Function_** within another **_Function_**  
the inner Functions can access to the variables within the outer functions.

```python
def runfunc_and_mult(a, b, c):
    def adder(a, b):
        return a + b
    return adder(a, b) * c

runfunc_and_mult(3, 5, 4)
32 # 3+5 = 8, and 8*4 = 32
```




---
## Closures

* The Outer functions have the nested Functions.  
* The Nested Functions(the child functions) refer to the variables of the Outer Function(the parent functions).  
* The Outer Functions(the outer functions) return the Nested Functions(the child functions).  

When do you use **_Closure_**?  

* Not to use _Global Variables_.
* Keep & Hide the inner data.  




---
## Lambda Functions

Anonymous Functions of Python.  It generates & returns retults **_ONCE_**.  
It is the simple way to generate Functions. You can use **_Lambda Functions_** _temporarily_.  


```lambda``` takes one argument.
```python
[lambda arg: operation(arg)]
```

* Example
```python
numlist = [1, 2, 3, 4]

def editor(numbers, func):
    for i in numbers:
        print(func(i))

def plusone(num):
    return num + 1

editor(numlist, plusone)
2
3
4
5 
```

```lambda``` is more simple!

```python
numlist = [1, 2, 3, 4]

def editor(numbers, func):
    for i in numbers:
        print(func(i))

editor(numlist, lambda i: i+1)
2
3
4
5
```




---
## Generators

The Python Sequence Objects.  
It's _iterable_ so you can iterate through HUGE Sequences without creaating & storing the entire sequence in memory at once.  
```range()``` is the most famous generator in Python3.(```xrange()``` in Python2.  

Look at the custom ver. of ```range()```
```python
def myrnage(start, end, step):
    i = start
    while i < end:
        yield i
        i += step
```

It's a normal Function,  
and it returns a **_Generator Object_**.  
This function can show how **_Generator_** works.  
```yield``` Statements can throw out the output of ```i```, step by step, while the function is operating(the ```while``` Statement is looping).  



---
## Decorators

Using **_Decorators_**, you can modify existing functions without changing it.  
It's a _Function_ takes one function as input & returns another.

Let's define a **_Decorator_**
```python
def plusone(func):
    def function(*args):
        res = func(*args):
        print('res + 1:', res+1)
        return res+1
    return function
```

And then,  define a _normal Function_ and use the**_Decorator_**

* Case 1: without the Decorator
```python
def adder(a, b):
    return a+b

adder(1, 2)
3 # it returns 3
```

* Case 2: with the Decorator
```python
@plusone
def adder(a, b):
    return a+b

adder(1, 2)
res+1: 4 # print & +1 function: adder function was Decorated!
4         # return the Decoratsed result!
```


You can use multiple **_Decorators_**.  
The closer one decorates the function first.
```python
# Create another Decorator
def double(func):
    def function(*args):
        res = func(*args)
        print('res*2:', res*2)
        return res*2
    return function

@double
@plusone
def adder(a, b):
    return a+b

adder(1, 2)
res+1: 4 # 1. plusone Decorator
res*2: 8 # 2. double  Decorator
```

```python
@print_form
@double
def adder(a, b):
    return a+b

adder(1, 2)
res*2: 6 # 1. double  Decorator
res+1: 7 # 2. plusone Decorator
```

## Errors

## Exceptions

## Clean-up Actions
[↑ Up to the Top](#data-structure)






---
[← back to *Main Page*](https://github.com/dawkiny/Python3/blob/master/README.md)

