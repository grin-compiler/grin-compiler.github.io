---
layout: grin-default
---

# Overview

GRIN is a compiler framework and an intermediate representation. It is short for *Graph Reduction Intermediate Notation*.
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

*GRIN gives framework for functional language experimentation.*

### Analysis Framework

Whole program compilation makes easy to observe and analyse programs.
I.e. researchers can use GHC/GRIN to experiment with real world functional programs.
GHC/GRIN compiler pipeline can serialize either the STG level and GRIN level intermediate representation (IR) for the whole program.
With this framework it is easily to convert large Haskell programs to a research IR.
We also plan to support all GHC primitive operations in the GRIN interpreter and GRIN native code generator.

### Related Work

The GRIN Project aims to utilize the most recent results of compiler research, especially pointer analysis and whole program optimization.

*Whole program compilers*

- [A modern look at GRIN, an optimizing functional language back end](http://nbviewer.jupyter.org/github/Anabra/grin/blob/fd9de6d3b9c7ec5f4aa7d6be41285359a73494e3/papers/stcs-2019/article/tex/main.pdf)  
  Our recent paper gives an overview of GRIN related projects and other whole program compilers.  
  i.e. *Boquist GRIN, UHC, JHC, LHC, HRC, MLton*

- [Intel Labs Haskell Research Compiler](http://www.leafpetersen.com/leaf/publications/hs2013/hrc-paper.pdf) / [Measuring the Haskell Gap](http://www.leafpetersen.com/leaf/publications/ifl2013/haskell-gap.pdf)  
  HRC is a research compiler that showed the performance effect of whole program optimization on Haskell. 

- [MLton](http://mlton.org/)  
  MLton is the leading industrial strength whole program compiler for SML. It showcased that whole program compilation is feasible with low compile times.

*Program analysis*

- [Souffle datalog compiler](https://souffle-lang.github.io/)  
  Souffle synthesizes a native parallel C++ program from a logic specification.
  It is used to implement *points-to, control flow*  and other analyses efficiently.

- [P4F: Pushdown Control-Flow Analysis for Free](https://arxiv.org/pdf/1507.03137.pdf)  
  P4F is an advanced control flow analysis. It can boost the optimizer efficiency with providing sophisticated control flow information.

*Vectorisation*

- [ISPC: Intel SPMD Program Compiler](https://ispc.github.io/)  
  Simple Program Multiple Data ([SPMD](https://en.wikipedia.org/wiki/SPMD)) is the programming model used by the GPUs.
  ISPC implements the SPMD model on CPU SIMD vector instructions like SSE and AVX.
  It proves that interprocedural data flow vectorisation can be much more performant than loop vectorisation.


- [FLRC: Automatic SIMD Vectorization for Haskell](http://www.leafpetersen.com/leaf/publications/icfp2013/vectorization-haskell.pdf)  
  Intel Labs Haskell Research compiler utilized a SIMD vectorisation optimization that was specially designed for pure functional languages.

*Memory management*

- [ASAP Memory Management](https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-908.pdf)  
  ASAP (*As Static As Possible*) describes a compile time automatic memory management system using whole program analysis.
  It essentially generates specialized garbage collector for each compiled program.
  With ASAP it seems possible to run Haskell programs without run time garbage collector.

- [Gibbon](https://github.com/iu-parfunc/gibbon) / [Compiling Tree Transforms to Operate on Packed Representations](http://drops.dagstuhl.de/opus/volltexte/2017/7273/pdf/LIPIcs-ECOOP-2017-26.pdf)  
  Gibbon is a research compiler that experiments with packed memory data representation.
  It compiles functional programs to work with pointerless data representation which reduces cache misses and improves runtime performance.
  This techique essentially turns data (de)serialization into raw memory copy.


# Support

Please support the project on [Patreon](https://www.patreon.com/csaba_hruska).

# Ask Us

[![Gitter chat](https://badges.gitter.im/grin-tech/grin.png)](https://gitter.im/Grin-Development/Lobby)

Please ask if you have any questions.  
(i.e. *code, design, research, support, etc.*)

**Email:** *csaba.hruska@gmail.com*


# FAQ

**What is the difference between GHC and GRIN?**  
answer...

**Why don't you improve GHC instead of GRIN?**  
answer...

**Can you reuse the GHC runtime for GHC/GRIN?**  
answer...

