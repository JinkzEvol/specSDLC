---
description: "Portable coding standards focused on readability, safety, and maintainability."
applyTo: "**"
---

# Coding Standards

- Keep files focused and reasonably small.
- Prefer explicit types at public boundaries.
- Avoid mutation unless the local language or framework strongly expects it.
- Handle errors explicitly.
- Validate external input at system boundaries.
- Keep production logging structured and safe.
- Favor simple, testable functions over hidden side effects.

## Before marking work complete

- code is readable
- boundary types are clear
- error handling exists
- configuration is not hardcoded
- risky side effects are tested

