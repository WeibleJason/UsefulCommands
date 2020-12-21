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