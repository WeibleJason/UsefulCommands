# Python Guide

## Data Types
1. Python Data Are Objects
    - In Python, an object is a chunk of data that contains at leasat the following:
        - a type that defines what it can do
        - a unique id to distinguish it from other object
        - a value consistent with its type
        - a reference count that tracks how often this object is used
    - Types
        | Name            | Type      | Mutable? | Example               |
        | --------------- | --------- | -------- | --------------------- |
        | Boolean         | bool      | no       | `True`,`False`        |
        | Integer         | int       | no       | `23`,`25000`,`25_000` |
        | Floating point  | float     | no       | `3.14`,`2.7e5` |
        | Complex         | complex   | no       | `3j`,`5 + 9j` |
        | Text string     | str       | no       | `'alas'`,`"alack"`,`'''a verse attack'''` |
        | List            | list      | yes      | `True`,`False` |
        | Tuple           | tuple     | no       | `True`,`False` |
        | Bytes           | bytes     | no       | `True`,`False` |
        | ByteArray       | bytearray | yes      | `True`,`False` | 
        | Set             | set       | yes      | `True`,`False` |
        | Frozen set      | frozenset | no       | `True`,`False` |
        | Dictionary      | dict      | yes      | `True`,`False` |