- rustup
- rustc: compiler
- rustfmt: formatter

marcos
ahead-of-time compiled
cargo

- crates
  - crates.io: registry
- trait
- prelude: standard libraries

## Common

### Variable

- immutable

### Data Types

- Strong & Static types system

- Scalar
  - Integer
    - Overflow
  - Float-point
  - Boolean
  - Character
- Compound
  - Tuple
  - Array

### Functions

- Function signatures
- Statement & Expression

### Control FLow

- If-else
- Loop

## Ownership

- Control memory:
  - garbage collector
  - the programmer must explicitly allocate and free the memory
  - Rust: ownership
- Stack
  - fixed size
- Heap
  - pointer
  - allocate
- ownership
  - scope
  - `drop` function - Resource Acquisition Is Initialization (RAII) in C++
  - move
  - `Copy` trait
  - `Drop` trait
- reference
  - pointer
  - borrow
  - mutable reference
  - data race (race condition issues)
  - dangling references
  - slice
    - slice is kind of reference

## Structure

- struct vs reference
- struct vs trait
- method
- `dbg!` macro

## Enums

- Option<T>

## Packages

- `pub`
- `use`

## Error Handling

- panic!: unrecoverable
- Result<T, E>: recoverable

- unwrap()
- expect()
- ? operator

## Generic

- Generic types
- Trait: Share behavior
