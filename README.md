Download Link : https://programming.engineering/product/ve477-lab-2/

# -VE477-Lab-2-VE477-Lab-2
 🔍 VE477 Lab 2 VE477 Lab 2

1 C programming

Using the C standard library write efficient implementations of

    The Union-Find data structure.

    Kruskal’s algorithm.

    Prim’s algorithm for solving the Minimum Spanning Tree problem.

Consider the complexity of Kruskal and Prim algorithms and then compare how do they do perform in practice.

Hint: run the implementations on various types of graphs (size, sparse, dense…).

2 More advanced programming in Python

Modules

A module is a “Python library”, that is a file where some functions, variables, or classes are defined. The main difference with regular C or C++ libraries is that a module can also include some runnable function.

Using modules

    print(sqrt(9))

    print(math.cos(0))

3 # import a specific function into the current name space

4 from math import sqrt

    print(sqrt(9))

6 # import a whole module

7 import math

    print(dir(math))

    print(math.cos(0))

Writing modules

The following module is composed of the function leonardo and an if statement. The function returns all the Leonardo numbers less than n. In itself this function is enough to define the module which can later be imported. The last three lines however allows the function to be directly called from the command line and arguments passed to it.

Leonardo numbers (leo.py)

    #!/usr/bin/python3

2

3 def leonardo(n):

    a, b = 1, 1

    seq=[a]

    while b < n:

    seq.append(b)

    a,b = b, a + b + 1

    return seq

10

11 if __name__ == “__main__”:

    import sys

    print(leonardo(int(sys.argv[1])))

Running from the command line.

sh $ python3 leo.py 1000

Using as a module.

1 import leo

    leo.leonardo(1000)

    print(dir(leo))

Object oriented programming in Python

In Python the type of an object is represented by the class used to build the object.

Types

    a=3; b=5.0

2 type(a); type(b)

Classes

More than one class can be implemented in a .py file. New keywords starting with “@” can be used to simplify and clarify the class implementation.

Base room class (room.py)

1
	

#!/usr/bin/python3

2
	

    class Room:

4
	

# attributes common to all instances

5
	

windows = 2

6
	

color = ‘white’

7
	

8
	

# constructor

9
	

def __init__(self, name, size, status):

10
	

self.name = name

11
	

self.size = size

12
	

self.status = status

13
	

14
	

# methods common to all instances

15
	

@classmethod

16
	

def paint(cls, color):

17
	

cls.color = color

18
	

print(cls.color)

19
	

20
	

# methods called without reference to the class or the instance

21
	

@staticmethod

22
	

def knock():

23
	

print(“Anybody here?”)

24
	

25
	

# transforms a method into a read-only attribute (get)

26
	

@property

27
	

def size(self):

28
	

return self.name + ‘ is ‘ + str(self._size) + ‘ square meters’

29
	

30
	

# allows to set the previous read-only attribute

31
	

# without it, it would be impossible to set the size attribute

32
	

@size.setter

33
	

def size(self, size):

34
	

self._size = size

35
	

36
	

# allows to delete the property, which can be set again later

37
	

@size.deleter

38
	

def size(self):

39
	

del self._size

40
	

41
	

# methods

    def open(self):

    self.status = ‘open’

44

    def lock(self):

    self.status = ‘locked’

Example usage of the Room class.

1 from room import Room

    b=Room(‘bedroom’,10,‘open’)

    b.size; b.size=200; b.size

    b.status; b.lock(); b.status

    b.knock()

    l=Room(‘living room’,20,‘open’)

7 # color is a class attribute

    b.color; l.color; Room.color=‘red’; b.color; l.color

9 # color can be adjusted for each instance

    b.color=‘green’; b.color; l.color

Inheritance

In Python inheritance works as usual.

Panic room class (panicroom.py)

    #!/usr/bin/python3

2

3 from room import Room

4 from random import randint

5

    class PanicRoom(Room):

7

    solidity = 0

9

    def ZombyAttack(self):

    strength = randint(0,100)

    if strength > self.solidity:

    print(self.name + ‘ is compromise, run!’)

    else:

    print(self.name + ‘ is safe, stay in here!’)

Example usage of the PanicRoom class.

1 from panicroom import PanicRoom

    p=PanicRoom(‘secret hidden room’,8,‘locked’)

    p.size

4 p.solidity=50; p.ZombyAttack()

    p.open()

        3 echo(5)

        4 echo(‘test’)

        5 echo([‘one’, ‘two’, ‘three’])

        From a C++ perspective the echo function has not been defined for all those data types so this should not be working. However the approach taken in Python is to assume the defined function is universal and does the same thing regardless of the data type.

        In Python instead of covering all the cases that might arise, the problem is delegated to the data, expecting it to perform the correct operation. For instance when adding two numbers there is no need to define the function for all the possible combination of input data type (e.g. int + float, int + int, float + complex…).

        This is well illustrated by the implementation of the + operator: when a+b is called, a.__add__(b) is executed.

        2

        return a

        16

        17 # redefinition of open()

        18

        def open(self):

        19

        ans=input(‘Are you sure this is a good idea? (y/n) ‘)

        20

        if ans == ‘y’:

        21

        self.status = ‘open’

        The Python approach to polymorphism is much different than the one of C++.

        1 def echo(a):

        15

        print(self.name + ‘ is safe, stay in here!’)

        14

        else:

        10

        def ZombyAttack(self):

        11

        strength = randint(0,100)

        12

        if strength > self.solidity:

        13

        print(self.name + ‘ is compromise, run!’)

        8

        9

        solidity = 0

        Polymorphism

        Polymorphism is extremely simple to realise in Python.

        Panic room class (panicroom_poly.py)

        1 #!/usr/bin/python3

        2

        3 from room import Room

        4 from random import randint

        5

        6 class PanicRoom(Room):

        7

    a=3; b=4; a.__add__(b)

    a=3.0; b=4; a.__add__(b)

    a=3; b=4.0; a.__add__(b)

In particular this explains why functions do not need to specify their input and output data types.

Error handling

When coding in Python it is common directly access attributes or methods without first checking their existence. This is consistent with the polymorphism approach described in the previous section.

In case something goes wrong as exception is raise. This can be easily and cleanly handle as follows.

1 def length(a):

    try:

    len(a)

    except TypeError:

    print(“len not supported by this data type”)

6 # run if everything went well

    else:

    print(len(a))

9 # always run

    finally:

    print(“clean up resources here”)

    # strings and lists have a length

    length(‘abcdefg’)

    length([1,2,3,4])

    # integers do not have a length

    length(1)

Raised exception can be of various types such as ttributeError, TypeError, NameError and IndexError.

More Python

Explain how to use:

When running python3 from the command line, the help() function can be used to access a description of functions and keywords. More information can be found in the official Python 3 documentation.

The webpage 15 Essential Python Interview Questions considers interesting points to test your knowledge and understanding of Python.
