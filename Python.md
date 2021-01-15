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
    - Integer Operations
        | Operator | Description                   | Example  | Result |
        | -------- | ----------------------------- | -------- | ------ |
        | +        | Addition                      | 5 + 8    | 13     |
        | -        | Subtraction                   | 90 - 10  | 80     |
        | *        | Multiplication                | 4 * 7    | 28     |
        | /        | Floating-point division       | 7 / 2    | 3.5    |
        | //       | Integer (truncating) division | 7 // 2   | 3      |
        | %        | Modulus (remainder)           | 7 % 3    | 1      |
        | **       | Exponentiation                | 3 ** 4   | 81     |
    - Integers and Variables
        - +-. -=, *=, /= (floating-point division), //= (integer division)
        - % has multiple meanings
        - `>>> 9 % 5` (remainder of integer division)
        - result is 4
        - `>>> divmod(9,5)` gives truncated quotient and remainder at once
        - result is (1,4)
        - `>>> 2**3` exponentiation, allows you to mix integers and floats
        - result is 8
        - `>>> 2.0 ** 3`
        - result if 8.0
    - Precedence
        - standard rules, look up in table
    - Bases
        - 0b or 0B for binary
        - 0o or 0O for octal
        - 0x or 0X for hex
        - `>>> 0x10` (prints the base 10 value)
        - result is 16
        - ```Python
            >>> value = 65
            >>> bin(value)
            '0b1000001'
            ```
        - also `oct(value)` and `hex(value)`
        - The `chr()` function converts an integer to its single-character string
        - The `ord()` functioon goes from single-character string to integer
    - Type Converstions
        - `int()` converts argument to int
        - can work on text string that only contains digits
        - can convert to binary, octal, and hex with 2nd argument
        - doesn't work on strings containing decimals
        - if you mix numerical types, Python will sometimes try to automatically convert
            them for you
        - boolean value False is treated as 0 or 0.0 when mixed with integers or floats,
            and True is treated as 1 or 1.0
        - `bool()` converts arguments to bool
    - Int size
        - Python 2 - 64 bytes
        - Python 3 - any size
    - Floats
        - `5. , 5.0 , 05.0` all represent 5.0
        - Floats can include a decimal integer exponent after the letter e
        ```Python
        >>> 540
        5.0
        >>> 5e1
        50.0
        >>> 5.0e1
        50.0
        >>> 5.0 * (10 ** 1)
        50.0
        ```
        - When you mix integers and float, Python automatically promotes the integer
            values to float values
        - Python also promotes booleans to integers or floats
        - Can convert to float with `float()`

    ## Structure - comments
    - Comment with `#`
    - Continue lines with `\`
        Useful with Python interpreter.
        If inside parentheses (or brackets), don't need to use continue lines.
    
    ## Structure - if statements
    ```Python
    disaster = True
    if disaser:
        print("Yes")
    else:
        print("No")
    ```
    - You don't need parentheses around the if test
    - You do need the colon
    - Four spaces are used to indent
        - You can use tabs, but you need to be consistent with code within a section
        - the lines need to be indented the same amount, lined up on the left
        - the recommened style, PEP-8, uses four spaces
        - Don't use tabs, or mix tabs and spaces; it messes up the indent count
    - 'else if' is `elif`
    - Comparison operators
    | Comparison            | Operator | 
    | ----------------------| -------- | 
    | equality              |    ==    |
    | inequality            |    !=    | 
    | less than             |    <     | 
    | less than or equal    |    <=    |    
    | greater than          |    >     | 
    | greater than or equal |    >=    |
    - Boolean operators
        - `and`, `or`, `not`
    - Python lets you do this:
        `5 < x < 10`
    ## What is True?
    - These are all considered False:
        | boolean      | `False` |
        | null         | `None`  |
        | zero integer | `0`     |
        | zero float   | `0.0`   |
        | empty string | `''`    |
        | empty list   | `[]`    |
        | empty tuple  | `()`    |
        | empty dict   | `{}`    |
        | empty set    | `set()` |
    - Anything else is considered True
    ## Membership Operator
    - Whenever you need to make a lot of comparisons separated by `or`, use Python's
        membership operator `in`.
    - Example:
        ```Python
        >>> vowels = 'aeiou'
        >>> letter = 'o'
        >>> letter in vowels
        True
        >>> if letter in vowels:
        ...     print(letter, 'is a vowel')
        ...
        o is a vowel
        ```
    - More examples of membership operator:
        ```Python
        >>> letter = 'o'
        >>> vowel_set = {'a', 'e', 'i', 'o', 'u'}
        >>> letter in vowel_set
        True
        >>> vowel_list = {'a', 'e', 'i', 'o', 'u'}
        >>> letter in vowel_list
        True
        >>> vowel_tuple = {'a', 'e', 'i', 'o', 'u'}
        >>> letter in vowel_tuple
        True
        >>> vowel_dict = {'a': 'apple', 'e': 'elephant',
        ...                 'i': 'impala', 'o': 'ocelot', 'u': 'unicorn'}
        >>> letter in vowel_dict
        True
        >>> vowel_string = 'aeiou'
        >>> letter in vowel_string
        True
        ```
        - For the dictionary, the membership operator looks at the keys, not the values
    ## Walrus operator
    - New in Python 3.8
    - `name := expression`
    - Normally, assignment and test take two steps
        ```Python
        >>> tweet_limit = 280
        >>> tweet_string = "Blah" * 50
        >>> diff = tweet_limit - len(tweet_string)
        >>> if diff >= 0:
        ...     print("Tweet")
        ...else:
        ...     print("Over by " abs(diff))
        ...
        Tweet
        ```
    - With the walrus operator, this can be combined into one step:
        ```Python
        >>> tweet_limit = 200
        >>> tweet_string = "Blah" * 50
        >>> if diff := tweet_limit - len(tweet_string) >= 0:
        ...     print("Tweet")
        ...else:
        ...     print("Over by " abs(diff))
        ...
        Tweet
        ```
    ## Strings
    - In Python, strings are immutable
        - You can't change a string in place, but you can copy parts of strings to
            another string to get the same effect
    - Strings can be made with double or single quotes
    - Python has a few special types of strings:
        - f or F starts an f string used for formating
        - r or R starts a raw string, used to prevent escape sequences in the string
        - fr or FR or Fr or fR starts a raw f-string
        - u starts a Unicode string which is the same as a plain string
        - b starts a value of type bytes
    - Two kinds of quote characters
        - You can have single quotes inside double-quoted strings, or double quotes
            inside single-quoted strings
        - You can also use three single quotes or three double quotes
        - Triple quotes aren't very useful for short strings
            - Their most common use is to create multiline string
    - `print()` strips quotes from strings and prints their contents. It's mean for
        human output
    - You can create the empty string with any of the quote types.
    - Create with `str()`
        - You can make a string from another data type by using `str()`
    - Escape with \ (backslash)
        - Escape characters
            - `\n`
            - `\t`
            - `\'`
            - `\"`
            - `\\`
        - Raw strings negate these escapes:
    - Combine by Using +
        - `>>> 'Release' + 'the Kraken'`
    - One after the other
        - `>>> "The combined" "sentence"`
    - Duplicates with *
        - You can use the * operator to duplicate a string
        - * has higher precendence than +, so the string is duplicated before
            the line feed is tracked on
            - `start = 'Na ' * 4 + '\n'`
    - Get a Character with []
        - To get a single character from a string, specify its offeset inside square
            brackets after the string's name
        - The first (leftmost) offset is 0, the next is 1, and so on
        - The last (rightmost) offset can be specified with -1, so you don't have
            to count, going to the left are -2, -3, and so on
        - indexing works the same with the other sequence types (lists and tuples)
        - Because strings are immutable, you can't insert a character directly into one
            or change the character at a specific index
        - Instead you need to use some combination of string functions such as replace()
            or a slice
            - replace doesn't change the value, just prints the new result
    - Getting a Substring with a Slice
        - You can extract a substring from a string by using a slice
        - You define a slice using square brackets, a start offset, and an optional
            step count between them
        - You can omit some of these arguments
        - The slice will include characters **from offset start to one before end**
            - [:] extracts the entire sequence from start to end
            - [ start : ] specified from the start offset to the end
            - [ : end ] specifies from the beginning to the end offset minus 1
            - [ start : end ] indicates from the start offset to the end offset minus 1
            - [ start : end : step ] extracts from the start offset to the end offset
                minus 1, skipping characters by step
        - As before, offsets go 0, 1, and so one from the start to the right,
            and -1, -2, and so forth from the end to the left. If you don't specify
            start, the slice uses 0 (the beginning). If you don't specify end, it uses
            the end of the string
        - If you want a step size other than 1, specify it after a second colon
        - Given a negative step size, the Python slicer can also step backward.
        - A slice offset earlier than the beginning of a string is treated as 0,
            and one after the end is treated as -1.
    - Get Length with len()
        the len() functions counts characters in a string
    - Split with split()
        - specific to string
        - string.functions(arguments)
        - You can use the built-in string split() functions to break a string
            into a list of smaller strings based on some separator
        - A list is a sequence of values, separaters by commas and surrounded
            by square brackets:
            ```Python
            >>> tasks = 'get gloves,get mask,give cat vitamines, call ambulance`
            >>> tasks.split(',')
            ['get gloves', 'get mask', 'give cat vitamines', 'call ambulance']
            ```
        - If you don't specify a separator, split() uses any sequqnce of white space
            characters - newlines, spaces, and tabs
    - Combine by Using join()
        - the join() function is the opposite of split()
            - it collapses a list of strings into a single string
            - `\n`.join(lines) joins the list lines with separating newlines
            - Example:
            ```Python
            >>> crypto_list = ['Yeti', 'Bigfoot', 'Loch Ness Monster']
            >>> cypto_string = ','.join(cypto_list)
            >>> print('Found and signing book deals:', cypto_string)
            "Found and singning book deals: Yeti, Bigfoor, Lock Ness Monster"
            ```
    - Substitue by Using replace()
        - Use replace() for simple substring substitution
        - Give it the old substring, the new one, and how many instance of the old
            substring to replace
        - It returns the changed string but does not modify the original string
        - If you omit this final count argument, it replaces all instances
        - When you know the exat substring(s) you want to change, use replace()
        - Sometimes you want to ensure that the substring is a whole world,
            or the beginning of a word, and so on. In those case, you need
            regular expressions.
    - Strip with strip()
        - The strip() functions assume you want to get rid of whitespace characters
            (' ','\t','\n') if you don't give them an argument
        - strip() strips both ends
        - lstrip() only from left
        - rstrip() only from right
        - if no whitespace characters, nothing happens
        - besides no argument (meaning whitespace characters) or a single character,
            you can also tell strip() to remove any character in a multicharacter
            string
        