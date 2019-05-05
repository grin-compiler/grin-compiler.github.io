---
layout: grin-default
---

- utilize recent pointer analysis and control flow analisis results, useful for:
  - generate much smaller binaries (better dead code elimination)
  - compile faster programs (better strictness analysis)

The project aim is to provide easy to use compiler backend with convenient intermediate language and framework.

# Status

- update tech to use the most recent research results
- update GRIN IR

# Haskell

**[GHC/GRIN]()** is a Haskel frontend with the standard tooling support: Cabal and Stack.

Compiling from STG linking the whole program into a single STG file.

Whole program optimization and interprocedural dead code elimination.

Generates small binaries.

No RTS yet. We need to build a new RTS from scratch supportin all the GHC primops.

**Roadmap:**
- WASM support
- GC implementation
- basic GHC primops (i.e. *arithmetic, arrays, refs*)
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
