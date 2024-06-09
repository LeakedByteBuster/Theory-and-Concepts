# Notes
## Index
- [Undefined Behavior](#undefined-behavior)
- [printf function](#printf-function)
- [Variadic Functions](#variadic-functions)

## Undefined Behavior

```md
* WHAT IS UNDEFINED BEHAVIOR ?
- The C FAQ defines "undefined behavior" like this:

    Anything at all can happen; the Standard imposes no requirements. The program may fail to compile, or 
    it may execute incorrectly (either crashing or silently generating incorrect results), or it may 
    fortuitously (By chance) do exactly what the programmer intended.

* TYPED AND UNTYPED LANGUAGUES
            ________________________
            |   Typed  |  Untyped  |
    -------------------------------
    |Safe   | ML, JAVA |  LISP     | It is a family of old languages (grammarly engine is written in Common Lisp)
    -------------------------------
    |Unsafe | C, C++   |  Assembler|
    -------------------------------

** Advantages of Safe languages :
    - Increase the security aspect of a program
    - Safe Languages check bounds of arrays..., so it doesn't run erroneous code it stops at compile time
    - Reduce debugging time
    - Development and maintainance

** Disadvantages of Safe languages :
    - Increase the run time of the program because of all the checks

** Advantages of Unsafe languages :
    - Performance
    - Run time
    - Running erroneous operation (accessing a null pointer, dividing by zero) which may lead to a meaniningless program 

** Disadvantages of Safe languages :
    - Lack of security (Overflows, Underflows...)
    - errors are not trapped. errors can run silenty (Observable later on)
```

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
```md
######################### VARIADIC FUNCTIONS #########################

What? Why? When? How?

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

    What to call this list? - Va_list   :    Takes the name of the list (gives a name to a list)
        (Naming the list)                     some call it (list, args...)
                                            {i.e. va_list my_list;}
        
    Begin of the list is?   - Va_start      : gives the start from where to read (from where start this list?)
        (Initializing the list)             {i.e. va_start (name of the list, the parameter that precedes the list)}
                                            {i.e. va_start (my_list, y)}
                                            va_start() must be matched by a call to va_end(), from within the same function

    Acccess individualy         - Va_arg    : Access members of the list
    to each parameter                        {Pro : va_arg(List_name, Data_type)} 
                                            {i.e. 1st call : va_arg (my_list, int) | 2nd call : Next one....}
                                            (if int => int, if char=>int)
                                            (if float => double)

    Ending a list               - Va_end    : Signify end of the list
                                            (Pro : va_end(list_name))
                                            (i.e.: va_end(my_list))
```
