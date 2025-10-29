---
applyTo: "**/*.py"
---

# Python Language-Specific Copilot Instructions

## Language Features

- Use Python 3.10+ features (e.g., structural pattern matching).
- Always use f-strings for string formatting.
- Prefer `pydantic` instead of `dataclasses`.
- Use `loguru` for logging.

## Project Structure

- Use a modular design: separate files for models, services, controllers, and utilities.
- Manage configuration with environment variables.
- Follow a clear `src`-layout structure:
    ```text
    src/
    ├── <app-name>/
    │   ├── __init__.py
    │   ├── ... (other modules)
    │   └── main.py
    tests/
    ├── __init__.py
    └── ... (test modules)
    docs/
    config/
    bin/                # (if needed) command-line scripts or executables
    ````

## Coding Standards

- Add typing annotations to all functions and classes, including return types.
- Prefer classes over standalone functions, except for simple utilities.
- Add descriptive docstrings to all functions and classes (PEP 257). Update existing docstrings when modifying behavior.
- Use Ruff for code style consistency: `poetry run ruff <args>`.

## Testing

- Use `pytest` (not `unittest`) and pytest plugins for all tests.
- Place all tests in `./tests`. Add `__init__.py` files as needed.
- Ensure all tests include typing annotations and docstrings.

## Documentation & Dependency Management

- Use docstrings and README files for documentation.
- Use `poetry` for dependency management.
