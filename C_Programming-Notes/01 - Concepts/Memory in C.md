
For a program to execute, it must use some of the computer’s resources such as CPU, RAM, IO, or other hardware. Deciding how and at what capacity to use these resources is the job of the underlying operating system. One of the most important of these resources is memory, more specifically: the temporary memory used for program execution which is called random access memory (RAM). When a program executes, the operating system reserves a section of the computer’s physical RAM to be used exclusively by the program. The fundamental unit of this memory is a byte. As you learned previously, all [variables](https://www.codecademy.com/resources/docs/c/variables) are simply a collection of some number of bytes: an `int` is four bytes, a `double` is eight bytes, and so on. The allocated section of RAM is simply a block of however many bytes the program needs (if available, of course).

As you can see, in this block of memory to the right, every byte has an associated address numbered using the [hexadecimal numbering system](https://en.wikipedia.org/wiki/Hexadecimal). For example, a byte of memory could be located at address 0x200 and the immediate byte next to it is located at address 0x201.

Every programming language has a different policy regarding the direct access and manipulation of a byte in memory; some allow it, some do not. C is one of the languages that allow such operations through the use of a _pointer_, and we will see how in this lesson.

***

In C, a byte of memory can be accessed using a _pointer_. A pointer containing the address of a variable is said to “point” to that variable.

Recall that when you declare a variable, a contiguous block of bytes is reserved in memory. A pointer to a variable is the address of the first of these bytes. A pointer can be created for every type of variable: be it primitive (for example `int`, `char`, or `double`), a custom data type created using a `struct` (we’ll cover those in a later lesson), or even another pointer. The syntax of a pointer is the following:

> `dataType* nameOfPointer;` or `dataType *nameOfPointer;` 

Since [pointers](https://www.codecademy.com/resources/docs/c/pointers) are used to store the memory address of a variable, we need to obtain this address first. This is done by using the _reference operator_ (&). The syntax for this is `&variableName:`

The address a pointer contains is not constant. A pointer may be reassigned to a new address so long as type consistency is maintained (e.g., `int` pointer points to a variable of type `int`).

***

If we have a pointer that is assigned the memory address of a variable, eventually we will need to access the data that it contains so we can use or manipulate it. The data contained in the memory address pointed to by a pointer can be accessed using the dereference operator (*). The syntax is as follows: `*pointerName;`

> Once a pointer is dereferenced, we can use its contents as we would a regular variable. It is important not to confuse this operator with the multiplication operator as they are represented by the same symbol!

Since `ptr` stores the address of variable `x`, the value obtained by dereferencing `ptr` is the value of `x`. If the value of a dereferenced pointer is changed, the value of the corresponding variable will change in the same way

***

Remember that a pointer is a special type of integer variable. This implies that basic arithmetic operations can be done on [pointers](https://www.codecademy.com/resources/docs/c/pointers). In this exercise, we will explore this idea.

The only arithmetic operations allowed for pointers are addition and subtraction. Conceptually, adding to (or subtracting from) a pointer means the pointer will point to some new address. Multiplication is not allowed because the address of a byte of memory is usually a large number; therefore, multiplying an address may yield an even larger number, possibly representing an address outside the bounds of the available memory space. Division is not allowed as it potentially allows a pointer to illogically point to an address with a non-integer index.

The addition operation for a pointer is only valid when adding an integer to a pointer; you cannot add two or more pointers together! The syntax is traditional addition illustrated by the following example (here, `n` represents an integer):

The important thing to note here is that adding `n` to a pointer _does not_ increment the address to point to a value `n` bytes away. It moves the pointer by `n` * (size of the data type in bytes). For example, if a pointer to an `int`, the size of which is four bytes, initially contains address 100 (we will use a decimal address for simplicity), and three is added to the pointer, the pointer will now point to address 112.

*** 

### Pointers and Arrays

In the lesson on [arrays](https://www.codecademy.com/resources/docs/c/arrays), you learned that an array is a contiguous block of memory reserved for many [variables](https://www.codecademy.com/resources/docs/c/variables) of the same type. Because of this structured organization, a pointer is well suited to work with this data type. If we have an integer array, we can use [pointers](https://www.codecademy.com/resources/docs/c/pointers) and pointer arithmetic to iterate through the array to access or manipulate its values. This might seem like an overcomplicated way to work with arrays, but there are some advanced applications in which working with an array through a pointer is necessary.

Consider an array of integers `arr`. Since arrays are contiguous blocks of memory, if we have a pointer to the first element, we can use pointer arithmetic to access the rest of the array.

> Keep in mind that while this is a valid way to work with arrays, it is unsafe. Accessing memory outside of the bounds of the array will not cause a program crash, but will silently corrupt data stored in those addresses. In the case of a read operation, it will return a random value. With caution in mind, let’s see how we can carefully access and manipulate elements in an array using pointers.