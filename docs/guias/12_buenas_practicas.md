# Buenas prácticas en python

## Virtualenv

```bash
virtualenv -p python venv
```

```bash
source venv/bin/activate
```

## IPython

```bash
pip install ipython
```

```bash
ipython
```

## Zen

```python
import this
```

```
# output
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

## Return multiple values

```python
def get_user(id):
    # fetch user from database
    name = "Fede" # Fake name
    birthdate = "01-01-2000" # Fake date
    return name, birthdate

name, birthdate = get_user(4)

print(name, birthdate)
```

```python
# output
Fede 01-01-2000
```

## One line if

```python
[on_true] if [expression] else [on_false]
```

```python
y = 2
result = "Success!" if (y == 2) else "Failed!"
print(result)
```

```python
# output
"Success!"
```

## Truth value testing

```python
true = True
false = False
true_value = "aaa"  # truthy
false_value = []  # falsey
none_value = None

# Bad:

if true == True:
    print("truthy")

if false == False:
    print("falsy")

# Good:

if true:
    print("truthy")

if true_value:
    print("truthy")

if not false:
    print("falsy")

if not false_value:
    print("falsy")

if none_value is None:
    print(None)
```

```
# output
truthy
falsy
truthy
truthy
falsy
falsy
None
```

## NO Globals

```python
c = 0

def add():
    global c
    c = c + 2
    print("Inside add():", c)

add()
print("In main:", c)
```

```
# output
Inside add(): 2
In main: 2
```

## Unpacking

```python
a = 1
b = 2
a, b = b, a
print(f"a: {a}")
print(f"b: {b}")
```

```
# output
a: 2
b: 1
```

```python
a, b = (1, 2)
print(f"a: {a}")
print(f"b: {b}")
```

```
# output
a: 1
b: 2
```

```python
a, b = [1, 2]
print(f"a: {a}")
print(f"b: {b}")
```

```
# output
a: 1
b: 2
```

```python
a, *b = [1,2,3]
print(f"a: {a}")
print(f"b: {b}")
```

```
# output
a: 1
b: [2, 3]
```

```python
a, *b, c = [1,2,3,4]
print(f"a: {a}")
print(f"b: {b}")
print(f"c: {c}")
```

```
# output
a: 1
b: [2, 3]
c: 4
```

## Merging dict

```python
dict1 = { "a": 1, "b": 2 }
dict2 = { "b": 3, "c": 4 }
merged = dict1 | dict2

print(merged)
```

```
# output
{'a': 1, 'b': 3, 'c': 4}
```

## Slicing a list

```python
a[start:stop:step]
```

`start`, `stop` y `step` son opcionales.
Si no los completas tendrán los siguientes valores por defecto:

- 0 para `start`
- el final de la lista para `end`
- 1 para `step`

```python
# We can easily create a new list from
# the first two elements of a list:
first_two = [1, 2, 3, 4, 5][0:2]
print(first_two)
```

```
# output
[1, 2]
```

```python
# And if we use a step value of 2,
# we can skip over every second number
# like this:
steps = [1, 2, 3, 4, 5][0:5:2]
print(steps)
```

```
# output
[1, 3, 5]
```

```python
# This works on strings too. In Python,
# you can treat a string like a list of
# letters:
mystring = "abcdefdn nimt"[::2]
print(mystring)
```

```
# output
aced it
```

## Enumerate

```python
# Bad
numbers = [2,4,6,8,10]
i = 0
for number in numbers:
  print(f"Item: #{number:02} at: {i}")
  i += 1
```

```
# output
Item: #02 at: 0
Item: #04 at: 1
Item: #06 at: 2
Item: #08 at: 3
Item: #10 at: 4
```

```python
# Good
numbers = [2,4,6,8,10]
for i, number in enumerate(numbers):
  print(f"Item: #{number:02} at: {i}")
```

```
# output
Item: #02 at: 0
Item: #04 at: 1
Item: #06 at: 2
Item: #08 at: 3
Item: #10 at: 4
```

## Zip

```python
numbers = [1, 2, 3]
words = ['one', 'two', 'three']

numbers_and_words = zip(numbers, words)

print(list(numbers_and_words))

# zip(numbers, words, strict=True) Probar!
```

```
# output
[(1, 'one'), (2, 'two'), (3, 'three')]
```

## Map

Map se utiliza generalmente cuando quiero aplicarle alguna transformación
a cada elemento de la lista, pero no alterar la cantidad de elementos.

```python
map(function, iterable)
```

```python
def upper(s):
    return s.upper()

words = list(map(upper, ['sentence', 'fragment']))
print(words)
```

```
# output
['SENTENCE', 'FRAGMENT']
```

```python
# With lambda
words = list(map(lambda x: x.upper(), ['sentence', 'fragment']))
print(words)
```

```
# output
['SENTENCE', 'FRAGMENT']
```

```python
# Convert a string representation of
# a number into a list of ints.
list_of_ints = list(map(int, "1234567"))
print(list_of_ints)
```

```
# output
[1, 2, 3, 4, 5, 6, 7]
```

## Filter

El filter se utiliza cuando quiero generalmente modificar la cantidad de
elementos de un iterable, pero no transformar cada elemento.

```python
filter(function, iterable)
```

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
filtered = filter(lambda x: x%3 == 0, numbers)
print(list(filtered))
```

