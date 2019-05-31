---
layout: grin-default
---

# Overview

GRIN is short for *Graph Reduction Intermediate Notation*, and it is an intermediate representation and a compiler framework.
GRIN could significantly improve the tooling, performance and size of functional programs and could enable functional technologies to target new platforms like WebAssembly.


Functional languages are compiled in three stages:
1. Language frontend
2. High level optimizer *(functional)*
3. Low level optimizer *(imperative)*

While [LLVM](http://llvm.org/) handles the last step perfectly, GRIN as a functional optimizer can capture the original language semantics and can perform transformations that are infeasible at LLVM level.


<img src="GRIN Pipeline.svg" width="50%" >

Currently the following language frontends are under development:

- **Haskell**  
  The Haskell language evolves with the Glasgow Haskell Compiler. GHC development is usually focused on language features and high level optimization while the machine code generator gets less attention.
  [GHC/GRIN](https://github.com/grin-compiler/ghc-grin) is a combination of GHC's Haskell language frontend and the GRIN optimizer.
  It is work in progress, check its [current status](https://github.com/grin-compiler/ghc-grin#status).
- **Idris**  
  Adding GRIN optimizer to Idris compiler pipeline will make programs faster and smaller.
  [Idris/GRIN](https://github.com/grin-compiler/idris-grin) can compile many programs but the runtime is [work in progress](https://github.com/grin-compiler/idris-grin#status).
- **Agda**  
  Plugging GRIN optimizer after Agda frontend is on our roadmap but currenly [Agda/GRIN](https://github.com/grin-compiler/agda-grin) is only an initial code stub.

GRIN aims to bring the benefits of whole program optimization to wide range of functional programming languages.

*Support the project on [Patreon](https://www.patreon.com/csaba_hruska).*

# Benefits For Programmers

*GRIN helps to improve the industrial presence of Haskell.*

### Tooling

Good tooling is essential for industrial software development. Whole program compilation makes it easy to observe the program both in runtime and compile time.
This makes it easier to build good visual debugger and profiler tools. With such runtime tooling it would be possible to *show memory structures, debug laziness and visualize unevaluated expressions.*  
Having access to the whole program could improve the code editor experience also. It would be possible to highlight optimization effects on source code,
*i.e. dead code/data, linear variable usage, laziness, strictness, tail call, unboxing, stack/heap allocation.*  
It seems feasible to implement these cool features using Language Server Protocol and GRIN.

### Smaller Executables

Whole program analysis helps the compiler to remove dead code and dead data fields more effectively.
E.g. it can remove the unused type class instances. This results much smaller executables.
It also cuts down the number of referenced external libraries and symbols in the program binary which make programs more portable.

### Better Performance

Whole program optimization can remove lots of redundant computation,
*i.e. unnecessary laziness and redundant memory operations*.
These program simplifications often allows other optimizations to apply.
GRIN represets memory operations and laziness explicitly. This allows agressive memory layout optimizations, *i.e. unboxing, turning heap values to stack/register values.*
GRIN also eliminates indirect function calls which enables LLVM to perform more optimizations.


### New Platforms

GRIN uses LLVM for machine code generation. LLVM provides roboust tooling and support for all mainstream platforms.
With this design choice the main platforms can be easily supported, *i.e. x64, ARM, WebAssembly* covering desktop, mobile and web.


# Benefits For Researchers

*GRIN gives framework for research and experimentation.*

### Analysis Framework

In case of GHC/GRIN... give some context  
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
answer...

**Why is GHC not good enough for you?**  
answer...


**Can you reuse the GHC runtime for GHC/GRIN?**  
answer...

