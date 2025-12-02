---
title: C/C++ Best Practices
inclusion: fileMatch
fileMatchPattern: '*.{c,cpp,cc,cxx,h,hpp,hxx}'
---

# C/C++ Best Practices

## Code Style
- Follow project-specific style guide (Google, LLVM, or custom)
- Use meaningful variable and function names
- Use snake_case for variables and functions (C style)
- Use PascalCase for classes and structs (C++ style)
- Use UPPER_SNAKE_CASE for macros and constants
- Limit line length to 80-120 characters

## Modern C++ (C++11/14/17/20)
- Prefer `auto` for complex type declarations
- Use `nullptr` instead of `NULL` or `0`
- Use smart pointers (`unique_ptr`, `shared_ptr`) over raw pointers
- Prefer `constexpr` for compile-time constants
- Use range-based for loops when appropriate
- Use `std::string_view` for non-owning string references
- Prefer `std::array` over C-style arrays

## Memory Management
- Follow RAII (Resource Acquisition Is Initialization)
- Avoid manual `new`/`delete`, use smart pointers
- Use `std::vector` instead of dynamic arrays
- Check for memory leaks with Valgrind or AddressSanitizer
- Initialize all variables

## Error Handling
- Use exceptions for exceptional cases (C++)
- Return error codes for expected failures (C)
- Use `std::optional` for nullable return values (C++17)
- Use `std::expected` or Result types for error handling (C++23)
- Check return values of system calls

## Build System
- Use CMake for cross-platform builds
- Use Meson or Bazel for complex projects
- Enable all warnings: `-Wall -Wextra -Wpedantic`
- Use `-Werror` in CI to treat warnings as errors
- Enable sanitizers in debug builds: `-fsanitize=address,undefined`

## Testing
- Use Google Test, Catch2, or doctest for unit testing
- Run tests with minimal output: `ctest --output-on-failure -j$(nproc)`
- Use CTest for test orchestration
- Mock external dependencies
- Test edge cases and error conditions

## Code Organization
- One class per header/source file pair
- Use include guards or `#pragma once`
- Forward declare when possible to reduce compile times
- Separate interface (.h) from implementation (.cpp)
- Use namespaces to avoid name collisions

## Performance
- Profile before optimizing
- Use `const` and `constexpr` liberally
- Prefer stack allocation over heap
- Use move semantics for expensive copies
- Consider cache locality in data structures
