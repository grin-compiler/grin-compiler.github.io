---
layout: grin-default
---

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

- update tech to use the most recent research results
- update GRIN IR

# Haskell

GHC does incremental (per module) compilation. That was the best design decision back then.

The goal of the GRIN project is to explore the design space of whole program optimization an unleash the performance and tooling benefits of it.

**[GHC/GRIN]()** is a Haskel frontend with the standard tooling support: Cabal and Stack.

Compiling from STG linking the whole program into a single STG file.

Whole program optimization and interprocedural dead code elimination.

Generates small binaries.

No RTS yet. We need to build a new RTS from scratch supportin all the GHC primops.

**Roadmap:**
- WASM support
- basic GHC primops (i.e. *arithmetic, arrays, refs*)
- tooling (profiler, debugger)
- GC implementation
- full GHC primops

# Idris

Working backend, with multiple sample programs.

**Roadmap:**

# Agda

Initial stub exists.

# Reserach papers

- Souffle
- P4F
- HRC / Haskell Gap
- MLton

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
