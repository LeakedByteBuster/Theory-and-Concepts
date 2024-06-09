# Notes
## Index
- [Undefined Behavior](#undefined-behavior)
- [printf function](#printf-function)
- [Variadic Functions](#variadic-functions)
- [Structures](#structures)

## Undefined Behavior

* **WHAT IS UNDEFINED BEHAVIOR?**
  - The C FAQ defines "undefined behavior" like this:
    - *Anything at all can happen; the Standard imposes no requirements. The program may fail to compile, or it may execute incorrectly (either crashing or silently generating incorrect results), or it may fortuitously (By chance) do exactly what the programmer intended.*

* **TYPED AND UNTYPED LANGUAGES**
  
  |           | Typed    | Untyped   |
  |-----------|----------|-----------|
  | Safe      | ML, JAVA | LISP      |
  | Unsafe    | C, C++   | Assembler |

  **Advantages of Safe languages:**
  - Increase the security aspect of a program
  - Safe Languages check bounds of arrays..., so it doesn't run erroneous code it stops at compile time
  - Reduce debugging time
  - Development and maintenance

  **Disadvantages of Safe languages:**
  - Increase the run time of the program because of all the checks

  **Advantages of Unsafe languages:**
  - Performance
  - Runtime
  - Running erroneous operation (accessing a null pointer, dividing by zero) which may lead to a meaningless program

  **Disadvantages of Unsafe languages:**
  - Lack of security (Overflows, Underflows...)
  - Errors are not trapped. Errors can run silently (Observable later on)


## printf function

```md
############################# CDECL calling convention #############################

CDECL :
    - Arguments :   * Passed through stack
                    * Pushed from right to left
                    * Caller removes parameters from stack

    - Return    :   * Integers, pointers : EAX
                    * Floating point     : STO
    
    - Registers :   * EAX, ECX, EDX saved by Caller
                    * all others saved by callee

    - Name mangling : C functions are prepended with a_
```

## Variadic Functions

**What? Why? When? How?**

- Variadic : maybe comes from (variable)(many)
- Variadic functions : functions that can have as many parameter as you want

- Variadic functions are macros (macro functions) pre-defined in <stdarg.h>

- A programmer may need a functions that take a volatile number of arguments (calculator)

- Representation (syntax) of variadic functions :
    function            : int(int x, int y)
    variadic function   : int(int x, int y, ...)
    "..." means more
    x and y are not part of list, they are declared explicitly BY YOUU!!

- To use variadic functions you need to know : 
    ### THERE SHOULD BE AT LEAST ONE ARGUMENT ###

| Action                  | Function      | Description                                              |
|-------------------------|---------------|----------------------------------------------------------|
| Naming the list         | Va_list       | Takes the name of the list (gives a name to a list)     |
|                         |               | - Some call it (list, args...)                           |
|                         |               | - Example: `va_list my_list;`                            |
| Initializing the list   | Va_start      | Gives the start from where to read (from where start this list?) |
|                         |               | - Example: `va_start (name of the list, the parameter that precedes the list)` |
|                         |               | - Example: `va_start (my_list, y)`                       |
|                         |               | - `va_start()` must be matched by a call to `va_end()`, from within the same function |
| Access individually     | Va_arg        | Access members of the list to each parameter            |
|                         |               | - Pros: `va_arg(List_name, Data_type)`                  |
|                         |               | - Example: 1st call: `va_arg(my_list, int)`             |
|                         |               |            2nd call: Next one...                         |
|                         |               | - If int => int, if char => int, if float => double     |
| Ending a list           | Va_end        | Signify end of the list                                  |
|                         |               | - Pros: `va_end(list_name)`                              |
|                         |               | - Example: `va_end(my_list)`                             |


## Structures


- **STRUCTURE also are called "records"**
- Structures help to organize complicated data
- they permit a group of related variables to be treated as a unit instead of as separate entities :
- 
### STRUCTURE DECLARATION :
```c
    struct point {
        int x;
        int y;
    }
```
- Struct : Introduces a structure declaration
- point : Optional name called "Structure Tag"
- int x, y : these var are called "members"

- A structure member or tag and an ordinary (i.e., non-member) variable, can have the same name without conflict
- A structure declaration that is not followed by a list of variables reserves no storage (Just the shape of struct)
- A structure can be initialized by following its definition with a list of initializers (constant expressiones to each member in the struct)
- **Automatic Structure** : Intialized by assignement or by calling a function that returns the right type

- **Calling** a member of a struct :
    structurename.member
    '.' connects structure name and the memeber name
  ```c
    printf("%d", point.x);
  ```
  
- Structure can be nested
```c
    struct rect {
       struct point pt1;
       struct point pt2;
   };
```
- If p is a pointer to a structure :
  ```c
    (*pp).member
  ```
    shorthand : p->member-of-structure

- Binary Tree :
    The tree contains one ``node'' per distinct word; each node contains
    • A pointer to the text of the word,
    • A count of the number of occurrences,
    • A pointer to the left child node,
    • A pointer to the right child node.
    No node may have more than two children; it might have only zero or one.
