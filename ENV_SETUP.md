# Environment Configuration Setup

This project uses environment variables to manage sensitive configuration like database credentials and JWT secrets.

## Files Created/Modified

### New Files
- **`.env`** - Contains your actual environment variables (DO NOT commit this file)
- **`.env.example`** - Template file showing what environment variables are needed (safe to commit)

### Modified Files
- **`app/core/config.py`** - Loads environment variables from `.env` using `python-dotenv`
- **`app/core/database.py`** - Now imports `DATABASE_URL` from `config.py`
- **`app/core/auth.py`** - Now imports `SECRET_KEY` and `ALGORITHM` from `config.py`
- **`requirements.txt`** - Added `python-dotenv` dependency
- **`.gitignore`** - Added `.env` file to prevent accidental commits

## Setup Instructions

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure your `.env` file:**
   - Copy `.env.example` to `.env`
   - Update the values with your actual credentials

3. **Run the application:**
   ```bash
   python -m uvicorn app.main:app --reload
   ```

## Environment Variables

The following environment variables are used:

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_URL` | PostgreSQL connection string | `postgresql+psycopg2://postgres:123@localhost:5432/mocksy` |
| `SECRET_KEY` | JWT secret key for token signing | `mysecret` |
| `ALGORITHM` | JWT algorithm to use | `HS256` |
| `DEBUG` | Debug mode (True/False) | `True` |

## Security Notes

⚠️ **Important:**
- Never commit `.env` to git (it's in `.gitignore`)
- Always use `.env.example` as a template for new developers
- Change `SECRET_KEY` to a strong random value in production
- Use strong database passwords in production
- Consider using a secrets management tool (e.g., AWS Secrets Manager, HashiCorp Vault) in production

