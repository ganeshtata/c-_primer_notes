# Type Conversions
We can convert object of given type to other similar types. Type conversions happen _automatically_ when we use one type of object instead of another similar type.

| Actual Object Type | Assigned Object Type | Result                                                |
|--------------------|----------------------|-------------------------------------------------------|
| bool               | int                  | `False` if integer is 0, `True` otherwise             |
| int                | bool                 | `1` if boolean is True, else `0`                      |
| int                | float                | Only integer part before the decimal point is stored  |
| float              | int                  | The integer is assigned,  with the fractional part as 0 |

* If we assign an out-of-range value to an object of unsigned type, the result is
the remainder of the value modulo the number of values the target type can
hold. For example, an 8-bit unsigned char can hold values from 0 through
255, inclusive. If we assign a value outside this range, the compiler assigns the
remainder of that value modulo 256. Therefore, assigning –1 to an 8-bit
unsigned char gives that object the value 255.
* If we assign an out-of-range value to an object of signed type, the result is
undefined. The program might appear to work, it might crash, or it might
produce garbage values.

**NOTE** - Avoid assuming that the size of a data type is fixed and known value, since it is always going to be dependent on the machine.

* When using both `unsigned` and `int` values in an arithemetic expression, the integer value will be converted
to unsigned. 

## Exercises
### Exercise 2.3: What output will the following code produce?
```
unsigned u = 10, u2 = 42;
std::cout << u2 - u << std::endl;
// 32

std::cout << u - u2 << std::endl;
// Some large number depending on the compiler

int i = 10, i2 = 42;
std::cout << i2 - i << std::endl;
// 32
std::cout << i - i2 << std::endl;
// -32
 
 
std::cout << i - u << std::endl;
// 0
std::cout << u - i << std::endl;
// 0
```
