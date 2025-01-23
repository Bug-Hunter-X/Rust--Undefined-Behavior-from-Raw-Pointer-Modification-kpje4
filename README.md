# Rust Undefined Behavior Example

This repository demonstrates a common source of undefined behavior in Rust: modifying a vector through a raw pointer after potential reallocation.  The `bug.rs` file contains the buggy code, while `bugSolution.rs` provides a corrected version.

The bug arises from the unsafe access to the vector's internal memory.  Rust's memory management may reallocate the vector's buffer if it needs to grow, invalidating any raw pointers pointing to the old location.  Modifying the memory pointed to by `ptr` after a potential reallocation leads to unpredictable results, including crashes or corrupted data.

The solution uses safe methods provided by the Rust standard library to modify the vector's elements, avoiding the risks associated with raw pointers.