---
layout: grin-default
---

[index2](index2)

**Page Status: work in progress**

GRIN is a compiler backend and an intermediate language.
The goal is to bring the benefits of whole program analysis and optimization for functional languages especially Haskell.  
The main benefits are:
  - **smaller executables** *(more accurate dead code elimination)*
  - **faster programs** *(better strictness analysis and unboxing)*

- utilize recent pointer analysis and control flow analisis results, useful for:
  - generate much smaller binaries (better dead code elimination)
  - compile faster programs (better strictness analysis)

The project aim is to provide easy to use compiler backend with convenient intermediate language and framework.

HIGHLIGHT: whole program analysis and optimization

BENEFIT:
- analyse real world programs (GHC/GRIN ; STG/Lambda export)

# Status

Urban Boquist's PhD thesis on
<a href="http://nbviewer.jupyter.org/github/grin-tech/grin/blob/master/papers/boquist.pdf">
Code Optimisation Techniques for Lazy Functional Languages
</a>.

Paper: <a href="http://nbviewer.jupyter.org/github/Anabra/grin/blob/fd9de6d3b9c7ec5f4aa7d6be41285359a73494e3/papers/stcs-2019/article/tex/main.pdf">
A modern look at GRIN, an optimizing functional language back end
</a>

- update tech to use the most recent research results: *Souffle/datalog, P4F, Steensgaard based points-to analysis*
- update GRIN IR: *introduce basic blocks*

# Language Frontends

## Haskell: GHC/GRIN

It is crutial to use GHC as a Haskel frontend to support the widest range of libraries. GHC/GRIN is 
GHC is patched to emit STG representation. The STG modules are linked together and processed by the GRIN compiler.

GHC does incremental (per module) compilation. That was the best design decision back then.

The goal of the GRIN project is to explore the design space of whole program optimization an unleash the performance and tooling benefits of it.

**[GHC/GRIN]()** is a Haskel frontend with the standard tooling support: Cabal and Stack.

Compiling from STG linking the whole program into a single STG file.

Whole program optimization and interprocedural dead code elimination.

Generates small binaries.

No RTS yet. We need to build a new RTS from scratch supporting every GHC primop.
TODO: why we need a new RTS.
  
**Roadmap:**
- WASM support
- basic GHC primops (i.e. *arithmetic, arrays, refs*)
- tooling (profiler, debugger)
- GC implementation
- full GHC primops

## Idris/GRIN

Working backend, with multiple sample programs.

**Roadmap:**

## Agda/GRIN

Initial stub exists.

# Reserach papers

- **[Souffle](https://souffle-lang.github.io/):** *efficient datalog compiler for performant program analyses*
- **[P4F](https://arxiv.org/pdf/1507.03137.pdf):** *advanced control flow analysis for whole program defunctionalization*
- **[HRC](http://www.leafpetersen.com/leaf/publications/hs2013/hrc-paper.pdf) / [Measuring the Haskell Gap](http://www.leafpetersen.com/leaf/publications/ifl2013/haskell-gap.pdf):**
      *research compiler that showed the potential of whole program optimization for modern Haskell*
- **[MLton](http://mlton.org/):** *leading industrial strength whole program compiler for SML*

# Tooling research

# Research directions

- ASAP Memory Management
- SPMD
- HRC vectorisation
- LLVM type system
- use Gibbon transformations to obtain packed data representation

# Related project

- JHC
- LHC
- HRC
- MLton
