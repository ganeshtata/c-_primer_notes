# Exercises Section 2.1.3
## Exercise 2.5: Determine the type of each of the following literals. Explain the differences among the literals in each of the four examples:
(a) 'a', L'a', "a", L"a" 

Ans. 'a' - Character type


## Exercise 2.11: Explain whether each of the following is a declaration or a definition:
(a) extern int ix = 1024;
Ans. Definition
(b) int iy;
Ans. Definition
(c) extern int iz;
Ans. Declaration

### Important notes - 
* Declaration - Specifies type and name of a variable
* Definition - Allocates storage, may provide the variable with an initial value

* Scope Resolution operator  - The global scope has no
name. Hence, when the scope operator has an empty left-hand side, it is a request to
fetch the name on the right-hand side from the global scope.

# Exercises Section 2.2.4
## Exercise 2.13: What is the value of j in the following program?
int i = 42;
int main()
{
    int i = 100;
    int j = i;
}

Ans. Value of j is 100 since `i=100` hides global `i`.

## Exercise 2.14: Is the following program legal? If so, what values areC++ Primer, Fifth Edition
printed?
 
Click here to view code image
 
int i = 100, sum = 0;
for (int i = 0; i != 10; ++i)
     sum += i;
std::cout << i << " " << sum << std::endl;

Ans. 
(i) It is a legal program since both `i`s are defined in different scopes
(ii)Output - 100 45. The `i` is taken from the outer scope.

### Important notes - 
* Reference - Once initialized, a reference remains
bound to its initial object. There is no way to rebind a reference to refer to a different
object. Because there is no way to rebind a reference, references must be initialized.

* Because references are not objects, we may not define a reference to a reference.

* A reference may be bound to an object - Not to a literal or the result of a general expression.

#Exercises Section 2.3.1
## Exercise 2.15: Which of the following definitions, if any, are invalid? Why?
(a) int ival = 1.01;
Ans. Valid
(b) int &rval1 = 1.01;
Ans. Invalid - Can't initialize reference with constant ( Literal can't be used as initializer )
(c) int &rval2 = ival;
Ans. Valid
(d) int &rval3;
Ans. Invalid. Needs a variable as an initializer

## Exercise 2.16: Which, if any, of the following assignments are invalid? If they are valid, explain what they do.
 
Click here to view code image
 
int i = 0, &r1 = i; double d = 0, &r2 = d;
 
(a) r2 = 3.14159; # Valid, d changes to 3.14
 
(b) r2 = r1; # Valid, d changes to 0.0
 
(c) i = r2; # d changes to 0
(d) r1 = d; # r1, i are 0

## Exercise 2.17: What does the following code print?
 
Click here to view code image
 
int i, &ri = i;
i = 5; ri = 10;
std::cout << i << " " << ri << std::endl;

Ans. 10 10


### Important notes

> It is an error to copy or otherwise try to access the value of an invalid pointer. As
when we use an uninitialized variable, this error is one that the compiler is unlikely to
detect. The result of accessing an invalid pointer is undefined. Therefore, we must
always know whether a given pointer is valid.

 
* Dereferencing a pointer yields the object to which the pointer points. We can assign to
that object by assigning to the result of the dereference.

* If there is no object to bind to a pointer, then
initialize the pointer to nullptr or zero. That way, the program can detect
that the pointer does not point to an object.

* It can be hard to keep straight whether an assignment changes the pointer or the
object to which the pointer points. The important thing to keep in mind is that
assignment changes its left-hand operand.

* The type void* is a special pointer type that can hold the address of any object.

 
# Exercises Section 2.3.2
## Exercise 2.18: Write code to change the value of a pointer. Write code to change the value to which the pointer points
Ans.
```
int *p = 0; // Initialize as null pointer
int q = 1;
p = &q; // Changed value of p to point to q, no longer a null ptr
*p = 25 // CHanged the value to which the pointer points. Q is now 25
```
## Exercise 2.19: Explain the key differences between pointers and references.
Ans. 
A pointer is an object that holds the address of another object of the same type ( With the exception of void pointer)
A reference is an alias of an object, but it isn't an object in itself. 

## Exercise 2.20: What does the following program do?
int i = 42;
int *p1 = &i;
*p1 = *p1 * *p1;
.
Ans. i is 1764

## Exercise 2.21: Explain each of the following definitions. Indicate whether any are illegal and, if so, why.
int i = 0;

(a) double* dp = &i; # Invalid. Pointer to double cannot be initialized with integer address.
(b) int *ip = i; # Invalid. Pointer to integer cannot be initialized with integer. Need address
(c) int *p = &i; # Valid

## Exercise 2.22: Assuming p is a pointer to int, explain the following code:
if (p) // True, if p is not a null pointer
if (*p) // True, if the value pointed by p is non-zero

## Exercise 2.23: Given a pointer p, can you determine whether p points to a valid object? If so, how? If not, why not?
Ans. No. It may so happen that the object to which the pointer points to, no longer exists, and thus, even though the pointer points to a address in memory, the value in that location is undefined


## Exercise 2.24: Why is the initialization of p legal but that of lp illegal?
## int i = 42;    void *p = &i;     long *lp = &i;
Ans.  void pointer can hold the address of any object. lp is a pointer to a long object, and thus can only hold the address of a long.

## Exercise 2.25: Determine the types and values of each of the following variables.
```
int* ip, &r = ip;
     Type                               Value
ip  - Pointer to integer                Undefined
r   - Reference to pointer to integer   Undefined
```

