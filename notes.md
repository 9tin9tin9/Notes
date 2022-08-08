# Programming teaching notes

## Table of Contents
1. [Statements and Expressions](#statements-and-expressions)
2. [Common Object Types](#common-object-types)
    1. [Numbers, Operators, Variables](#numbers-operators-variables)
    2. [Strings](#strings)
    3. [Lists](#lists)
5. [Control Flow](#control-flow)
    1. [Boolean Values, Comparison Operators, Boolean Operators](#booleans)
    2. [Code Blocks in Python](#code-blocks-in-python)
    3. [`if` Statement](#if-statement)
    4. [`while` Statement](#while-statement)

## Statements and Expressions

Programming is all about doing instructions, and there are mainly 2 kinds of instructions: Expression and statement.

Expressions are instructions that the interpreter evaluate and return something.<br>
`1+1` returns `2`<br>
`5*(2+3)` returns `25`<br>
`0.3/4.5` returns `0.06666666666666667`

Statements are instructions that the interpreter executes and does not return something. Statements are usually used for controlling the flow of programming (conditionals, loops). Eg `if...elif...else`, `while`, `for`
```python
If time == "morning":
    print("Good morning")
else:
    print("Hello")
```
If it is morning, print "Good morning"; if not, print "hello".
```python
while count < 10:
    count = count + 1
```
While `count` is less than `10`, add one to `count` and assign the result to `count`<br>
Or<br>
Increment `count` by one as long as `count` is less than `10`

Programming basically is problem solving. You encounter a problem, and you tell the machine to solve the problem according to instructions(program) given to it.

## Common Object Types

<a name="numbers-operators-variables"></a>
### Numbers, Operators, Variables

First try something simple. Lets use python as a calculator. Start a python interpreter and type `1 + (2 * 3) / 4 - 10` You should see something like:
```python
>>> 1 + (2 * 3) / 4 - 10
-7.5
```
Same syntax as the calculator you always use (before) except you use `/` for division. Division always return a floating point number You may expect the result of `6 / 3` is `2`.<br>
But in python's case:
```python
>>> 6 / 3
2.0
```
`2.0` is not `2` in python(and in most other languages) because they have different types. `2` is an integer but `2`.0 is a float (number that has decimal).

Some other operators
- power: `**`
- floor division that discards the fractional part: `//`
- modulo: `%`
```python
>>> 5 ** 3
125
>>> 17 // 3
5
>>> 17 % 3
2
```
You store the result of expressions into variables by assign the result to a name (without space) using `=`.
```python
>>> width = 10
>>> height = 83 + 14
```
And using the variables just like in a calculator.
```python
>>> width * height
970
```
However unlike the calculator that variables are predefined (A, B, C, D, X, Y, M), you define variables yourself. Therefore you have to be careful if you are trying to use undefined variables. You if try to use undefined variables, your program will crash during run time (when the programming is running) and the interpreter will complain about that
```python
>>> obviously_undefined_variable
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'obviously_undefined_variable' is not defined
```
> The three lines after `>>>` are error message printed by the interpreter.

There are also some rules for naming python variables:
- A variable name must start with a letter or the underscore character;
- A variable name cannot start with a number;
- A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ );
- Variable names are case-sensitive (age, Age and AGE are three different variables).

### Strings

Strings are a sequence of characters. In python, strings are either enclosed in single quotes (`'...'`) or double quotes (`"..."`). If you want to use single quotes or double quotes inside a string, escape it by adding back slash `\` before them.
```python
>>> 'spam eggs' 
'spam eggs'
>>> 'doesn\'t'
"doesn't"
```
Or
```python
>>> "doesn't" 
"doesn't"
>>> 'he said: "Hi"'
'he said: "Hi"'
```
You can use the `print()` function to print values, variables and strings.
```python
>>> print(10)
10
>>> print('123')
123
```
You cannot separate strings inside a pair of quotes into multiple lines.
To tell python to print the following characters in the next line, use `\n`.
```python
>>> print('first line\nsecond line')
first line
second line
```
You could use a bunch of `\n` to format strings.
```python
>>> print("first line\n  indented second line\n\n    indented fourth line")
first line
  indented second line

    indented fourth line
```
But the string is ugly and difficult to read. Instead, you could use triple-quotes: `"""..."""` or `'''...'''`. String literals are allowed to span multiple lines inside these and new lines (formats) are retained.
```python
>>> print("""first line
  Indented second line

    Indented forth line""")
first line
  Indented second line

    Indented fourth line
```
A back slash followed by a character inside a string is called an escape sequence. A back slash is always interpreted as the beginning of an escape sequence and will not be printed. To print a back slash, escape the back slash.
```python
>>> print("\\")
\
```
Strings are very useful when you want to print something to the console when the interpreter is executing a script (a file of program).

Operators can also be applied on strings
```python
>>> 3 * 'um' + '...err'
'umumum...err'
```
Two or more strings will be automatically concatenated.
```python
>>> 'Hello' 'World'
'HelloWorld'
>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
```
Note that the three dots on the second line are printed by the interpreter. Also note that this cannot be applied to variables. To concatenate variables, use the `+` operator.
```python
>>> prefix = 'first '
>>> suffix = 'last'
>>> prefix + suffix
'first last'
```

### Lists

Lists are a collection of data having the same data type. It is written as a list of comma separated values `/` items between square brackets.
```python
>>> prime_numbers = [2, 3, 5, 7, 11]
```
Each item inside a list have an index, and the index starts with zero. You retrieve the data by indexing the list. You do that by adding the index surrounded by square brackets after the list variable.
```python
>>> prime_numbers[0]
2
>>> prime_numbers[1]
3
>>> prime_numbers[3]
7
```
Negative index means start counting from the right. Index `-1` means getting the last item in a list.
```python
>>> prime_numbers[-1]
11
>>> prime_numbers[-2]
7
>>> prime_numbers[-5]
2
```
You can get part of the list by slicing it.
```python
>>> prime_numbers[0:3] # beginning from index 0 (included) to index 3 (excluded)
[2, 3, 5]
>>> prime_numbers[2:4]
[5, 7]
>>> prime_numbers[:4] # omitting left hand side of colon: beginning from index 0 (included) to index 4 (excluded)
[2, 3, 5, 7]
>>> prime_numbers[3:] # omitting right hand side of colon: beginning from index 3 (included) to the end
[7, 11]
>>> prime_numbers[-2:] # from second last item (included) to the end
[7, 11]
```
Same as strings, you can concatenate lists using `+` operator.
```python
>>> prime_numbers[:2] + prime_numbers[2:]
[2, 3, 5, 7, 11]
>>> prime_numbers[1:3] + [2, 4, 6]
[3, 5, 2, 4, 6]
```
One thing to note, `#` is used to comment code. Which means characters after `#` are ignored by the interpreter.
```python
very_difficult_code() # useful explanation, ignored by interpreter
```
Indices should always be a valid number. i.e. 0 <= index < length of list. Otherwise you will encounter a run time error.
```python
>>> prime_numbers[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```
To get the length of a list or a string, use the `len()` function.
```python
>>> long_string = 'supercalifragilisticexpialidocious'
>>> len(long_string)
34
>>> len(prime_numbers)
5
```
This is useful not only to get the length of list but also prevent yourself from out of bounds indexing.

Strings are in fact lists of characters. Therefore indexing and slicing can also be done on strings using the same syntax.

## Control Flow

Control flows are statemens that controls the flow of program.<br>
Diving into control flows, let's first introduce boolean values.

<a name="booleans"></a>
### boolean values, comparison operators, boolean operators

A boolean value is either `True` or `False`. To get such value, you use either comparison operators or boolean operators.

Comparison operators are binary operators
```python
>>> 1 < 2 # smaller than
True
>>> 0 == 0 # equal to
True
>>> 1 > 2 # larger than
False
>>> 1 >= 2 # larger or equal to
False
>>> 1 <= 2 # smaller or equal to
True
```
Boolean operators: `and`, `or`, `not`
```python
>>> True and True
True
>>> True or False
True
>>> not True
False
```
Conventially `0` is means `False` and `1` is means `True`.<br>
Here is a truth table for your reference to see what boolean operators returns depending on operands:
`A operator B => result`
| A | B |    | and | or |
| - | - | -  | --- | -- |
| 0 | 0 | => | 0   | 0  |
| 0 | 1 | => | 0   | 1  |
| 1 | 0 | => | 0   | 1  |
| 1 | 1 | => | 1   | 1  |

**VERY IMPORTANT**:<br>
`and` `or` `not` have different precedence.<br>
`not` evaluates first, next `and`, lastly `or`.
```python
>>> a = False
>>> b = True
>>> not a and b or a # -> ((not a) and b) or a
True
>>> a and b or not a # -> (a and b) or (not a)
True
```

Now you know what is boolean, next lets see code blocks in Python

### Code Blocks in Python

Code blocks are lines of code with indentation (tabs or spaces). Indentation is part of the syntax in Python. Usually people use 2 spaces or 4 spaces as indentation. You must keep the indetation in the same level of code block the same, and more indentation in the next level of code block.
```python
normal code
    first level of indentation
    still first level
        second level of indentation
            third level of indentation
            third level...
```

Now you know what is boolean and code block, let's explain `if` statements

## `if` statement

The syntax of `if` statement is:
```
if <boolean expression>:
    code block
elif <boolean expression>:
    code block
else:
    code block
```

Let's see an example
```python
>>> x = 20
>>> if x < 0:
...     print("Negative number")
... elif x == 0:
...     print("Zero")
... elif x == 1:
...     print("One")
... else:
...     print("More")
More
```
There is a lot going on here. Lets break it down.
1. Variable `x` is declared and initialised with an integer `20`
2. The program checks `x` if it meets any of the following conditions in order
    1. if `x` is smaller than 0
        * print "Negative number"
    2. if `x` is equal to 0
        * print "Zero"
    3. if `x` is equal to 1
        * print "One"
    4. if none of the above conditions is true
        * print "More"

If one of the conditions is satisfied, the rest of the code is not evaludated, including the conditions. For example, let's say `x` is 0:
1. Python checks if `x` is smaller than 0 (False)
2. Python checks if `x` equals 0 (True)
3. Prints Zero
4. The rest of the if statement won't be executed

## `while` statement
