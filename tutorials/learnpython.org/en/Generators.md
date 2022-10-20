Tutorial
--------

Generators are very easy to implement, but a bit difficult to understand.

Generators are used to create iterators, but with a different approach. Generators are simple functions which return an iterable set of items, one at a time, in a special way.

Before we get too deep into generators, let's take a look at the `yield` keyword.

### yield

First, note that the `yield` keyword and generators are bound. Declaring the yield keyword inside a method automatically makes that object a generator object. So what does `yield` do?

Imagine you were a data scientist, and you need to process a massive dataset. As you may know, these datasets can consist of millions of records, and the file itself can be a good couple of megabytes. This situation would be worse if you had to deal with several large datasets. Naturally, you would want to do something with this data, and not just print it out, meaning that you would probably want to pass the data into a function. However, putting all this data in a list that gets stored in memory can slow down both your program as well as the machine running it, and this is where `yield` shines.

Instead of doing this:

    def loop_file(file):
        for line in file:
            list.append(line)
        return list

where you have to store all the lines of the file inside a list, you can do this:

    def loop_file(file):
        for line in file:
            yield line

You can then call this function in the same way as calling a function that returned a list (such as the function in the former example):

    for line in loop_file(file):
        ...

But now, you have a much better-optimized program since you aren't passing around variables that hold megabytes of data. So what happens here?

When an iteration over a set of item starts using the for statement, the generator is run. Once the generator's function code reaches a "yield" statement, the generator yields its execution back to the for loop, returning a new value from the set. The generator function can generate as many values (possibly infinite) as it wants, yielding each one in its turn.

Here is a simple example of a generator function which returns 7 random integers:

      import random
      
      def lottery():
          # returns 6 numbers between 1 and 40
          for i in range(6):
              yield random.randint(1, 40)
      
          # returns a 7th number between 1 and 15
          yield random.randint(1, 15)
      
      for random_number in lottery():
             print("And the next number is... %d!" %(random_number))

This function decides how to generate the random numbers on its own, and executes the yield statements one at a time, pausing in between to yield execution back to the main for loop.

Exercise
--------

Write a generator function which returns the Fibonacci series. They are calculated using the following formula: The first two numbers of the series is always equal to 1, and each consecutive number returned is the sum of the last two numbers.
Hint: Can you use only two variables in the generator function? Remember that assignments can be done simultaneously. The code

    a = 1
    b = 2
    a, b = b, a
    print(a, b)

will simultaneously switch the values of a and b.

Tutorial Code
-------------

# fill in this function
def fib():
    pass #this is a null statement which does nothing when executed, useful as a placeholder.

# testing code
import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")

    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break



Expected Output
---------------

test_output_contains("Good, The fib function is a generator.")
success_msg('Good work!')

Solution
--------

# fill in this function
def fib():
    a, b = 1, 1
    while 1:
        yield a
        a, b = b, a + b

# testing code
import types
if type(fib()) == types.GeneratorType:
    print("Good, The fib function is a generator.")

    counter = 0
    for n in fib():
        print(n)
        counter += 1
        if counter == 10:
            break
