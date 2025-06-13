# CRUD Import and Endpoint Order Convention

To ensure consistency and maintainability across the TruCtrl-API codebase, all modules that implement CRUD (Create, Read, Update, Delete) logic should follow a standardized order for both import statements and endpoint/function definitions.

## Required Order

The correct order for CRUD-related imports and endpoint definitions is:

1. **list**
2. **create**
3. **upsert**
4. **read**
5. **update**
6. **delete**

This order should be followed in:
- Import statements (e.g., `from .crud import list, create, upsert, read, update, delete`)
- Endpoint or function definitions in route files (e.g., `def list_users`, `def create_user`, etc.)

## Example

```python
# Package Imports
from .crud import list, create, upsert, read, update, delete

# --- CRUD Endpoints ---

# List
@router.get("")
def list_items(...):
    ...

# Create
@router.post("")
def create_item(...):
    ...

# Upsert
@router.post("/upsert")
def upsert_item(...):
    ...

# Read
@router.get("/{id}")
def get_item(...):
    ...

# Update
@router.put("/{id}")
def update_item(...):
    ...

# Delete
@router.delete("/{id}")
def delete_item(...):
    ...
```

## Rationale

- **Predictability:** Developers can quickly find and understand CRUD logic in any module.
- **Consistency:** Reduces merge conflicts and onboarding time for new contributors.
- **Documentation:** This convention is referenced in code comments and should be followed in all relevant files.

## Applicability

This convention applies to all files in the project that:
- Import CRUD functions from a local `crud.py` module
- Define CRUD endpoints in FastAPI route files

For more information, see the [Import Style Guide](import-style-guide.md).
