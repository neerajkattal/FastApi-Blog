# FastAPI Blog

A full-stack blog platform with server-rendered pages and a JSON API side
by side — user accounts, posts, profile pictures, and a complete
forgot/reset password email flow.

**Live:** [fastapi-blog-stle.onrender.com](https://fastapi-blog-stle.onrender.com/)

## Features

- JWT authentication (`pwdlib`/argon2 password hashing, not bcrypt-only)
- Forgot/reset password over email — a single-use, hashed, time-limited
  reset token, with a deliberately identical response whether or not the
  email exists (no account enumeration)
- Profile picture upload with server-side image validation, resizing, and
  a max-size limit
- Full post CRUD, ownership-checked (a user can only edit/delete their
  own posts) with pagination
- Both a server-rendered UI (Jinja2 templates) and a versioned JSON API
  (`/api/users`, `/api/posts`) sharing the same async SQLAlchemy models
- Custom error pages for both the HTML and API surfaces

## Stack

FastAPI · SQLAlchemy 2.0 (async) · SQLite (aiosqlite) · Jinja2 · PyJWT ·
pwdlib (argon2) · Pillow · aiosmtplib · deployed on Render

## Running locally

```bash
git clone https://github.com/neerajkattal/FastApi-Blog.git
cd FastApi-Blog
pip install -r requirements.txt

# .env (all required except mail_* / frontend_url, which default to
# local-friendly values):
# SECRET_KEY=<a random string>

fastapi dev main.py
# → http://localhost:8000
```

`populate_db.py` seeds the database with a handful of demo users and
posts (placeholder avatars, no real personal data) if you want something
to look at right away.
