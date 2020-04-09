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
  
## Templates  
Django will automatically look for `.html` templates in a directory named `/templates/` in your application.  

## Methods
* `static`  
In Django's official documentation, it recommends that you keep all static files, such as images, videos, javascript files, CSS files, etc. in the static directory of the app you are using.  
`context`  
* variable, which is a Python dictionary, containing the data to insert into the placeholders.

## Objects
You can search for records that match certain criteria using the model's objects attribute (provided by the base class).
```python
all_listings = Listing.objects.all()
```

## Filter
Django's `filter()` method allows us to filter the returned `QuerySet` to match a specified text or numeric field against particular criteria.
```python
condo_listings = Listing.objects.filter(property_type__contains='Apartment/Condo)
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
