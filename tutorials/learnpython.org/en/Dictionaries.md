Tutorial
--------

A dictionary is a data type similar to arrays, but works with keys and values instead of indexes. Each value stored in a dictionary can be accessed using a key, which is any type of object (a string, a number, a list, etc.) instead of using its index to address it.

For example, a database of phone numbers could be stored using a dictionary like this:

    phonebook = {}
    phonebook["John"] = 938477566
    phonebook["Jack"] = 938377264
    phonebook["Jill"] = 947662781
    print(phonebook)

Alternatively, a dictionary can be initialized with the same values in the following notation:

    phonebook = {
        "John" : 938477566,
        "Jack" : 938377264,
        "Jill" : 947662781
    }
    print(phonebook)

### Iterating over dictionaries

Dictionaries can be iterated over, just like a list. However, a dictionary, unlike a list, does not keep the order of the values stored in it. To iterate over key value pairs, use the following syntax:
    
    phonebook = {"John" : 938477566,"Jack" : 938377264,"Jill" : 947662781}
    for name, number in phonebook.items():
        print("Phone number of %s is %d" % (name, number))

### Removing a value

To remove a specified index, use either one of the following notations:
    
    phonebook = {
       "John" : 938477566,
       "Jack" : 938377264,
       "Jill" : 947662781
    }
    del phonebook["John"]
    print(phonebook)

or:
    
    phonebook = {
       "John" : 938477566,
       "Jack" : 938377264,
       "Jill" : 947662781
    }
    phonebook.pop("John")
    print(phonebook)

### Additional things to note

Since the key of a dictionary is like its index, it means that duplicate keys are not allowed. Doing so would just replace the existing key-value pair with the new one. You are also allowed to use nonprimitives as values in a dictionary. For example, a list assigned to a key would also be perfectly acceptable:

    phonebook = {
       "John" : [938477566, 938477563, 938477562],
       "Jack" : 938377264,
       "Jill" : 947662781
    }

You could even declare a class and have an object of that class assigned as a value to the JSON variable. This flexibility makes dictionaries a powerful tool that goes hand in hand with file formats such as JSON. You can easily convert a Python dictionary to JSON using `JSON.dumps()`, and the other way around with `json.load(file)`.

In addition to the dictionary methods mentioned above, there are a few other methods that might be worth considering. The `.get(<key>)` method can be used to get values when a key is provided. You could also pass in an additional parameter which will be returned as the default if the key doesn't exist in the dictionary. `.keys()` will return all the keys, `.values()` will return all the values, and the `dict1.update(dict2)` method will merge the values from `dict1` into `dict2`. The [documentation](https://python-reference.readthedocs.io/en/latest/docs/dict/) can provide a comprehensive list of usable methods.

Exercise
--------

Add "Jake" to the phonebook with the phone number 938273443, and remove Jill from the phonebook.

Tutorial Code
-------------

phonebook = {  
    "John" : 938477566,
    "Jack" : 938377264,
    "Jill" : 947662781
}  
# your code goes here

# testing code
if "Jake" in phonebook:  
    print("Jake is listed in the phonebook.")
    
if "Jill" not in phonebook:      
    print("Jill is not listed in the phonebook.")  


Expected Output
---------------

test_output_contains("Jake is listed in the phonebook.")
test_output_contains("Jill is not listed in the phonebook.")
success_msg("Nice work!")

Solution
--------

phonebook = {  
    "John" : 938477566,
    "Jack" : 938377264,
    "Jill" : 947662781
}  

# your code goes here
phonebook["Jake"] = 938273443  
del phonebook["Jill"]  

# testing code
if "Jake" in phonebook:  
    print("Jake is listed in the phonebook.")
    
if "Jill" not in phonebook:      
    print("Jill is not listed in the phonebook.")  
