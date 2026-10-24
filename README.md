# Claude Code template

A starter repo for new projects worked on with Claude Code. It holds two files to copy into a new repository:

- **`CLAUDE.md`**: the instructions Claude Code reads at the start of every session. It sets out how I work across all projects: guardrails (no commits to `main`, no new dependencies without asking), Git workflow, Conventional Commits, testing expectations, progress reporting, secrets handling, and default tech choices (TypeScript with pnpm, Python with uv and Ruff).
- **`.gitignore`**: a general-purpose ignore list covering secrets (`.env`), OS and editor files, Node/TypeScript, Python, test coverage and logs.

## Using it

1. Create a new repo from this template, or copy both files into an existing one.
2. Fill in the sections of `CLAUDE.md` marked `<!-- FILL IN PER PROJECT -->`, starting with the Project Overview.
3. Add an `example.env` alongside any `.env` file, as the Security & Secrets section asks.
