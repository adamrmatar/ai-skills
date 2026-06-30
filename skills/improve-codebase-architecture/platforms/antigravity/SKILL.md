---
name: improve-codebase-architecture
description: >-
  How to refactor, format, and structure a codebase that has been cluttered or corrupted by AI-generated boilerplate code (slop).
---

# Improve Codebase Architecture (De-Slop)

Use this skill to refactor, streamline, and restructure files that have become cluttered, bloated, or fragmented by excessive AI-generated boilerplate.

## 🛠️ Step-by-Step Refactoring Workflow

1. **Establish a Baseline**: Run existing unit tests and linters before making any modifications to ensure you don't introduce regressions.
2. **Identify Slop**: Look for:
   - Duplicate utility functions or redundant helper modules.
   - Files containing large blocks of unused imports.
   - Functions with excessive complexity or unneeded abstraction layers.
3. **Consolidate and De-duplicate**: Extract duplicate logic into a shared helper module and remove duplicate code paths.
4. **Simplify Imports**: Group imports logically and prune unused references.
5. **Verify Changes**: Rerun unit tests and confirm the refactoring did not alter the runtime behavior of the codebase.

