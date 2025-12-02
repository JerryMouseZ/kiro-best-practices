---
title: Rust Best Practices
inclusion: fileMatch
fileMatchPattern: '*.rs'
---

# Rust Best Practices

## Code Style
- Follow Rust API Guidelines and rustfmt defaults
- Use snake_case for variables, functions, and modules
- Use PascalCase for types, traits, and enums
- Use SCREAMING_SNAKE_CASE for constants and statics
- Limit line length to 100 characters

## Ownership and Borrowing
- Prefer borrowing over ownership when possible
- Use `&str` for string parameters, `String` for owned strings
- Use `&[T]` for slice parameters, `Vec<T>` for owned collections
- Avoid unnecessary clones
- Use `Cow<T>` for flexible ownership

## Error Handling
- Use `Result<T, E>` for recoverable errors
- Use `Option<T>` for optional values
- Use `?` operator for error propagation
- Create custom error types with `thiserror`
- Use `anyhow` for application-level error handling
- Avoid `unwrap()` and `expect()` in library code

## Type System
- Leverage the type system for correctness
- Use newtypes for type safety
- Prefer enums over boolean flags
- Use generics and traits for abstraction
- Implement standard traits: `Debug`, `Clone`, `PartialEq`

## Concurrency
- Prefer message passing over shared state
- Use `Arc<Mutex<T>>` sparingly
- Consider `tokio` or `async-std` for async code
- Use `rayon` for data parallelism
- Avoid `unsafe` unless absolutely necessary

## Testing
- Write unit tests in the same file with `#[cfg(test)]`
- Use `cargo test -- --quiet` for minimal output
- Filter tests: `cargo test test_name`
- Use `#[should_panic]` for panic tests
- Use `proptest` or `quickcheck` for property-based testing
- Mock with `mockall` or trait objects

## Dependencies
- Use `cargo-audit` for security vulnerabilities
- Keep dependencies minimal and well-maintained
- Pin versions in `Cargo.lock` for applications
- Use features to reduce compile times
- Prefer `no_std` compatible crates when possible

## Performance
- Use `cargo bench` with criterion for benchmarks
- Profile with `perf`, `flamegraph`, or `cargo-flamegraph`
- Use `#[inline]` judiciously
- Prefer iterators over manual loops
- Use `&mut` instead of returning new values when appropriate

## Documentation
- Document public APIs with `///` doc comments
- Include examples in documentation
- Use `cargo doc --open` to preview docs
- Add `#![deny(missing_docs)]` for library crates
