# ARM ASM helper library


## Summary of things you care about

This repo endeavours to provide the initalization vectors, etc. that are
absolutely required for running pure Assembly programs on ARM Microcontrollers.

This means:


1. An appropriate $CPU.ld framework for you to use

2. An appropriate initial entrypoint (ie: reset handler) for you to use
    This comes in the form of a vector.o file.

    Technically, you could link against the whole libXXXXX.a, and it will pull out
	just your vector.o file. 
    And/or you can manually extract it from the lib, with something like
	
	  ar x lib/libopencm3_stm32f4.a  vector.o

3. A set of standardized ASM register definitions/offsets for you to use.
    Kindasorta a Hardware Abstraction Layer, except still very close to hardware!

Everything else will be ignored.





## What register definitions are available for me to use?

(This is a work-in-progress. Volunteers to add more code are encouraged)

I'm going to try to keep a top level test file, that just loads in values
but doesnt actually do anything with them.
Define your CPU, and try to build it. If it doesnt build, then you know 
theres a problem with support for that CPU varient



## This Fork vs Upstream

Given the purpose of this repo (Pure ASM), all the C code in this repo
(with the exception of the initialization/vector code) is going to be IGNORED.
It might not even compile any more.

However, in order to simplify comparisons with the original upstream codebase, it 
is going to be left in (at least for now)


## Background and details
I found the libpencm3 library to be a great 95% solution, to my ASM
programming interests.
Unfortunately, I do need that last 5% as well.
I wanted a solution that can be used to deploy pure ASM programs onto this
type of hardware, with zero use of libc, or any C constructs.

So, my work here is

1. Primarily (only?) under the stm32 tree

2. going to be a bit brute-force-ish. I'm not going to support the weird, noncompliant 
hardware. Only the "nice" hardware

This latter means that, when all the stm cpus use an RCC register clock enable
for the GPIO features that start at bit0... 
EXCEPT for f0, f1, and f3 models...

Im going to ditch support for those models, rather than making the RCC #defines way 
more complicated than they would have to be.













# Original README

You may be interested in the original README file, preserved here as
[[README_orig.md]]
