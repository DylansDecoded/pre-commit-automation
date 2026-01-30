# Install pre-commit python package
```
bash
pipenv install 
```

# Install pre-commit as a dev dependency
```pipenv install --dev pre-commit```


# Remove cached hook environments
pre-commit clean

# Reinstall fresh
pre-commit install --install-hooks
```

## Lenient Rules Philosophy

This setup intentionally uses **lenient rules** to focus on major errors only:

### Python (Ruff)
- ✅ Catches: Undefined variables, syntax errors, unused imports
- ❌ Ignores: Line length strictness, naming conventions, docstring requirements

### SQL (SQLFluff)
- ✅ Catches: Inconsistent indentation, trailing whitespace, comma placement
- ❌ Ignores: Capitalization, strict naming conventions, complex layout rules

### YAML
- ✅ Catches: Invalid YAML syntax, inconsistent indentation
- ❌ Ignores: Key ordering, quote style preferences

**Future**: Rules can be gradually strengthened as the team adapts.

## File Structure
```
osdi-backend-repo/
├── .pre-commit-config.yaml   # Pre-commit hook configuration
├── ruff.toml                 # Python linting/formatting rules
├── .sqlfluff                 # SQL formatting rules (Databricks)
├── Pipfile                   # Python dependencies
├── Pipfile.lock              # Locked dependency versions
├── bogiefile                 # YAML-formatted config (no extension)
└── README.md                 # This file
```

#!/usr/bin/env bash
# Installed by pre-commit

# This hook is invoked by git-commit
if [ -x "$HOME/.cache/pre-commit/..." ]; then
    exec /path/to/pipenv/run pre-commit run --hook-stage commit
fi


