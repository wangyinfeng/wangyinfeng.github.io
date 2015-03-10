---
layout: post
title: Why 'undefined reference' comes out
category: C
---
When I worked on an issue, was confused by the "undefined reference to ...".
#The background
Someone add a new global variable in his module, and declare it in a header file which locate in the public `include` folder. My misson is use the new global variable in my module to do something, so I include the header file, and reference the variable, when compile(I suppose is the link stage) the error comes out. My confuse is the global variable is declared and I've include the header file, why the symbol not found during link?

Well, after do some test and discuss with someone, it's because when gcc link my module, it really don't know what's the symbol is. Each global variable has a address in the binary file, the header file just tell you the symbol exist at somewhere, but not tell you where it is, so the linker will try to find the symbol like say in some global symbol table, but the symbol is defined in another module and you're not linked that module to your own module, so symbol mission will happen and the error will throw out.

The fix is simple, when do link, provide the .o file which contain the symbol; or move the definition to some `shared` module, such as some library module, so we can use the `-L` to include that library. 

