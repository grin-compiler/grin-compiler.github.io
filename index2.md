---
layout: grin-default
---

# Overview

GRIN (Graph Reduction Intermediate Notation) is an intermediate representation and a compiler framework.
GRIN could significantly improve the tooling, performance and size of functional programs and could enable functional technologies to target new platforms like WebAssembly.


Functional languages are compiled in three stages: frontend, functional optimizer, low level / machine code / imperative level optimimization.
While [LLVM](http://llvm.org/) handles the last step perfectly, GRIN as a functional optimizer can capture the original language semantics and can perform transformations that are infeasible at LLVM level.


<img src="GRIN Pipeline.svg" width="50%" >

Currently the following frontends are under development:

- **Haskell**  
  GHC ....
- **Idris**  
  Working ....
- **Agda**  
  Code stub ....

~~GRIN could significantly improve the tooling, performance and size of functional programs and could enable functional technologies to target new platforms like WebAssembly.~~  
GRIN aims to bring the benefits of whole program optimization to wide range of functional programming languages.

*Support the project on [Patreon](https://www.patreon.com/csaba_hruska).*

# Benefits For Programmers

*improving the industrial presence of Haskell*

### Tooling

visual runtime debugger and profiler  
show runtime memory structures, debug lazyness  
highlight optimization effects on source code in the code editor  
*i.e. dead code/data, linear usage, laziness, strictness, tail call, unboxing, stack or heap allocation*  
With the help of Language Server Protocol it would be possible to visualize all of theese cool features.

### Smaller Executables

Whole program analysis helps the compiler to remove dead code and dead data fields more efficiently.  
For example it can effectively remove the unused type class instances.  
In result the executables are much smaller.  
It also cuts down the external dependencies in the program binary.

### Better Performance

Whole program optimization removes lots of redundant computation  
*i.e. unnecessary laziness and redundant memory operations*.  
These simplifications often allows other optimizations to apply.


### New Platforms

functional technologies in resource constrained environments:  

*WebAssembly*  
*Mobile*  
*Gaming Consoles*  
*Embedded Systems*  

why?  



# Benefits For Researchers

*help research and experimentation*

### Analysis Framework

*The whole Haskell program compiled to a single STG then to a GRIN file.  
Good for program static and runtime analysis.  
All GHC primitive operations will be supported by an interpreter and by the native code generator.  
Easy to write interpreters for experiments.  
This framework makes it easy to do experiments on real world haskell programs.*

### Related Work

The GRIN Project aims to utilize the most recent results of compiler research.

*Whole program compilers*

- [A modern look at GRIN, an optimizing functional language back end](http://nbviewer.jupyter.org/github/Anabra/grin/blob/fd9de6d3b9c7ec5f4aa7d6be41285359a73494e3/papers/stcs-2019/article/tex/main.pdf)  
  Overview of GRIN related projects and other whole program compilers.  
  i.e. *Boquist GRIN, UHC, JHC, LHC, HRC, MLton*

- [Intel Labs Haskell Research Compiler](http://www.leafpetersen.com/leaf/publications/hs2013/hrc-paper.pdf) / [Measuring the Haskell Gap](http://www.leafpetersen.com/leaf/publications/ifl2013/haskell-gap.pdf)  
  research compiler that showed the potential of whole program optimization for modern Haskell  
  HRC, FLRC, SIMD Vectorisation

- [MLton](http://mlton.org/)  
  leading industrial strength whole program compiler for SML

*Program analysis*

- [Souffle datalog compiler](https://souffle-lang.github.io/)  
  Souffle synthesizes a native parallel C++ program from a logic specification.  
  It is used to implement *points-to, control flow*  and other analyses efficiently.

- [P4F: Pushdown Control-Flow Analysis for Free](https://arxiv.org/pdf/1507.03137.pdf)  
  advanced control flow analysis for whole program defunctionalization

*Vectorisation*

- [ISPC: Intel SPMD Program Compiler](https://ispc.github.io/)  
  high-performance SIMD programming on the CPU

- [FLRC: Automatic SIMD Vectorization for Haskell](http://www.leafpetersen.com/leaf/publications/icfp2013/vectorization-haskell.pdf)

*Memory management*

- [ASAP Memory Management](https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-908.pdf)

- [Gibbon](https://github.com/iu-parfunc/gibbon) / [Compiling Tree Transforms to Operate on Packed Representations](http://drops.dagstuhl.de/opus/volltexte/2017/7273/pdf/LIPIcs-ECOOP-2017-26.pdf)  
  


# Support

Please support the project on [Patreon](https://www.patreon.com/csaba_hruska).

# Ask Us

[![Gitter chat](https://badges.gitter.im/grin-tech/grin.png)](https://gitter.im/Grin-Development/Lobby)

Please ask if you have any questions. (i.e. *code, design, research, support, etc.*)

**Email:** *csaba.hruska@gmail.com*


# FAQ

**What is the difference between GHC and GRIN?**

**Why is GHC not good enough for you?**

**Can you reuse the GHC runtime for GHC/GRIN?**

