---
layout: post
title: "Paranoid C/C++ warnings"
date: 2020-07-08 23:37:22 +0100
---

I started programming in C++ around the summer of 2016, essentially because I knew that, however useful it could be for my academic life, the knowledge I had about TI-BASIC would not be of much use for the things I aspired most: learning a fast and useful language, that would be practical for my small projects as well as a starting point for my endeavour into competitive programming.

Codeblocks is definitely a good tool for starters, but as soon as you grab a hold of the language itself you should take a step back and start asking questions like "what is my IDE doing for me?". One of the first things you probably heard before learning the languages themselves is that C/C++ are *compiled* languages; well then where is the compiler?

## Warnings are your friends

Warnings are the way the compiler has to tell you "I'm gonna compile that, but I'm not too happy about what I just saw". Say you really want your code to be bullet-proof; warnings can help with that by pointing out dangerous constructs that could induce errors.

## Being paranoid

The more extensive the list of active warnings (the more *paranoid* you are), the more problems you can find and fix. We could be tempted to demand something like [CLang's `-Weverything`](https://clang.llvm.org/docs/UsersManual.html#cmdoption-Weverything). It is well-known that `-Weverything` should not be used in production, as its behaviour might be somewhat unpredictable or unwanted; it is however useful to have a comprehensive list of available warnings that can be activated and usually give rise to better coding.

In general, you always want to be careful about what C/C++ standard you will use. Other than that, most details depend on the compiler system.

## Being paranoid in GNU

[GNU GCC](https://gcc.gnu.org/) is a compiler system produced by the GNU project. It is one of the most well-known compiler systems, mostly because it is free, readily available and its history is intrinsically connected to that of Unix systems. It most notably includes the compilers `gcc` mostly for C and `g++` mostly for C++, although usually one is an alias of the other with some extra flags.

First time into a GNU compiler (`gcc`/`g++`), you're told to use `-Wall` to activate lots of useful warnings. As you probably already experienced, `-Wall` does not activate *all* warnings, instead enabling all generally useful warnings. In fact, [`gcc`](https://man7.org/linux/man-pages/man1/gcc.1.html)/[`g++`](https://man7.org/linux/man-pages/man1/g++.1.html) have many more warnings that are not enabled by default nor by `-Wall`, including warnings about:

- Ignored return values
- Conversions with precision loss
- A `switch` missing a `default` case
- Unused or unreachable functions and pieces of code

and many more.

Before going into specifics of compilation flags, there is an interesting feature of GNU compilers: you can assign some names with *attributes* (`__attribute__`), which are to be understood by the GNU compilers. One that I find particular is the `__attribute__((warn_unused_result))`, which warns you if you are ignoring the result of that function somewhere else in your code. This can be useful to remind you the result of that function is important, or otherwise that you should never forget to handle return codes.

### Being paranoid in GNU G++

Here is a list of `g++` warnings I usually find useful (most of them are self-descriptive, although I will focus on some of them):

```sh
-g -pedantic -Wall -Wcast-align -Wcast-qual -Wchar-subscripts -Wcomment -Wconversion
-Wdisabled-optimization -Weffc++ -Wextra -Wfloat-equal -Wformat -Wformat-nonliteral -Wformat-security
-Wformat-y2k -Wformat=2 -Wimport -Winit-self -Winline -Winvalid-pch -Wmissing-braces
-Wmissing-field-initializers -Wmissing-format-attribute -Wmissing-include-dirs -Wmissing-noreturn
-Wpacked -Wpadded -Wparentheses -Wpointer-arith -Wredundant-decls -Wreturn-type -Wsequence-point -Wshadow
-Wsign-compare -Wstack-protector -Wstrict-aliasing -Wstrict-aliasing=2 -Wswitch -Wswitch-default
-Wswitch-enum -Wtrigraphs -Wuninitialized -Wunknown-pragmas -Wunreachable-code -Wunsafe-loop-optimizations
-Wunused -Wunused-function -Wunused-label -Wunused-parameter -Wunused-result -Wunused-value
-Wunused-variable -Wvariadic-macros -Wvolatile-register-var -Wwrite-strings
```

I will only briefly expose the ones that might not be as clarifying:
- `-g` enables debug symbols (used by debuggers); it does not impact performance, as debug symbols are not written in the same section as the code.
- `-pedantic` issues warnings demanded by strict ISO C++, and rejects some programs that do not abide to it. ISO C++ is the succession of standardized versions of C++ (the most broadly supported, decently recent version is C++11). This is because different compilers use different *dialects* of the C++ language, because they are used in specific dominia or simply because compilers evolve in different directions. Using this flag assures the code will compile in the vast majority of C++ compilers.

That being said, there are some of those warnings that should be used with a pinch of salt:
- `-Weffc++` warns about violations of the style guidelines from Scott Meyers' [Effective C++](https://books.google.pt/books/about/Effective_C++.html?id=jP01PwAACAAJ&source=kp_book_description&redir_esc=y). Some of those violations are useful, but most are too strict and don't point to potential code problems, as not even the standard library headers obey all of these guidelines. Use this flag as rarely as possible.
- `-Winline` warns about a function that was declared as `inline` but was not inlined. This is usually not helpful as it has to do with compilers' choice to inline a function or not, which can seem arbitrary.
- `-Wpadded` warns if a structure or class was padded to align an element of the structure, or to align the whole structure. The organization of a structure's fields can have an impact on its total size if the compiler enforces [alignment](https://en.wikipedia.org/wiki/Data_structure_alignment) to improve performance. This is a mere suggestion in case you may care about structure size, otherwise it is not that useful and in most cases has hardly anything to do with code quality.

### Being paranoid in GNU GCC

Similarly, here is a list of `gcc` warnings I usually find useful:

```sh
-pedantic -Wall -Wbad-function-cast -Wcast-align -Wcast-qual -Wextra -Wfloat-equal -Wformat-nonliteral
-Winline -Wmissing-declarations -Wmissing-prototypes -Wnested-externs -Wno-unused-parameter
-Wpointer-arith -Wshadow -Wstrict-prototypes -Wundef -Wunused-parameter -Wunused-result -Wwrite-strings
```

Take special care with the following warnings:

- `-Wmissing-declaractions` warns if a global function is defined without a previous declaration. The point is to find global functions that are not declared in header files, otherwise it is not a problem.
- `-Wmissing-prototypes` warns if a global function is defined without a previous **prototype** declaration.

These warnings refer to a nuance of C standards; from C11 we roughly have that:
- A *declaration* specifies the interpretation and attributes of a set of identifiers.
- A function *prototype* is a declaration of a function that declares the types of its parameters.

This means a *declaration* only introduces a name (of a variable, a function, etc.), whereas a *prototype* only applies to a function and means you specify the number and type of arguments it will receive.

As a brief example,
```c
int f();
```
is a *declaration*, as it only declares function `f` returning an `int`, but does not specify the number or type of its arguments (compiler assumes any number of arguments of any type can be passed to `f`). This differs from the following *prototypes*, as they all specity the number and type of their arguments:
```c
int g(void);  // Declares function g returning int and receiving no arguments
int h(int a); // Declares function h returning int and receiving one argument of type int
```

A missing prototype is usually an avoidable sign of bad code.

## Being paranoid in MSVC

[Microsoft Visual C++](https://en.wikipedia.org/wiki/Microsoft_Visual_C%2B%2B) is an IDE from Microsoft for the C and C++ languages, which also includes the Microsoft C++ (MSVC) C and C++ compilers and linker. These are controlled by `cl.exe`, which in layman's terms is what we call a *compiler*; formally, `cl.exe` coordinates MSVC compilers and linker, and `gcc`/`g++` are not compilers as they also run the linker when needed. Either way, `cl.exe` and `gcc`/`g++` are almost equivalent in terms of objective.

In terms of warnings, MSVC is pretty straightforward: 

- `/W0` suppresses all warnings
- `/W1` displays severe warnings
- `/W2` displays level 1 and significant warnings
- `/W3` displays level 2 and production quality warnings
- `/W4` displays level 3 and informational warnings
- `/Wall` includes absolutely all warnings
- `/GS` detects some exploits related to buffer overruns, by analysing the code in compile time and making small changes to avoid some hacks. Is enabled by default.
- `/sdl` adds more security checks and enables additional warnings. It is a superset of `/GS` and is disabled by default.

MSVC is not as familiar to me as GNU GCC, so there's not much I can add to it. If you are familiar to GNU GCC and struggle to understand how MSVC works, or if you otherwise prefer a free alternative for native Windows applications, try [MinGW-W64](https://www.mingw-w64.org/).
