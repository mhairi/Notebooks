
### Basic List Comprehensions

Before we get into the details of sentiment analysis, we're going to cover a Python concept that wasn't covered in unit one: list comprehensions. They are a somewhat advanced topic, but they make much of the code in the next units easier to read and understand.

Basically, a list comprehension is a short-hand way of writing a loop in Python. They are particularly useful when you would normally write a loop which adds elements into a list. The best way to understand them is though examples. For each type of list comprehension we will show you an example with a loop, and then show you the same code done with a list comprehension.

Below we have code which makes a list of all the square numbers up to 100. You need to start by creating and empty list and then filling it inside a loop with append.


```python
squares = []

for i in range(11):
    squares.append(i**2)
    
squares
```




    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]



Now you can see the same list, created with a list comprehension. Note that you start with the code that was inside the loop and then have the same for statement afterwards. Everything is wrapped in a list


```python
[i**2 for i in range(11)]
```




    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]



### If-statements in list comprehensions

Below is a loop that creates a list of numbers which are divisible by 8. This is more complicated that our first loop because it includes an if-statement.


```python
multiples_of_8 = []

for i in range(101):
    
    if i % 8 == 0:
        multiples_of_8.append(i)
        
multiples_of_8
```




    [0, 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96]



If you want to use an if-statement inside a list comprehension, it comes after the loop part.


```python
[i for i in range(101) if i % 8 == 0]
```




    [0, 8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96]



### Nested list comprehensions

Below we have code that combines 'Hello' or 'Goodbye' with a name and adds it to a list. It does this though a nested loop: we start by looping through the first word and then we loop through all the names. This gives us every combination of first word and name.


```python
greetings = []

for start in ['Hello', 'Goodbye']:
    for name in ['Chris', 'Mhairi', 'Roseanne']:
        
        greeting = start + ' ' + name
        greetings.append(greeting)

greetings
```




    ['Hello Chris',
     'Hello Mhairi',
     'Hello Roseanne',
     'Goodbye Chris',
     'Goodbye Mhairi',
     'Goodbye Roseanne']



This can be done much more compactly with a list comprehension. If you have one loop after the other, they will nest.


```python
[start + ' ' + name for start in ['Hello', 'Goodbye'] for name in ['Chris', 'Mhairi', 'Roseanne']]
```




    ['Hello Chris',
     'Hello Mhairi',
     'Hello Roseanne',
     'Goodbye Chris',
     'Goodbye Mhairi',
     'Goodbye Roseanne']



### Dictionary comprehensions

As well as list comprehensions, you can also write dictionay comprehensions. These work the same way and can use if statements and nested loops. The only difference is that you enclose everything in curly brackets instead of square brackets. 

Below is an example of creating a dictionary where the keys are numbers, and the values are the the ordinal number description of the key.


```python
ordinal_dict = {}

for i in range(4, 11):
    ordinal_dict[i] = str(i) + 'th'

ordinal_dict
```




    {4: '4th', 5: '5th', 6: '6th', 7: '7th', 8: '8th', 9: '9th', 10: '10th'}



Below is an example of the same dictionary, made using a dictionary comprehension.


```python
{i:str(i) + 'th' for i in range(4, 11)}
```




    {4: '4th', 5: '5th', 6: '6th', 7: '7th', 8: '8th', 9: '9th', 10: '10th'}



Excercise

Write the following loops as a list comprehensions

1.


```python
primes = []
for i in range(2, 100):
    if i % 2 != 0 and i % 3 != 0 and i % 5 != 0 and i % 7 !=0 and i % 11 != 0:
        primes.append(i)
```


```python
[i for i in range(2, 100) if i % 2 != 0 and i % 3 != 0 and i % 5 != 0 and i % 7 !=0 and i % 11 != 0]
```




    [13,
     17,
     19,
     23,
     29,
     31,
     37,
     41,
     43,
     47,
     53,
     59,
     61,
     67,
     71,
     73,
     79,
     83,
     89,
     97]



2.