```
int i, *ip = 0;
     Type            Value
i  - integer         undefined
ip - Null Pointer      0
```

```
int* ip, ip2;
       Type                     Value
ip  -  Pointer to integer       Undefined
ip2 -  integer                  Undefined
```


## Exercise 2.26: Which of the following are legal? For those that are illegal, explain why
```
const int buf; // Illegal - Bug has not been initialized
int cnt = 0; // Legal
const int sz = cnt; // Legal
++cnt; ++sz; // Illegal ( ++sz ) - Cannot change const value4
```

## Exercise 2.27: Which of the following initializations are legal? Explain why.
```
(a) int i = -1, &r = 0 ;
// Illegal. i is an integer being initialized with -1 ( Legal ). r is a integer reference, and thus needs to be initialized with an integer variable( Illegal )
(b) int *const p2 = &i2;
// If i2 is an integer, then this is legal, because p2 is a constant pointer to integer, and thus it is mandatory to initialize it with an address of an integer. But, if i2 is an integer th, then this initialization is invalid, since through p2, i2 value can be changed.
(c) const int i = -1, &r = 0;
// Legal. r is a const integer reference, and thus can be initialized with a literal / constant. 
(d) const int *const p3 = &i2;
// Legal if i2 is an integer. It is legal for both const and non-const cases, since p3 is a const pointer to a const integer, which means we cannot change p3's value, or the value it points to, THROUGH p3. Thus, it doesn't matter if i2 is const or not.
(e) const int *p1 = &i2;
// Legal. Same reason as previous case. 
(f) const int &const r2;
// Illegal. This is not a valid statement. The error message is self-explanatory - "error: ‘const’ qualifiers cannot be applied to ‘const int&’"
(g) const int i2 = i, &r = i;
// Legal. i2 is being initialized with i, and thus only the value of i is being copied to i2. r is a const integer reference, and thus, i's value CANNOT be changed THROUGH r.
```

## Exercise 2.28: Explain the following definitions. Identify any that are illegal.
```
(a) int i, *const cp;
// i is an integer. cp is a constant pointer to integer. cp's initialization is illegal since cp needs to be explicitly initialized during its definition.
(b) int *p1, *const p2;
// p1 is a pointer to integer. p2 is a constant pointer to integer. Refer to previous statement to understand why p2 is illegal.
(c) const int ic, &r = ic;
// ic is an integer constant. r is a const integer refernce initialized with ic. r ic's initialization is illegal since it is a const integer and thus needs to be initialized with an integer constant. 
(d) const int *const p3;
// p3 is a constant pointer to constant integer. Illegal initialization since p3 needs to initialized with the address of an integer object / variable.
(e) const int *p;
// p is a pointer to integer constant. Legal initialization.
```

## Exercise 2.29: Using the variables in the previous exercise, which of the following assignments are legal? Explain why.
```
(a) i = ic;
// Valid. Value of ic is being assigned to i. Modifying i does NOT modify ic.
(b) p1 = p3;
//  Invalid. p3 is a constant pointer to a constant integer. And p1 is a pointer to integer, and thus if this assignment were legal, address stored in p1 and p3 would be the same. But p3 must NOT allow the value to that it points to, to be modifed. Thus, this is illegal.
(c) p1 = &ic;
// Invalid. ic is an integer constant, and thus, its value cannot be changed. But, this assignment would allow p1 to modify the value pointed by it, i.e., ic's value. Thus, this illegal.
(d) p3 = &ic;
// Illegal. p3 is a constant pointer to constant integer. Since it is a constant pointer, its value cannot be changed. Error message is self-explanatory - " error: assignment of read-only variable ‘p3’"
(e) p2 = p1;
// Illegal. Same as previous reason.

(f) ic = *p3;
// Illegal. ic is a constant integer, and thus its value cannot be modified. 
```

## Exercise 2.30: For each of the following declarations indicate whether the object being declared has top-level or low-level const.
```
const int v2 = 0;  
// Low-level const

int v1 = v2;  
// No const - v1's value can be modified

int *p1 = &v1, &r1 = v1;
 // No const - p1 is a pointer to integer, and r1 is an integer reference. Both of them are not const.

const int *p2 = &v2, *const p3 = &i, &r2 = v2; 
// p2 is a pointer to integer constant - Hence it has top-level const. p3 is a constant pointer to constant integer. Hence it has both top-level and low-level const. // r2 is a constant integer reference, It has a  low-level const
 
```

## Exercise 2.31: Given the declarations in the previous exercise determine whether the following assignments are legal. Explain how the top-level or low-level const applies in each case.
```
r1 = v2; 
// r1 is a reference to integer. Thus, r1 has to be a const reference for this assignment to work since v2 has a low-level const ( Low-level const should match). Illegeal

p1 = p2; 
// Low-level const does not match. IF this assignment was legal, we would be able to modify value pointed by p2, using p1, since both p1 and p2 would then point to the same integer. But p2 should NOT allow this since it is a pointer to const integer. Illegal.

p2 = p1;
// p1 has no low-level const. Hence, this is legal. p2 and p1 point to the same integer now, but since p1 doesn't have any low level const, this is legal.

p1 = p3;
// Illegal. Same reason as p1 = p2

p2 = p3;
// Legal. Both have low level const. Because of this assignment, p2 and p3 would point to the same integer. But since both have low level const, p2 CANNOT change the value that it points to ( Note - This means the value at the address stored in p2, p3 cannot be modified THROUGH p2, p3 )
```
