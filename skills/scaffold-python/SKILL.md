---
name: scaffold-python
description: Bootstraps Python repositories with standard uv Makefile, .gitignore, and pyproject.toml tooling whenever the user asks to initialize, bootstrap, or scaffold a project.
---

# Python Project Scaffold Skill

Use this skill when the user asks to "scaffold", "bootstrap", "init", or set up a Python project or Makefile.

## Instructions

1. **Makefile**:
   Copy `<skill_dir>/templates/Makefile` to `<repo_root>/Makefile`.
   Ensure target recipes use tabs, not spaces.

2. **Gitignore**:
   If `<repo_root>/.gitignore` does not exist or lacks Python defaults, copy or merge `<skill_dir>/templates/gitignore` into `<repo_root>/.gitignore`.

3. **Project Config (`pyproject.toml`)**:
   If `<repo_root>/pyproject.toml` does not exist, initialize a standard package with:
   ```bash
   uv init --lib
   ```
   Add standard dev tools:
   ```bash
   uv add --dev ruff mypy pytest
   ```

4. **Verify**:
   Run `make sync` and `make check` to ensure the environment is ready.
