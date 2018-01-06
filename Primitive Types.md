## JAVA PRIMITIVE DATA TYPES

In Java language, primitive data types are the basic data types. A
primitive type is predefined by the language and is named by
a reserved keyword. Based on the data type of a variable, the
operating system allocates memory and decides what can be stored
in reserved memory.


There are eight primitive data types supported by Java:
*  Arithmetic data types
  * Integer type
    * byte
    * short
    * int
    * long
  * Floating-point type
    * float
    * double
* char, character type whose values are 16-bit Unicode characters
* boolean whose values are either true or false
___
##### 1. byte
* Byte data type is an 8-bit signed two's complement integer
* Minimum value is -128 (-2^7) and Maximum value is -127 (2^7-1)
* Default value is 0
* Byte data type is used to save space in large arrays where memory is a constraint.
  mainly inplace of int. since a byte is four times smaller than int

##### 2. short
* Short data type is a 16-bit signed two's complement integer
* Minimum value is (-2^15) and Maximum value is (2^15-1)
* Default value is 0
* short can also be used to save memory in large arrays as it's two times
  smaller than int

##### 3. int
* Int data type is a 32-bit signed two's complement integer
* Minimum value is (-2^31) and Maximum value is (2^31 -1)
* Default value is 0
* Data type int can be used to represent an unsigned 32-bit integer,
  which has a minimum value of 0 and a maximum value of (2^32-1)
* Integer class can be used to use int data type as an unsigned integer
* Integer class have static methods like compareUnsigned,
  divideUnsigned etc to support the arithmetic operations for 
  unsigned integer

##### 4. long
* Long data type is a 64-bit signed two's complement integer
* Minimum value is (-2^63) and Maximum value is (2^63-1)
* long data type can be used to represent an unsigned 64-bit long,
  which has a minimum value of 0 and a maximum value of (2^64-1)
* Use long when you need a range of values wider than those provided by int
* Long class also have methods like compareUnsigned, divideUnsigned etc
  to support arithmetic operations for unsigned long

##### 5. float
* Float data type is a single-precision 32-bit IEEE 754 floating point
* Range is approximately ±3.40282347E+38F (6-7 significant decimal digits)
* Default value is 0.0f
* Float is used to save memory in large arrays of floating point numbers
* Float data type is never used for precise values such as currency

##### 6. double
* Double data type is a double-precision 64-bit IEEE 754 floating point
* Range is approximately ±1.79769313486231570E+308(15 significant decimal digits)
* Default value is 0.0d
* Data type double is generally used as the default data type for decimal values,
  generally the default choice.
* Double data type is also never used for precise values such as currency

##### 7. char
* Char data type is a single 16-bit Unicode character
* Minimum value is '\u0000' (or 0) and Maximum value is '\uffff'
  (or 65,535 inclusive)
* Data type char is used to store any character

##### 8. boolean
* Boolean data type represents one bit of information, only two
  possible values: true and false
* Boolean size is not precisely defined, it varies
  from one jvm to another
* Default value is false
* Data type boolean is used for simple flags that track true/false conditions

___

The following table summarizes the primitive data types.

| Data Type  | Description                  | Default Value | Size   | Example Literals       |
|------------|------------------------------|---------------|--------|------------------------|
| byte       | two's complement integer     | 0             | 8 bits | None                   |
| short      | two's complement integer     | 0             | 16 bits| None                   |
| int        | two's complement integer     | 0             | 32 bits| -2, -1, 0, 1, 2        |
| long       | two's complement integer     | 0L            | 64 bits| -2L, -1L, 0L, 1L, 2L   |
| float      | IEEE 754 floating point      | 0.0f          | 32 bits| 1.35e100f, -1.35e-100f, .4f, 14.3F|
| double     | IEEE 754 floating point      | 0.0d          | 64 bits| 1.23456e300d, -1.23456e-300d, 1e1d |
| char       | Unicode characters           | \u0000        | 16 bits| 'a', '!', '\u0041', '\101', '\\', '\'', '\n', 'ß' |
| boolean    | true or false                | false | Not precisely defined| true, false     |
