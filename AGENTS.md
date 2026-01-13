# Development Playbook

This document integrates general development guidelines and best practices for this Python repository.

## 1. Development Workflow

### Verification (Manual)
Before committing any code, you must ensure the following pass:
- **Type Checking:** Run `mypy .` to verify type safety.
- **Testing:** Run `pytest`.
  - *Tip:* Run targeted tests (e.g., `pytest tests/test_specific.py`) to avoid unnecessary delays during development, but ensure the full suite passes before finishing.

### Automated Hooks
This project uses `pre-commit` hooks to maintain code quality.
- **Linting & Formatting:** `ruff` and `black` run automatically when you commit.
  - You generally do not need to run these manually.
  - If they modify files, the commit will fail; simply stage the changes and commit again.

## 2. Coding Standards

### Type Annotations
- **Inputs:** Use generic types to allow flexibility (e.g., use `Sequence[str]` instead of `list[str]`, or `Mapping` instead of `dict` if mutable access isn't required).
- **Outputs:** Use specific types for return values to provide clear guarantees to callers.

### Code Structure
- **Simplicity:** Keep the directory structure flat and code logic simple. Avoid over-engineering.
- **OOP Strategy:** When advanced structuring is required:
  - Define a **Base Class** that outlines the interface/methods.
  - Implement **Subclasses** for specific, swappable variants.
  - Avoid deep inheritance hierarchies; prefer composition or flat polymorphism.

## 3. General Guidelines

### Design and Planning
- Ensure you have a clear plan before implementing complex features.
- If a design requires significant changes, outline the architecture or data flow first.

### Git Operations
- Write clear, concise commit messages.
- Ensure all local checks (tests, types) pass before pushing.