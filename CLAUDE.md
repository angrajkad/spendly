# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Setup

```bash
python -m venv venv
source venv/Scripts/activate   # Windows
# source venv/bin/activate     # Unix/macOS
pip install -r requirements.txt
```

## Commands

| Task | Command |
|------|---------|
| Run dev server | `python app.py` (http://localhost:5001, debug mode on) |
| Run tests | `pytest` |
| Run single test | `pytest tests/test_foo.py::test_name -v` |

## Architecture

**Spendly** is a Flask-based personal expense tracker structured as a step-by-step learning project. The backend is largely a scaffold with placeholder routes; students implement the database layer and features incrementally.

### Stack
- **Backend:** Flask 3.1.3, plain `sqlite3` (no ORM), Jinja2 templates
- **Frontend:** Vanilla HTML/CSS/JS — no build step, no framework
- **Testing:** pytest + pytest-flask

### Key files
- `app.py` — single file containing the Flask app and all route definitions
- `database/db.py` — stub for `get_db()`, `init_db()`, and `seed_db()` helpers (not yet implemented)
- `templates/base.html` — base layout with navbar and footer; all other templates extend it
- `static/css/style.css` — all styles using CSS custom properties; includes color palette, typography (DM Serif Display / DM Sans via Google Fonts), and responsive layout

### Routes (current state)
- `GET /` — landing page (fully built)
- `GET /register`, `GET /login` — forms rendered, auth logic not yet implemented
- `GET /terms`, `GET /privacy` — static pages
- `/logout`, `/profile`, `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete` — placeholder strings, to be implemented in later steps

### Planned implementation steps
The project builds up in stages: database layer → user auth (register/login/logout/session) → expense CRUD → filtering/analytics. Each stage maps to explicit step numbers referenced in placeholder route comments.

### CSS conventions
CSS variables are defined on `:root`. Use existing variables (`--color-primary`, `--color-accent`, `--radius-md`, etc.) rather than hardcoding values. Auth forms max-width: 440px; main content max-width: 1200px.
