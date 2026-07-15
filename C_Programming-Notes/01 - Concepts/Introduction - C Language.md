
C is an older language compared to other languages in use and yet it is still very popular. The [TIOBE Index](https://www.tiobe.com/tiobe-index/), which measures the popularity of programming languages, has C at the top of the list for many years. This is due to C’s use in all areas of computing.

Most operating systems today including the Linux Kernel are implemented with C code. The main version of the Python programming language is named CPython because it is implemented using C. C has also been extended using the languages C++ and C#.

C is also common in embedded systems which are smaller computing units that control things like home appliances, lighting controllers, and other small physical devices.

---

```C
#include <stdio.h>

int main() {

  // output a line

  printf("Hello World!\n");

}
```

# Basic concepts

> [!NOTE] **`#include < >`** :
> Include standard library functions header file (directives) 
> 
> The pre-existing header files come bundled with the compiler and reside in the standard system file directory. This file contains C standard library function declarations and macro definitions to be shared between several source files. Functions like the printf(), scanf(), cout, cin, and various other input-output or other standard functions are contained within different Pre-Existing header files.
> 
> 	`#include` library can be include through <> or "" 
> 	
> 	![[Pasted image 20260716005354.png]]
> https://www.geeksforgeeks.org/c/c-c-include-directive-with-examples/

> [!NOTE] **`int main(){ }`** :
> Code starting point, where code within `{ }` have priority run. 

> [!NOTE] **`\\`** : Comment
> **Single line comment**, everything after the slashes on that line is considered a comment
> **Multi-line comments:** begin with **`**/***`** and end with **`***/**`**
 
> [!NOTE] `printf("Hello World!");`:
> This line of code prints, or outputs, the text “Hello World!” to the console. Printing text to the console is one way for a program to communicate with the user.

* * * *

# Syntax Rules

- Case sensitive
- All statements end with must end with `;` 
- Strings are referred through `""` (double quotes)

## Functions

## Compiling

