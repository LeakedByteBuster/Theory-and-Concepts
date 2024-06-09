```makefile
NAME = libft.a
#Compiler to be used
CC = cc
#CFLAGS contains the options for compilation
CFLAGS = -Wall -Werror -Wextra
#EXEC contains executable files to be generated
EXEC = a.out
#OBJECTS, objs, OBJS, obj, or OBJ contains all object files names
OBJECTS = program.o ft_strlen.o
RM = rm -rf

#all : contains all the executable files to produce (.DEFAULT_GOAL edit a.out)
all: $(EXEC)

#Creating the executable file "a.out"
# -c option tells the compiler to compile the src code (Without Linkage)
# -o option : write the build output to an output file (Changing default name)
a.out: $(OBJECTS)
	$(CC)	$(CFLAGS)	-o $(EXEC) $(OBJECTS)
#Tabulation Must be Included before the line(s) of recipe(s) or command(s)
ft_strlen.o : ft_strlen.c libft.h
	$(CC)	$(CFLAGS)	-c	ft_strlen.c	

#Removing object files from hard disk
#clean is an "action" called "Phony Targets", others like run, install...
#Compiling program from scratch
#Clean should be at the end of the makefile, so it doesn't run by default
#.Phony is used, so in case a file named "clean" exists make won't mix it with..
.Phony = clean
clean :
	$(RM) $(OBJECTS)

fclean :
	$(RM) $(all)

#Compiling a c files :
# 1 - Pre-processing :
#		- Get rid of comments
#		- Include headers and macros
#		- replace macros by their values
#		- generate .i file (-E option to stop compilation at this stage)
# 2 - The compiler :
#		- produce an IR (Intermediate Representation) (some compiler produce assembly code at this stage)
#		- '-S' option to stop compilation at this step
#		- generate .s file
# 3 - The assembler :
#		- take the IR and produce machine language code (binary)
#		- '-c' to stop the compilation at this step
#		- generate .o files
# 4 - The Linker :
#		- creates the final executable in binary
#		- Role 1 : Linking all source files together (i.e. xs.o && ys.o)
#		- Role 2 : Calling the functions by their definitions (Linker knows where to look for...(static & dynamic library))
# 5 - Executable
#		- given the object files produced in the linker step + libraries if any exists ==> produce an executable a.out
#		- '-o' option to change the name of the executable
#
#-Werror : Turn warnings into errors.

#-----------------------------------------------------------------------------
#		##### Automatic Variables ####
# '%' is a wildcard. if used many times in the same rules, it has the same value
# "$*" refers to the part matched by '%' character
# "$@" refers to full the target name

# "$<" refers to the dependency list matched with the rule
# "@<" First dependency
# "$^" All dependencies
# "$?" Dependencies that have changed 

#https://www.gnu.org/software/make/manual/make.html#Automatic-Variables

# ## Static Pattern rules ##
# https://www.gnu.org/software/make/manual/make.html#Static-Pattern
#-----------------------------------------------------------------------------
#Implicit Rules :
#We can omit the individual C source files from the recipe\
(i.e. omit ft_strlen//Line 18), make will figure it out\
it has an <implicit rule> for updating a ‘.o’ file from a correspondingly \
named ‘.c’ file using a ‘cc -c’ command. 
#We can omit the prerequisites, when a ".c" is used automatically\

#Reference https://www.gnu.org/software/make/manual/html_node/make-Deduces.html#make-Deduces
#-----------------------------------------------------------------------------
#If an implicit Rule is used : You can group entries by their prerequisites \
instead of by their targets. (i.e. $(OBJECTS) = libft.h

#Reference https://www.gnu.org/software/make/manual/html_node/Combine-By-Prerequisite.html#Combine-By-Prerequisite
#-----------------------------------------------------------------------------
#Makefile contains : \
 -An Explicit Rules : How to remake file(s) called "The Rule's target (Target : prerequisites : recipe)\
 -An Implicit Rule : says When and How to remake a class of files based on their names\
 -A Variable Definition : A line that specifies a text string\
 -A directive : Instruction for makefile to do something while reading the makefile\
					-Reading another makefile\
					-Deciding to use or not a part of the makefile\
					-Defining a variable from a verbatim string containing\
						multiple lines\
-'#' : Starts a comments : '\': for multiple lines comment, Any '#'\
								is treated literally\
	Can't comment : Recipe, Within variables, functions calls\
	Comments are not ignored within a define directive
#-----------------------------------------------------------------------------
#command make looks for : GNUmakefile, makefile, and Makefile (Recommended)
#-----------------------------------------------------------------------------
#Commands : \
	- make -f {name} : give to makefile another name \
	- include filenames… : Include directive. make suspend reading the \
							current makefile and reads one or more others\
		Directives can be useful when you have several programs handelded by \
		one single makefile. Or, for generating \prerequisites from \
		source files automatically\
	- -include filenames… : include with a dash, to ignore a specfic makefile\
							sinclude another name for -include


#-----------------------------------------------------------------------------
```

## Ressources :

### Makefile Conventions :
- https://www.gnu.org/software/make/manual/html_node/Makefile-Conventions.html#Makefile-Conventions

### Summary of Options :
- https://www.gnu.org/software/make/manual/html_node/Options-Summary.html#Options-Summary

### Special Built-in Target Names :
- https://www.gnu.org/software/make/manual/html_node/Special-Targets.html#Special-Targets

### Index of Concepts :
- https://www.gnu.org/software/make/manual/html_node/Concept-Index.html#Concept-Index
