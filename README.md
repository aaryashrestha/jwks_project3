Objective
Enhance the JWKS server by encrypting private keys, adding user registration, logging auth requests, and optionally rate-limiting /auth.

Features
AES Encryption: Private keys encrypted using key from NOT_MY_KEY.
User Registration: POST /register with username/email, returns UUIDv4 password, hashed with Argon2.
Auth Logging: Logs IP, timestamp, and user ID in auth_logs.

Database
users table stores users and hashed passwords
auth_logs table records authentication attempts.

Setup
export NOT_MY_KEY="your_secret_key"
pip install -r requirements.txt
python server/jwks_server.py
pytest --cov=server --cov-report=term-missing
