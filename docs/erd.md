# Poverty App — Entity Relationship Diagram (ERD)

This file contains the Mermaid source for the project database ERD.

```mermaid
erDiagram
  USERS {
    TEXT id PK
    TEXT username UNIQUE
    TEXT password_hash
    TEXT email
    TEXT role
    TEXT profile_pic_path
    TEXT created_at
  }

  PREDICTIONS {
    TEXT id PK
    TEXT user_id FK
    TEXT username
    TEXT timestamp
    TEXT class_name
    REAL confidence
    TEXT features_json
    TEXT recommendations_json
    TEXT dataset_name
  }

  ADMIN_LOGS {
    TEXT id PK
    TEXT admin_id FK
    TEXT action
    TEXT details
    TEXT timestamp
  }

  USER_ACTIONS {
    TEXT id PK
    TEXT user_id FK
    TEXT username
    TEXT action
    TEXT details
    TEXT timestamp
  }

  USERS ||--o{ PREDICTIONS : "creates"
  USERS ||--o{ USER_ACTIONS : "performs"
  USERS ||--o{ ADMIN_LOGS : "administers"
```

Notes:
- The ERD is based on `app.py` table definitions created in `init_db()`.
- `PREDICTIONS`, `USER_ACTIONS`, and `ADMIN_LOGS` all relate back to `USERS` via user identifiers.