```python
times_tables = {}

for i in range(1, 13):
    for j in range(1, 13):
        if i <= j:
            times_tables[str(i) + ' x ' + str(j)] = i*j

times_tables
```




    {'1 x 1': 1,
     '1 x 2': 2,
     '1 x 3': 3,
     '1 x 4': 4,
     '1 x 5': 5,
     '1 x 6': 6,
     '1 x 7': 7,
     '1 x 8': 8,
     '1 x 9': 9,
     '1 x 10': 10,
     '1 x 11': 11,
     '1 x 12': 12,
     '2 x 2': 4,
     '2 x 3': 6,
     '2 x 4': 8,
     '2 x 5': 10,
     '2 x 6': 12,
     '2 x 7': 14,
     '2 x 8': 16,
     '2 x 9': 18,
     '2 x 10': 20,
     '2 x 11': 22,
     '2 x 12': 24,
     '3 x 3': 9,
     '3 x 4': 12,
     '3 x 5': 15,
     '3 x 6': 18,
     '3 x 7': 21,
     '3 x 8': 24,
     '3 x 9': 27,
     '3 x 10': 30,
     '3 x 11': 33,
     '3 x 12': 36,
     '4 x 4': 16,
     '4 x 5': 20,
     '4 x 6': 24,
     '4 x 7': 28,
     '4 x 8': 32,
     '4 x 9': 36,
     '4 x 10': 40,
     '4 x 11': 44,
     '4 x 12': 48,
     '5 x 5': 25,
     '5 x 6': 30,
     '5 x 7': 35,
     '5 x 8': 40,
     '5 x 9': 45,
     '5 x 10': 50,
     '5 x 11': 55,
     '5 x 12': 60,
     '6 x 6': 36,
     '6 x 7': 42,
     '6 x 8': 48,
     '6 x 9': 54,
     '6 x 10': 60,
     '6 x 11': 66,
     '6 x 12': 72,
     '7 x 7': 49,
     '7 x 8': 56,
     '7 x 9': 63,
     '7 x 10': 70,
     '7 x 11': 77,
     '7 x 12': 84,
     '8 x 8': 64,
     '8 x 9': 72,
     '8 x 10': 80,
     '8 x 11': 88,
     '8 x 12': 96,
     '9 x 9': 81,
     '9 x 10': 90,
     '9 x 11': 99,
     '9 x 12': 108,
     '10 x 10': 100,
     '10 x 11': 110,
     '10 x 12': 120,
     '11 x 11': 121,
     '11 x 12': 132,
     '12 x 12': 144}




```python
{str(i) + ' x ' + str(j) : i*j for i in range(1, 13) for j in range(1, 13) if i < j}
```




    {'1 x 2': 2,
     '1 x 3': 3,
     '1 x 4': 4,
     '1 x 5': 5,
     '1 x 6': 6,
     '1 x 7': 7,
     '1 x 8': 8,
     '1 x 9': 9,
     '1 x 10': 10,
     '1 x 11': 11,
     '1 x 12': 12,
     '2 x 3': 6,
     '2 x 4': 8,
     '2 x 5': 10,
     '2 x 6': 12,
     '2 x 7': 14,
     '2 x 8': 16,
     '2 x 9': 18,
     '2 x 10': 20,
     '2 x 11': 22,
     '2 x 12': 24,
     '3 x 4': 12,
     '3 x 5': 15,
     '3 x 6': 18,
     '3 x 7': 21,
     '3 x 8': 24,
     '3 x 9': 27,
     '3 x 10': 30,
     '3 x 11': 33,
     '3 x 12': 36,
     '4 x 5': 20,
     '4 x 6': 24,
     '4 x 7': 28,
     '4 x 8': 32,
     '4 x 9': 36,
     '4 x 10': 40,
     '4 x 11': 44,
     '4 x 12': 48,
     '5 x 6': 30,
     '5 x 7': 35,
     '5 x 8': 40,
     '5 x 9': 45,
     '5 x 10': 50,
     '5 x 11': 55,
     '5 x 12': 60,
     '6 x 7': 42,
     '6 x 8': 48,
     '6 x 9': 54,
     '6 x 10': 60,
     '6 x 11': 66,
     '6 x 12': 72,
     '7 x 8': 56,
     '7 x 9': 63,
     '7 x 10': 70,
     '7 x 11': 77,
     '7 x 12': 84,
     '8 x 9': 72,
     '8 x 10': 80,
     '8 x 11': 88,
     '8 x 12': 96,
     '9 x 10': 90,
     '9 x 11': 99,
     '9 x 12': 108,
     '10 x 11': 110,
     '10 x 12': 120,
     '11 x 12': 132}



