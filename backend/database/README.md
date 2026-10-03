# Backend Database

The backend uses SQLAlchemy models and creates the configured database tables during application startup. The development configuration defaults to SQLite at database/vulnity_kp.db.

Set DATABASE_URL in backend/.env to use another SQLAlchemy-supported database. Keep local database files and backups out of version control, and use deployment-specific credentials for shared environments.

See the [backend README](../README.md) for setup instructions.

