# Primitive Built-in Types
## Arithmetic Types
* Basic character type is **char**. A char is the same size as a single machine byte.
* The **wchar_t** type is guaranteed to be large enough to
hold any character in the machine’s largest extended character set.
* **int** - at least as large as a **short**, **long** - at least as large as a **int** and so on..
* The floating-point types represent single-, double-, and extended-precision values.
* The **float** and **double** types typically yield about 7
and 16 significant digits, respectively
* Signed and unsigned types
    * int, short, long, long long are all signed
    * Adding _unsigned_ in front of the above data types indicates that the data stored in the variable will be unsigned
    * Three distinct character base types - *char*, *signed char* and *unsigned char*. char is assigned either of the other two representations depending upon the compilerng
    * For signed values, range should be equally divided between positive and negative values. For example, if a character is of 1 byte ( 8 bits), number of possible values = 256. But, a signed char can hold values from -127 to +127. ( Most machines allow values from -128 to 127 ).  
* Key advice on choosing types
    * Use an unsigned type when you know that the values cannot be negative.
    * Use *char* or *bool* types only to hold characters and truth values respectively. Since the behaviour of *char* ( signed or unsigned ) is dependent on the compiler, if you ever want to hold a small integer, then use char and specify whether it is *signed* or *unsgined*.
    * Use double for floating-point computations; float usually does not have enough precision, and the cost of double-precision calculations versus single-precision is negligible.

## Exercises
 
### Exercise 2.1: What are the differences between int, long, long long, and short? Between an unsigned and a signed type? Between a float and a double?
* The primary difference between int, long, and long long is the **size of the data** that each of these data types can hold. A _long_ is at least as large as an _int_, which means it might hold larger values than _int_. There is a similar relationship between _long_ and _long long_. 
* An unsigned type holds values ranging from 0 to its size. A signed type holds both positive and negative values, and thus the range is equally divided between signed and unsigned values.
* Both *float* and *double* are used for storing **floating point** values. Float yields upto 7 significant digits, whereas double yields upto 16. That is, double is more precise.

### Exercise 2.2: To calculate a mortgage payment, what types would you use for the rate, principal, and payment? Explain why you selected each type.
* Both principal and rate can be floating point numbers, and hence I would use **double** for them. 
* I am assuming payment here means the time, and if it always supposed to be represented in years, then it would be an **int**, else a **float**.