```
# output
[3, 6, 9]
```

```python
numbers = [1, None, 2, 3, 4, None, 5, 6, 7, 8, 9]
filtered = filter(bool, numbers)
print(list(filtered))
```

```
# output
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Reduce

Se puede utilizar en distintos casos:

- Quiero sumarizar valores de un iterable
- Quiero generar un iterable bastante distinto en forma partiendo de otro

**Se recomienda no utilizarlo cuando se podría haber usado un filter o un map**

```python
reduce(function, iterable, init)
```

```python
from functools import reduce

numbers = (1, 4, 8, 18, 22)
print("a:", reduce(lambda acc, number: acc + number, numbers))

print("b:", reduce(lambda acc, number: number, numbers))
print("c:", reduce(lambda acc, number: acc, numbers))
# using reduce with initializer = 3
print("d:", reduce(lambda acc, number: acc + number, numbers, 3))
```

```
# output
a: 53
b: 22
c: 1
d: 56
```

```python
from functools import reduce

list_of_invitees = [
    {"email": "alex@example.com", "name": "Alex", "status": "attending"},
    {"email": "brian@example.com", "name": "Brian", "status": "declined"},
    {"email": "carol@example.com", "name": "Carol", "status": "pending"},
    {"email": "derek@example.com", "name": "Derek", "status": "attending"},
    {"email": "ellen@example.com", "name": "Ellen", "status": "attending"}
]

def invitee(acc, invitee):
  acc[invitee["name"]] = invitee["status"]
  return acc

result = reduce(invitee, list_of_invitees, {})
print(result)
```

```
# output
{'Alex': 'attending', 'Brian': 'declined', 'Carol': 'pending', 'Derek': 'attending', 'Ellen': 'attending'}
```

## List comprehension

Esta expresión nos permite hacer prácticamente lo mismo que un filter y un map
al mismo tiempo.

```python
[expression for item in list if condition]
```

```python
numbers = [i for i in range(10)]
print(numbers)
```

```
# output
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
squares = []
for x in range(10):
  squares.append(x**2)
print("a:", squares)
# --
squares = [x**2 for x in range(10)]
print("b:", squares)
```

```
# output
a: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
b: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

```python
def some_function(a):
    return (a + 5) / 2

my_formula = [some_function(i) for i in range(10)]
print(my_formula)
```

```
# output
[2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5, 6.0, 6.5, 7.0]
```

```python
filtered = [i for i in range(20) if i%2==0]
print(filtered)
```

```
# output
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

## Generators

Todas las funciones que vimos anteriormente son eficientes. Lo son porque
lo que terminan devolviendo internamente son generadores. Los generadores nos
permiten devolver parcialmente elementos en una iteración si tener que
procesar toda la estructura.

### Iterar hasta numeros muy grandes

```python
r = range(0, 100_000_000)
%time l = list(r)
```

```python
def g_range(start, end):
    n = start
    while True:
        yield n
        n += 1
        if n == end:
            break

gr = g_range(0, 100_000_000)
```

### Iterar infitinamente

```python
def all_even():
    n = 0
    while True:
        yield n
        n += 2
```

### Pipeline de generadores

```python
def fibonacci_numbers(nums):
    x, y = 0, 1
    for _ in range(nums):
        x, y = y, x+y
        yield x

def square(nums):
    for num in nums:
        yield num**2

print(sum(square(fibonacci_numbers(10))))
```

## Data classes

```python
from dataclasses import dataclass

@dataclass
class Card:
    rank: str
    suit: str

card = Card("Q", "hearts")

print("Equals?", card == card)
print("Rank:", card.rank)
print("Card:", card)
```

```
# output
Equals? True
Rank: Q
Card: Card(rank='Q', suit='hearts')
```

### Ejemplo para usar en el juego

```python
import PySimpleGUI as sg
from dataclasses import dataclass, field


@dataclass
class Event():
    name: str
    values: dict = field(default_factory=dict)


sg.theme('DarkAmber')    # Keep things interesting for your users

layout = [[sg.Text('Persistent window')],
          [sg.Input(key="-AGE-")],
          [sg.Input(key="-TEXT-")],
          [sg.Button('Read'), sg.Exit()]]

window = sg.Window('Window that stays open', layout)

while True:                             # The Event Loop
    event = Event(*window.read())
    print(event)

    match event:
        case Event(name='Read', values={"-AGE-": str(value)}) if int(value) < 18:
            print("ES MENOR de edad!")
        case Event(name='Read', values={"-NAME-": str(value)}):
            print(f"READ: {value}")
        case Event(name='Exit'):
            print("EXIT")
            break

window.close()
```

## Style guide

```python
pip install pycodestyle
```

## Auto-Formatting

```python
pip install black
```
