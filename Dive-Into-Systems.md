# Notes on C Programming

## Comments in C
- **Multiline comments**: Begin with `/*` and end with `*/`.
- **Single-line comments**: Begin with `//`.

---

## The `main` Function in C
```c
int main(void) { }
```
- Defines the main function.
- The main function:
  - **Returns a value of type `int`**:
    - `int` is C’s type for specifying signed integers (e.g., `-3`, `0`, `1234`).
    - Returning `0` signifies that the program ran to completion without errors.
  - **Uses `void` as a parameter**:
    - Indicates that the function does not expect to receive any arguments.
  - Future implementations may take parameters to receive command-line arguments.

---

## Running a C Program
1. On a Unix system, C code must be compiled before running:
   - Use a C compiler (e.g., GNU C Compiler, GCC).
   - Compilation produces a binary executable (default name: `a.out`).

2. **Example: Compiling and Running `hello.c`**
   ```bash
   $ gcc hello.c
   $ ./a.out
   ```

3. After compiling, the binary executable can be run directly on the system.

---
