
*Based on <https://realpython.com/python-conditional-statements/>*

You now have quite a bit of Python code under your belt. Everything you have seen so far has consisted of sequential execution, in which statements are always performed one after the next, in exactly the order specified.

But the world is often more complicated than that. Frequently, a program needs to skip over some statements, execute a series of statements repetitively, or choose between alternate sets of statements to execute.

That is where control structures come in. A control structure directs the order of execution of the statements in a program (referred to as the program’s control flow).

Here’s what you’ll learn in this tutorial: You’ll encounter your first Python control structure, the if statement.

In the real world, we commonly must evaluate information around us and then choose one course of action or another based on what we observe:

If the weather is nice, then I’ll mow the lawn. (It’s implied that if the weather isn’t nice, then I won’t mow the lawn.)

In a Python program, the if statement is how you perform this sort of decision-making. It allows for conditional execution of a statement or group of statements based on the value of an expression.

## Introduction to the if Statement
We’ll start by looking at the most basic type of if statement. In its simplest form, it looks like this:

```
if *expr*:
    *statement*
In the form shown above:
```

*expr* is an expression evaluated in Boolean context, as discussed in the section on Logical Operators in the Operators and Expressions in Python tutorial.
*statement* is a valid Python statement, which must be indented. (You will see why very soon.)
If *expr* is true (evaluates to a value that is “truthy”), then *statement* is executed. If *expr* is false, then *statement* is skipped over and not executed.

Note that the colon (:) following *expr* is required. Some programming languages require <expr> to be enclosed in parentheses, but Python does not.

Here are several examples of this type of if statement:


```python
x = 0
y = 5
```


```python
if x < y:                            # Truthy
     print('yes')
```

    yes



```python
if y < x:                            # Falsy
     print('yes')
```


```python
if x:                                # Falsy
     print('yes')
```


```python
if y:                                # Truthy
     print('yes')
```

    yes



```python
if x or y:                           # Truthy
     print('yes')
```

    yes



```python
if x and y:                          # Falsy
     print('yes')
```


```python
if 'aul' in 'grault':                # Truthy
     print('yes')
```

    yes



```python
if 'quux' in ['foo', 'bar', 'baz']:  # Falsy
     print('yes')
```

## Blocks

So far, so good.

But let’s say you want to evaluate a condition and then do more than one thing if it is true:

If the weather is nice, then I will:

Mow the lawn
Weed the garden
Take the dog for a walk
(If the weather isn’t nice, then I won’t do any of these things.)

In all the examples shown above, each if *expr*: has been followed by only a single *statement*. There needs to be some way to say “If *expr* is true, do all of the following things.”

In Python indentation is used to define compound statements or blocks. In a Python program, contiguous statements that are indented to the same level are considered to be part of the same block.

Thus, a compound if statement in Python looks like this:

```
if *expr*:
    *statement*
    *statement*
    ...
    *statement*
*following_statement*
```

Read though the following. Predict what will be printed out. 


```python
if 'foo' in ['foo', 'bar', 'baz']:          
    print('Outer condition is true')        

    if 10 > 20:                             
        print('Inner condition 1')                

    print('Between inner conditions')       

    if 10 < 20:                             
        print('Inner condition 2')          

    print('End of outer condition')         
print('After outer condition')   
```

    Outer condition is true
    Between inner conditions
    Inner condition 2
    End of outer condition
    After outer condition


## Loops

Often you will need to do a bit of work repeatedly. The way to do this is through writing a loop. We can write a for loop in Python that goes through all the elements of a list.

In Python, a for loop is started with the keywords **for** and **in**, with a colon (**:**). Everything inside the for loop must be indented. 

You can loop though elements of a list


```python
l = ['apple', 'bannana', 'carrot']
for item in l:
    print(item[0])
```

    a
    b
    c


The range function makes a special kind of list of sequential numbers. The numbers start at 0 and go up to one less than the range you selected.


```python
for i in range(6):
    print(i**2)
```

    0
    1
    4
    9
    16
    25


Loops use blocks, just like if statements. To include multiple statements inside a loop, make sure they are all indented the same.


```python
primes = [2, 3, 5, 7]

for p in primes:
    prime_squared = p**2
    print(prime_squared)
```

    4
    9
    25
    49


Loops are useful when combined with if statements.


```python
for i in range(30):
    squared = i**2
    if squared < 50:
        print(i)

```

    0
    1
    2
    3
    4
    5
    6
    7


A common use of loops is to sum up values.


```python
numbers = [1,10,20,30,40,50]
s = 0
for number in numbers:
    s = s + number
print(s)
```

    151


1. Loop though the numbers 0 to 10, if the number is divisable by 2 print it (hint: look up the modulo function (%))
2. Here is a list of 5 names. If the length of the name is bigger than 5 print it.

['Mark',
'Mary',
'Maximilian',
'Mhairi',
'Mae']

3. Sum up the squares of the numbers from 0 to 20.


```python
# 1 

for i in range(11):
    if i % 2 == 0:
        print(i)
```

    0
    2
    4
    6
    8
    10



```python
# 2

names = ['Mark',
'Mary',
'Maximilian',
'Mhairi',
'Mae']

for name in names:
    if len(name) > 5:
        print(name)
```

    Maximilian
    Mhairi



```python
# 3

s = 0
for i in range(21):
    s = s + i**2
    
s
```




    2870


