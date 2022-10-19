Tutorial
-----------------

Objects are an encapsulation of variables and functions into a single entity. Objects get their variables and functions from classes. Classes are essentially a template to create your objects.

A very basic class would look something like this:

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

We'll explain why you have to include that "self" as a parameter a little bit later.  First, to assign the above class(template) to an object you would do the following:

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()

Now the variable "myobjectx" holds an object of the class "MyClass" that contains the variable and the function defined within the class called "MyClass".

### Accessing Object Variables

To access the variable inside of the newly created object "myobjectx" you would do the following:

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()

    myobjectx.variable

So for instance the below would output the string "blah":

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()

    print(myobjectx.variable)

You can create multiple different objects that are of the same class(have the same variables and functions defined).  However, each object contains independent copies of the variables defined in the class.  For instance, if we were to define another object with the "MyClass" class and then change the string in the variable above:

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()
    myobjecty = MyClass()

    myobjecty.variable = "yackity"

    # Then print out both values
    print(myobjectx.variable)
    print(myobjecty.variable)


### Accessing Object Functions

To access a function inside of an object you use notation similar to accessing a variable:

    class MyClass:
        variable = "blah"

        def function(self):
            print("This is a message inside the class.")

    myobjectx = MyClass()

    myobjectx.function()

The above would print out the message, "This is a message inside the class."

### __init__()

The `__init__()` function, is a special function that is called when the class is being initiated.
It's used for assigning values in a class.

    class NumberHolder:
       
       def __init__(self, number):
           self.number = number
           
       def returnNumber(self):
           return self.number

    var = NumberHolder(7)
    print(var.returnNumber()) #Prints '7'

### self

Now let's get to the `self` parameter that you have been seeing in the above sections. This parameter is similar to the `this` keyword in most other programming languages and is used for the object to reference itself. However, you don't necessarily have to call the keyword `self`, and it can be called whatever you want. The only hard requirement is that it has to be the first parameter in the function definition. However, it is recommended to use `self` as it improves code readability. You can see this in use in the above section, where the `self.number` is being assigned in the `__init__` function. This means that the number parameter is getting assigned as a value in the currently referenced object.

Forgetting to place this parameter will throw an error. Let's take an example from above, but without the self parameter this time:

    class MyClass:
        variable = "blah"

        def function():
            print("This would not get printed.")

    myobjectx = MyClass()

    myobjectx.function()

When the `myobjectx.function()` is invoked, you get an error `"TypeError: function() takes 0 positional arguments but 1 was given"`. This might seem slightly strange to you, considering that you haven't passed an argument. While it may be true that you haven't passed in a parameter, the object itself gets automatically passed as a parameter to the function. So behind the scenes, there is 1 parameter getting passed in.

However, this behavior is different for static functions. You define a static function by placing the `@staticmethod` decorator above a function definition. Since static functions are shared among all objects of a class, Python does not automatically pass the object as a variable, meaning that you can have a static function inside a class without any parameters.

Now that you know about `self`, you might have a question. If you look at the code presented in the `__init__()` section, you might notice that the `__init__()` function also has a self parameter. While the `__init__()` function can be easily mistaken to be a constructor of this class, the existence of the `self` parameter in here disproves this. After all, you can't pass an object that hasn't been created yet. The `__init__()` function runs _after_ the object is initialized, and is where you would initialize the attributes of the object. The constructor is a method called `__new__()`, and is used to do the actual object creation. Like the other methods, it also has an implicitly passed parameter, which is the `cls` parameter (naming is the recommended standard and not mandatory). This is the class itself.

### Inheritence, encapsulation, polymorphism, etc...

Python, like other languges that support OOP, have OOP concepts. However, it does not have these concepts to the same level as languages such as Java happen to have. Let's first consider inheritence.

Inheritence allows child classes to inherit methods and properties from parent classes. In the same way that the child would extend the parent in Java, the child class would have the parent class as a parameter:

    class Parent:
        def __init__(self):
            ...

        def Func(self):
            ...

    class Child(Parent):
        ...

You can now call the functions defined in the parent class using an object in the child class:

    child = Child()
    child.Func()

Polymorphism also works in the same way as it does in ordinary OOP based languages, meaning that you could override `Func()` in the above code in you children classes, and have the children behave differently when `Func()` is called.

While inheritence has a pretty solid defintion in Python, encapsulation doesn't. In order to signify a protected member in a class you would use a convention where you prefix an underscore (_) to the variable, but this isn't enforced anywhere. To signify a private variable, you would use a double underscore (__). It is simply a convention which developers are supposed to respect unlike in other strictly type object oriented languages, where you would get a hard error if you tried to use the variable illegally.

Exercise
--------

We have a class defined for vehicles. Create two new vehicles called car1 and car2.
Set car1 to be a red convertible worth $60,000.00 with a name of Fer,
and car2 to be a blue van named Jump worth $10,000.00.

Tutorial Code
-------------

# define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str
# your code goes here

# test code
print(car1.description())
print(car2.description())

Expected Output
---------------

#test_output_contains('Fer is a red convertible worth $60000.00.')
#test_output_contains('Jump is a blue van worth $10000.00.')
success_msg("Great job!")

Solution
--------

# define the Vehicle class
class Vehicle:
    name = ""
    kind = "car"
    color = ""
    value = 100.00
    def description(self):
        desc_str = "%s is a %s %s worth $%.2f." % (self.name, self.color, self.kind, self.value)
        return desc_str

# your code goes here
car1 = Vehicle()
car1.name = "Fer"
car1.color = "red"
car1.kind = "convertible"
car1.value = 60000.00

car2 = Vehicle()
car2.name = "Jump"
car2.color = "blue"
car2.kind = "van"
car2.value = 10000.00

# test code
print(car1.description())
print(car2.description())
