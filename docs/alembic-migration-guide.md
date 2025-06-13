# Alembic Migration Guide for TruCtrl-API

This guide explains how to manage database schema changes for the TruCtrl-API project using Alembic and environment variables from your `.env` file.

## Prerequisites
- Alembic is installed (see `requirements.txt`).
- The `.env` file is configured with your database settings (DB_TYPE, DB_NAME, etc.).

## How Alembic Finds the Database
Alembic is configured to read your `.env` file and construct the database URL from the following variables:
- `DB_TYPE` (e.g., `sqlite`)
- `DB_NAME` (e.g., `tructrl.db`)
- `DB_USER`, `DB_PASSWORD`, `DB_HOST`, `DB_PORT` (for non-SQLite databases)

For SQLite, the URL will look like:
```
sqlite:///tructrl_api/tructrl.db
```

## Common Alembic Commands

### 1. Generate a New Migration
This will create a migration script based on changes in your models:
```pwsh
alembic revision --autogenerate -m "Describe your change here"
```

### 2. Apply Migrations (Upgrade the Database)
This will apply all pending migrations to your database:
```pwsh
alembic upgrade head
```

### 3. Downgrade (Rollback) the Last Migration
```pwsh
alembic downgrade -1
```

### 4. Check Current Migration State
```pwsh
alembic current
```

## Troubleshooting
- If you see errors about the database URL or missing tables, check your `.env` file and ensure all variables are set correctly.
- Alembic will use the database defined by your `.env` file every time you run a migration command.

## More Info
- See [Alembic documentation](https://alembic.sqlalchemy.org/en/latest/) for advanced usage.
- For project-specific questions, see the `alembic/env.py` file for how environment variables are loaded.
