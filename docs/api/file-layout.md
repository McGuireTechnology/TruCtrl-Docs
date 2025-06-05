auth/models.py

Pydantic models (Token, TokenData, User, etc.)
Any ORM/database models for users or sessions (if/when you add persistent storage)

auth/routes.py

All authentication-related endpoints (login, refresh, logout, session management, etc.)
auth/schemes.py (optional, for larger projects)

OAuth2PasswordBearer and other security schemes

auth/utils.py

Helper functions: token creation, password hashing, token validation, etc.

auth/dependencies.py

Dependency functions for FastAPI (e.g., get_current_user, get_current_active_user)

auth/constants.py (optional)

Any constants (token types, error messages, etc.)
auth/db.py (if you add persistent storage)

Database access functions for users, sessions, or tokens