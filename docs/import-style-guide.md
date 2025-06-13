# Python Import Template and Classification Guide

This document describes the recommended import section template for Python files in this project, and how to determine whether an import is a Standard Library, Third-Party, Project, or Module import.

---

## Import Section Template

```python
# --- Imports ---

# Standard Imports
from typing import Optional
import os
import sys
# ...other standard library imports...

# Third-Party Imports
from fastapi import APIRouter
from sqlmodel import SQLModel, Field
import ulid
# ...other pip-installed packages...

# Project Imports
from ..database import get_session
# ...imports from other top-level project packages...

# Package Imports
from .models import User
from .crud import create, read, update, delete
# ...imports from sibling files in the same package...
```

---

## How to Classify Imports

### 1. Standard Imports
- **Definition:** Modules that are part of the Python Standard Library.
- **How to Identify:**
  - You do **not** need to install them with `pip`.
  - They are documented in the [Python Standard Library documentation](https://docs.python.org/3/library/).
  - Examples: `os`, `sys`, `datetime`, `typing`, `json`, `re`, `math`, `pathlib`, `itertools`.

### 2. Third-Party Imports
- **Definition:** Modules that are not included with Python by default and must be installed (usually via `pip`).
- **How to Identify:**
  - You (or your requirements.txt) must install them with `pip` or another package manager.
  - If you try to import them in a fresh Python environment and get an ImportError, they are third-party.
  - Examples: `fastapi`, `sqlmodel`, `ulid`, `pydantic`, `requests`, `numpy`, `pandas`.

### 3. Project Imports
- **Definition:** Imports from other top-level packages or modules within your own project (not the current package).
- **How to Identify:**
  - They use relative imports with one or more dots (e.g., `from ..database import get_session`).
  - They refer to code in other directories at the same or higher level in your project structure.

### 4. Package Imports
- **Definition:** Imports from sibling files/modules within the same package/directory.
- **How to Identify:**
  - They use a single dot for relative import (e.g., `from .models import User`).
  - They refer to code in the same directory as the current file.

---

## Example

```python
# --- Imports ---

# Standard Imports
from typing import Optional
import os

# Third-Party Imports
from fastapi import APIRouter
from sqlmodel import SQLModel, Field
import ulid

# Project Imports
from ..database import get_session

# Module Imports
from .models import User
from .crud import create, read, update, delete
```

---

## Tips
- If you are unsure, check the [Python Standard Library documentation](https://docs.python.org/3/library/).
- If you had to install it with `pip`, it is third-party.
- Use this template for all new and existing Python files for consistency.
