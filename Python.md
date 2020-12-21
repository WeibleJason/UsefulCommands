# Python Guide

## Data Types
1. Python Data Are Objects
    - In Python, an object is a chunk of data that contains at leasat the following:
        - a type that defines what it can do
        - a unique id to distinguish it from other object
        - a value consistent with its type
        - a reference count that tracks how often this object is used
    - Types
        | Name            | Type      | Mutable? | Example                            |
        | --------------- | --------- | -------- | ---------------------------------- |
        | Boolean         | bool      | no       | `True`,`False`                     |
        | Integer         | int       | no       | `23`,`25000`,`25_000`              |
        | Floating point  | float     | no       | `3.14`,`2.7e5`                     |
        | Complex         | complex   | no       | `3j`,`5 + 9j`                      |
        | Text string     | str       | no       | `'alas'`,`"alack"`,`'''a verse'''` |
        | List            | list      | yes      | `['Alice','Bob','Fred']`           |
        | Tuple           | tuple     | no       | `(2, 4, 6)`                        |
        | Bytes           | bytes     | no       | `b'ab\xff`                         |
        | ByteArray       | bytearray | yes      | `bytearray(...)`                   | 
        | Set             | set       | yes      | `set([3, 6, 9])`                   |
        | Frozen set      | frozenset | no       | `frozenset(['Elsa','Otto'])`       |
        | Dictionary      | dict      | yes      | `{'game': 'bingo', 'cat': 'Oreo'}` |
    

    - Python is strong typed, which means that the type of an object does not change,
        even if its value is mutable
    - Variables must begin with letter or underscore
        - names that begin with an underscore are treated specially
        - in a python consle, you can list reserved words with `help("keywords")`
    - Variables are names, not places
        - variables are just names
        - assignment does not copy a value
            - it just attaches a name to the object that contains the data
            - the name is a reference to a thing rather than the thing itself
        - a name can refer to anything and we get teh value and type by "following the
            string" to the data object itself
    - If you want to know the type of anything (a variable or a literal value),
        you can use `type()` 
        Ex:
        ```python 
        >>> type(7)
        <class 'int'>
        >>> type(7) == int
        True
        >>> isinstance(7, int)
        True
        ```
    - A class is the definition of an object
        - in Python, "class" and "type" mean pretty much the same thing
        - When you use a variable in Python, it looks up the object that it refers to.
            Behind the scenes, Python is busy, often creating temporary objects that will
            be discarded a line or two later. 
    - Python suppports multiple assignment
        Ex: `>>> two = deux = zewi = 2`
    - Reassigning a Name
        - Because names point to objects, changing the value assigned to a name just
            makes the name point to a new object. The reference count of the old object
            is decremented, and the new one is incremented
- Copying
    - Assigning an existing variable A to a new variable name B just makes B point to
        the same object that A does. If you pick up either the A opr B tag and follow
        their strings, you get to the same object
    - If the object is immutable (like an integer), its value can't be changed, so
        both names are essentially read-only
    - Example:
        ```python
        >>> x = 5
        >>> x
        5
        >>> y = x
        >>> y
        5
        >>> x = 29
        >>> x
        29
        >>> y
        5
        ```
    - When we assigned x to y, that made the name y point to the integer object with
        value 5 that x was also pointing to. Changing x made it point to a new
        integer object with value 29. It did not change the one containing 5, which y
        still points to.
    - But if both names point to a mutable object, you can change the object's value
        via either name, and you'll see the changed value when you either name.
    - A list is a mutable array of values.
        ```python
        >>> a = [2, 4, 6]
        >>> b = a
        >>> a
        [2, 4, 6]
        >>> b
        [2, 4, 6]
        ```
    - These list members (a[0], a[1], and a[2]) are themselves like names, pointing
        to integer objects with the values 2, 4, and 6. The list object keeps its
        members in order.
    - Now change the first list element, through the name a, and see that b also
        changed:
        ```python
        >>> a[0] = 99
        >>> a
        [99, 4, 6]
        >>> b
        [99, 4, 6]
        ```
    - When the first list element is changed, it no longer point to the object
    with value 2, but a new object with value 99. The list is still of type list, but
    its value (the list elements and their order) is mutable.

## Numbers and Booleans
- Zero values are considered False
    ```Python
    >>> bool(False)
    False
    >>> bool(0)
    False
    >>> bool(0.0)
    False
    ```
- Integers
    - Any sequence of digits in Python represents a *literal integer*
    - Cannot have leading zeros
    - Can start integers with 0b, 0o, or 0x
    - Underscore as a digit separator
    ```Python
    1_000_000
    ```
    - You can put the underscore anywhere after the first digit. They are ignored. 
