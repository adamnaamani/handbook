# Python

"It was designed with an emphasis on code readability, and its syntax allows programmers to express their concepts in fewer lines of code."

"Python is the main dynamic language used at Google."

"Used at NASA, Quora, Amazon, Reddit, Netflix, Dropbox, and Instagram."

## Table of Contents
1. [pip3](#pip3)
1. [python3](#python3)
1. [Django](#Django)
    1. [Shortcuts](#shortcuts)
1. [Field Types](#field-types)
1. [Init](#init)
1. [Templates](#templates)
1. [Functions](#functions)
1. [Methods](#methods)
1. [Objects](#objects)
1. [Filter](#filter)
1. [Tuples](#tuples)

## pip3
```bash
pip3 install virtualenvwrapper
pip3 install django
```

## python3
```bash
python3 -m django --version
python3 manage.py makemigrations
python3 manage.py migrate
python3 manage.py startapp <name>
python3 manage.py createsuperuser
```

## Django
```bash
django-admin startproject <name>
```

### Shortcuts
Commands to shorten `python3 manage.py` scripts:
```bash
$ pip3 install django-shortcuts
$ django <command or shortcut>
```
```bash
# Django
'c'  : 'collectstatic',
'r'  : 'runserver',
'sd' : 'syncdb',
'sp' : 'startproject',
'sa' : 'startapp',
't'  : 'test',

# Shell
'd'  : 'dbshell',
's'  : 'shell',

# Auth
'csu': 'createsuperuser',
'cpw': 'changepassword',

# South
'm'  : 'migrate',
'mm' : 'makemigrations',
'sm' : 'schemamigration',
'dm' : 'datamigration',

# Haystack
'ix' : 'update_index',
'rix': 'rebuild_index',

# Django Extensions
'sk' : 'generate_secret_key',
'rdb': 'reset_db',
'rp' : 'runserver_plus',
'shp': 'shell_plus',
'url': 'show_urls',
'gm' : 'graph_models',
'rs' : 'runscript'
```

## Field Types
* **`CharField`**  
Used to define short-to-mid sized fixed-length strings. You must specify the `max_length` of the data to be stored.
* **`TextField`**  
Used for large arbitrary-length strings. You may specify a max_length for the field, but this is used only when the field is displayed in forms (it is not enforced at the database level).
* **`IntegerField`**  
Field for storing integer (whole number) values, and for validating entered values as integers in forms.
* **`DateField`** and **`DateTimeField`**  
Used for storing/representing dates and date/time information (as Python `datetime.date` in and `datetime.datetime` objects, respectively). These fields can additionally declare the (mutually exclusive) parameters `auto_now=True` (to set the field to the current date every time the model is saved), `auto_now_add` (to only set the date when the model is first created) , and default (to set a default date that can be overridden by the user).
* **`EmailField`**  
Used to store and validate email addresses.
* **`FileField`** and **`ImageField`**  
Used to upload files and images respectively (the **`ImageField`** simply adds additional validation that the uploaded file is an image). These have parameters to define how and where the uploaded files are stored.
* **`AutoField`**  
A special type of **`IntegerField`** that automatically increments. A primary key of this type is automatically added to your model if you don’t explicitly specify one.
* **`ForeignKey`**  
Used to specify a one-to-many relationship to another database model (e.g. a car has one manufacturer, but a manufacturer can make many cars). The "one" side of the relationship is the model that contains the "key" (models containing a "foreign key" referring to that "key", are on the "many" side of such a relationship).
* **`ManyToManyField`**  
Used to specify a many-to-many relationship (e.g. a book can have several genres, and each genre can contain several books). In our library app we will use these very similarly to **`ForeignKeys`**, but they can be used in more complicated ways to describe the relationships between groups. These have the parameter `on_delete` to define what happens when the associated record is deleted (e.g. a value of `models.SET_NULL` would simply set the value to `NULL`).

## Init
Marks directories as Python package directories:
```python
directory/__init__.py
directory/module.py
```
Importing:
```python
import directory.module

# or

from directory import module
```
  
## Templates  
Django will automatically look for `.html` templates in a directory named `/templates/` in your application.

## Functions
The Python interpreter supports many functions that are built-in: sixty-eight, as of Python 3.6.

### Math
| Function | Description                                                         |
|----------|---------------------------------------------------------------------|
| abs()    | Returns absolute value of a number                                  |
| divmod() | Returns quotient and remainder of integer division                  |
| max()    | Returns the largest of the given arguments or items in an iterable  |
| min()    | Returns the smallest of the given arguments or items in an iterable |
| pow()    | Raises a number to a power                                          |
| round()  | Rounds a floating-point value                                       |
| sum()    | Sums the items of an iterable                                       |

### Type Conversion
| Function  | Description                                                          |
|-----------|----------------------------------------------------------------------|
| ascii()   | Returns a string containing a printable representation of an object  |
| bin()     | Converts an integer to a binary string                               |
| bool()    | Converts an argument to a Boolean value                              |
| chr()     | Returns string representation of character given by integer argument |
| complex() | Returns a complex number constructed from arguments                  |
| float()   | Returns a floating-point object constructed from a number or string  |
| hex()     | Converts an integer to a hexadecimal string                          |
| int()     | Returns an integer object constructed from a number or string        |
| oct()     | Converts an integer to an octal string                               |
| ord()     | Returns integer representation of a character                        |
| repr()    | Returns a string containing a printable representation of an object  |
| str()     | Returns a string version of an object                                |
| type()    | Returns the type of an object or creates a new type object           |

### Iterables and Iterators
| Function    | Description                                                             |
|-------------|-------------------------------------------------------------------------|
| all()       | Returns True if all elements of an iterable are true                    |
| any()       | Returns True if any elements of an iterable are true                    |
| enumerate() | Returns a list of tuples containing indices and values from an iterable |
| filter()    | Filters elements from an iterable                                       |
| iter()      | Returns an iterator object                                              |
| len()       | Returns the length of an object                                         |
| map()       | Applies a function to every item of an iterable                         |
| next()      | Retrieves the next item from an iterator                                |
| range()     | Generates a range of integer values                                     |
| reversed()  | Returns a reverse iterator                                              |
| slice()     | Returns a slice object                                                  |
| sorted()    | Returns a sorted list from an iterable                                  |
| zip()       | Creates an iterator that aggregates elements from iterables             |

### Composite Data Type
| Function    | Description                                                              |
|-------------|--------------------------------------------------------------------------|
| bytearray() | Creates and returns an object of the bytearray class                     |
| bytes()     | Creates and returns a bytes object (similar to bytearray, but immutable) |
| dict()      | Creates a dict object                                                    |
| frozenset() | Creates a frozenset object                                               |
| list()      | Constructs a list object                                                 |
| object()    | Returns a new featureless object                                         |
| set()       | Creates a set object                                                     |
| tuple()     | Creates a tuple object                                                   |

### Classes, Attributes, and Inheritance
| Function      | Description                                                                     |
|---------------|---------------------------------------------------------------------------------|
| classmethod() | Returns a class method for a function                                           |
| delattr()     | Deletes an attribute from an object                                             |
| getattr()     | Returns the value of a named attribute of an object                             |
| hasattr()     | Returns True if an object has a given attribute                                 |
| isinstance()  | Determines whether an object is an instance of a given class                    |
| issubclass()  | Determines whether a class is a subclass of a given class                       |
| property()    | Returns a property value of a class                                             |
| setattr()     | Sets the value of a named attribute of an object                                |
| super()       | Returns a proxy object that delegates method calls to a parent or sibling class |

### Input/Output
| Function | Description                                    |
|----------|------------------------------------------------|
| format() | Converts a value to a formatted representation |
| input()  | Reads input from the console                   |
| open()   | Opens a file and returns a file object         |
| print()  | Prints to a text stream or the console         |

### Variables, References, and Scope
| Function  | Description                                                                   |
|-----------|-------------------------------------------------------------------------------|
| dir()     | Returns a list of names in current local scope or a list of object attributes |
| globals() | Returns a dictionary representing the current global symbol table             |
| id()      | Returns the identity of an object                                             |
| locals()  | Updates and returns a dictionary representing current local symbol table      |
| vars()    | Returns __dict__ attribute for a module, class, or object                     |

### Miscellaneous
| Function       | Description                                 |
|----------------|---------------------------------------------|
| callable()     | Returns True if object appears callable     |
| compile()      | Compiles source into a code or AST object   |
| eval()         | Evaluates a Python expression               |
| exec()         | Implements dynamic execution of Python code |
| hash()         | Returns the hash value of an object         |
| help()         | Invokes the built-in help system            |
| memoryview()   | Returns a memory view object                |
| staticmethod() | Returns a static method for a function      |
| __import__()   | Invoked by the import statement             |

## Methods
* `static`  
In Django's official documentation, it recommends that you keep all static files, such as images, videos, javascript files, CSS files, etc. in the static directory of the app you are using.  
* `context`  
Variable, which is a Python dictionary, containing the data to insert into the placeholders.

## Objects
You can search for records that match certain criteria using the model's objects attribute (provided by the base class).
```python
all_listings = Listing.objects.all()
```

## Filter
Django's `filter()` method allows us to filter the returned `QuerySet` to match a specified text or numeric field against particular criteria.
```python
condo_listings = Listing.objects.filter(property_type__contains='Apartment/Condo')
```

## Tuples
A tuple is an immutable sequence of Python objects. The differences between tuples and lists are, the tuples cannot be changed unlike lists and tuples use parentheses, whereas lists use square brackets.
```python
LISTING_STATUS = (
    ('a', 'Active'),
    ('s', 'Sold'),
    ('t', 'Terminated'),
    ('e', 'Expired'),
)
```
