# ABI Knowledge

## What is ABI

What is **ABI**
- Application
- Binary
- Interface

Some things that are included in the discussion of ABI:

- Size, number and order of data members in a type
- Size, number and order of virtual functions
- Number and order of function parameters
- Function return types

## Changing the return type

- Return type is not part of function signature.

- Return type is not part of the name mangling[<sup>1</sup>](#refer-anchor-1), so if the header doesn't match the binary, things can go very wrong
    ![Alt text](image.png)

    ![Alt text](image-2.png)

## Changing the order of virtual functions


- If you change the order of virtual functions in the header file, the compiler will call the wrong one.

    ![Alt text](image-3.png)

    ![Alt text](image-4.png)

## Changing the Order of Member Variables
- Just like the virtual function order, the compiler would generate the wrong offset.
    ![Alt text](image-5.png)

    ![Alt text](image-6.png)
- Program needs to be recompiled, by adding the object at the end of your struct, 
it becomes undefined behavior to compiler.
    ![Alt text](image-7.png)

## references
<div id="refer-anchor-1"></div>

- [1] [Name Mangling Wikipedia](https://en.wikipedia.org/wiki/Name_mangling#)
