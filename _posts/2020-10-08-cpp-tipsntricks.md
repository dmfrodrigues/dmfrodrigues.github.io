---
layout: post
title: "C/C++ tips & tricks under GNU"
date: 2020-07-14 18:37:37 +0100
---

Here are some tips and tricks that I found useful when programming in C/C++ under Linux, using the GNU GCC compiler suite. I will focus on the ones that I found useful, as can be seen from the fact I only mention a few pragmas when in fact the list of possible pragmas is quite long.

## Pragmas

Pragmas are compiler directives which specify how a program should be compiled. Specifically, directives are processed by the C/C++ preprocessor. You are probably already familiar with some directives: `#define`, `#include`, `#ifdef`, `#ifndef` and `#endif` which are essential to header inclusion and header guards. Here, I will mention what I would call *pragmas in a strict sense*, which are C/C++ compiler directives starting with `#pragma`, which is an extremely powerful construct.

The first and most common pragma is `#pragma once`, which is a non-standard but widely-supported directive that instructs the compiler to include the current file only once in a single compilation, effectively replacing the more verbose and error-prone C header guards. However I tend to use this as sparsely as possible, because of the vast amount of C code developed using header guards in the past, and also because I learned header guarding first instead of `#pragma once`. It is mostly a matter of taste, but usage should be consistent across a project (although I believe there are no side effects to mixing header guards and `#pragma once`).

Pragmas are compiler-specific and each compiler may assign any meaning it wants to any pragma, but we will focus on GNU GCC pragmas, which start with `#pragma GCC`. I will focus only on the ones I found most useful, but you can find more about other types of pragmas [here](https://gcc.gnu.org/onlinedocs/gcc/Pragmas.html#Pragmas);

### Getting rid of compiler warnings: diagnostic pragmas

Diagnostic pragmas allow you to:

1. Enable/disable certain types of diagnostics, so the compiler won't annoy you with a warning about something you did on purpose; for instance, if you use floats from a finite set of floats you can legitimately compare them (assuming there are no intermediate conversions that might change the float) but the compiler will still raise a `-Wfloat-equal`.
2. Change the kind of diagnostic. For instance, you might have specified that you want all warnings to be considered errors with `-Werror`, but maybe you want one specific warning to remain as such instead of being considered an error.

Diagnostic pragmas all start with `#pragma GCC diagnostic`, and have a pretty simple syntax. Diagnostic pragmas operate using a sort of policy stack, where you can push and pop diagnostic policies from that stack. The way it operates is using the following pragmas:

- `#pragma GCC diagnostic <kind> <option>` changes the disposition of a diagnostic; `<kind>` is one of `warning`, `error` or `ignored`, and `option` is a compiler option that would raise a warning/error; for instance, to disable checking of warning in a region of code, the directive `#pragma GCC diagnostic ignored "-Wfloat-equal"` could be used.
- `#pragma GCC diagnostic push` pushes the current diagnostics policy to a stack, and the current policy is a copy of the policy that was pushed to the stack.
- `#pragma GCC diagnostic pop` replaces the current policy with the one at the top of the policies stack, and pops the stack; basically restores the policy that was being used before the last time `push` was called.

Thus, the main use case is one where you have, for instance, a function that raises a certain warning `-Wfloat-equal` that you'd rather ignore for that section; then you'd use something along these lines:

```cpp
bool equals(float a, float b) {

#pragma GCC diagnostic push                     // Push the old policy into stack
#pragma GCC diagnostic ignored "-Wfloat-equal"  // Ignore "-Wfloat-equal"

    return a == b;

#pragma GCC diagnostic pop                      // Restore the old policy

}
```

This set of pragmas should be used sparingly, otherwise you may miss important warnings. This means that each `push` should have a corresponding `pop` to restore the general diagnostics policy, that the code section wrapped between `push`/`pop` should be as short as possible, and that the new policy should have the least amount of changes possible so your diagnostics policies don't become harder to remember than your own code.

### Making your program faster: tuning

Tuning is the art of making your program faster when running in a specific processor. There is much to say about tuning as it is a very relevant matter, but we're going to stick to the basics.

You can customize your optimization level with the `-O` flags, but there is only so much that can be done by the compiler without compromising portability too much (i.e., even though we are always warned that each compiler should be used for each processor, almost all Windows binaries and most Linux binaries are portable). But what if you know your users will compile your program in their own computers, and you wanna squeeze out a few milliseconds? Then you can use pragmas to tell the compiler to compile/tune targeting a specific architecture. By far the easiest use case is simply placing `#pragma GCC target("tune=native")` to tell the compiler to tune the resulting binaries to the current processor. As said before, compilers are free to interpret pragmas in any way they want, so it might not do anything, or even make the program a bit slower. I have not managed to find much documentation on this specific pragma, but it is widely known in competitive programming to squeeze a bit of time out of programs in less serious competitions (as most important competitions explicitly prohibit pragmas and competitors that use pragmas risk disqualification).

Anyway, don't trust on these shenanigans to make your slow code faster; improvements are usually in the orders of 5-10% because compilers already do a pretty good job as-is, so if you think your code should be faster you should do the following instead:

1. Approach the problem from the algorithmic point of view; try to find new/better algorithms or algorithmic optimizations.
2. Know your language very well, so you can play around with data types; these can make a big difference: don't use doubles if floats suffice, don't use longs if ints suffice, and don't use floats if longs/ints suffice, since floating-point arithmetics are slower than integer arithmetics, and arithmetics with longer types (double/long) are slower than shorter types (float/int). Make use of bitsets and other techniques.
3. Only then, if you've applied the two previous steps, should you resort to tuning.

## Attributes

## Doxygen
