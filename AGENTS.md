# Repository Guidelines

## Project Structure & Module Organization
- `l01_hello.py`: simple greeting script; use as template for small runnable examples.
- `doc/`: Markdown lessons (`l01_python_init.md`, `l02_jupyther.md`, etc.) that explain Python basics; keep new lessons numbered consistently.
- `l02_jupyter.ipynb`: notebook for interactive walkthroughs; prefer notebooks only when narrative output is needed.
- `venv/`: local virtual environment; recreate locally and avoid checking it in.

## Build, Test, and Development Commands
- Create environment: `python3 -m venv venv && source venv/bin/activate`.
- Install or refresh dependencies (add `requirements.txt` if missing): `pip install -r requirements.txt`.
- Run scripts: `python3 l01_hello.py` (extend with your own module names as needed).
- Work with notebooks: `jupyter notebook l02_jupyter.ipynb` or `jupyter lab`.

## Coding Style & Naming Conventions
- Target Python 3; use 4-space indentation and keep lines reasonably short (~100 chars).
- Format with Black and enable `Python` + `Pylance` in VS Code (as suggested in docs); run `black .` before sharing changes.
- Module files follow the existing `lNN_topic.py` pattern; functions and variables use `snake_case`, classes use `CamelCase`.
- Prefer small, single-purpose functions and include brief docstrings for educational examples.

## Testing Guidelines
- Use `pytest` for new tests; place them under `tests/` mirroring source names and use `test_*.py` files.
- Keep tests fast and isolated; prefer pure functions over I/O-heavy logic.
- If coverage matters for a change, run `pytest --maxfail=1 --disable-warnings -q` and note any gaps.

## Commit & Pull Request Guidelines
- Write clear commit messages; a short present-tense summary like `feat: add list basics lesson` works well.
- PRs should explain what changed, why, and how to verify (commands or screenshots for notebooks if relevant).
- Link related issues or tasks and call out any follow-up work.

## Security & Configuration Tips
- Do not commit secrets or `.env` files; prefer environment variables or `.env.example` templates.
- Keep `venv/` and other local artifacts out of version control; add ignores if the project is git-initialized later.
