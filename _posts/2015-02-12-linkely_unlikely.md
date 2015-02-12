---
layout: post
title: The linkely() and unlikely() macro in Kernel
categories: 
- GCC
- kernel
---
When I read the book 'Linux Kernel Development', first time saw the macro `linkely()` and `unlikely()`, why kerenel need them to do condition test?

Answer from [Stackoverflow](http://stackoverflow.com/questions/109710/likely-unlikely-macros-in-the-linux-kernel-how-do-they-work-whats-their):
> They are an instruction to the compiler to emit instructions that will cause branch prediction to favour the "likely" side of a jump instruction. This can be a big win, if the prediction is correct it means that the jump instruction is basically free and will take zero cycles. On the other hand if the prediction is wrong, then it means the processor pipeline needs to be flushed and it can cost several cycles. So long as the prediction is correct most of the time, this will tend to be good for performance.

So when should use the `likely()` and `unlikely()`? Consider the branch perdictor to improve the performance is importent, **BUT** the more importent is consider which branch you want to be exectued fast! For example, to check the *neclure_leacking*, for the most case is `neclure_leacking == false` and seems we should write `if(unlikely(neclure_leacking)) {do_the_maintaince()} else {run()}`, but obviously when *neclure_leacking == true*, do the `run()` is much more improtant and emergency, should make sure this exectution be run fastest, so the code should change to `if(likely(neclure_leacking)) {run()} else {do_the_maintaince()}`.

##The definitation of these macros(2.6.32)

```c
# define likely(x)      __builtin_expect(!!(x), 1)
# define unlikely(x)    __builtin_expect(!!(x), 0)
```

It's also work for userspace application, but only for GCC compiler, the defination should be wrote as:

```c
#ifdef __GNUC__
#define likely(x)       __builtin_expect(!!(x), 1)
#define unlikely(x)     __builtin_expect(!!(x), 0)
#else
#define likely(x)       !!(x)
#define unlikely(x)     !!(x)
#endif
```
###What's the useful of !! in that macro
The `!!` operation make the `x` convert to a *bool* easily. We don't know what's the type of the `x` is, `!!x` will implicitly convert the `x` to be a bool type.
The explicit way to do the convert is `bool_var = (x != 0)` or `bool_var = x ? true : false`, it's not as short/lazy as the `!!`.


#Reference
[What every Programmer should know about Memory - page 57](http://www.akkadia.org/drepper/cpumemory.pdf)
[Branch Predictor](http://en.wikipedia.org/wiki/Branch_predictor)
[Double negation in C++](http://stackoverflow.com/questions/248693/double-negation-in-c-code/249305#249305)
[Using likely() and unlikely()](http://250bpm.com/blog:6)
