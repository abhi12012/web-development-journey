<!-- Short, focused guidance for AI coding agents working in this workspace -->
# Copilot instructions for this workspace

Purpose
- Help AI coding agents quickly understand repository structure, where to look for runnable projects, and how to behave when files are missing or folders are empty.

Repo snapshot (discoverable)
- Top-level: [01_Learning](01_Learning), [02_Practice](02_Practice), [03_Projects](03_Projects), [04_Git-GitHub](04_Git-GitHub), [05_Notes](05_Notes), [06_Resources](06_Resources)
- There is an empty `README.md` folder at the repo root.
- Topic folders (e.g. `01_Learning/NodeJS`, `01_Learning/React`) currently contain no project manifests.

Primary agent goals
- Treat this repository as a collection of learning materials and small exercises, not a single monolithic app.
- When asked to modify or run code, first locate a concrete project (presence of `package.json`, `index.html`, `requirements.txt`, or similar). If none found, report that no runnable project exists and ask the user whether to create a starter project.

Search & discovery strategy (explicit steps)
1. Look for project manifests: `package.json`, `pyproject.toml`, `requirements.txt`, `index.html` anywhere under the relevant topic folder.
2. Prefer the nearest manifest when multiple are found (e.g. a `package.json` inside `01_Learning/React/my-app`).
3. If manifests are absent, look for README files or subfolders with code files (`.js`, `.html`, `.css`, `.py`) to infer runnable examples.

Typical run/build commands (use only after confirming a manifest exists)
- Node / React projects with `package.json`: run `npm install` then `npm start` (or `npm run dev` if present). Use `npm test` for any `test` script.
- Static HTML examples: open `index.html` or serve the folder with `npx http-server .` for quick previews.

Project-specific conventions (what's actually present)
- The repository is organized by topic number prefixes (e.g. `01_Learning`) — search under those folders for exercises before proposing cross-repo refactors.
- Do not assume centralized tooling or CI; verify presence of config files (ESLint, Babel, webpack, GitHub Actions) before using them.

When creating changes or new files
- Keep changes local to the topic folder unless the user asks for a global change.
- Add a short `README.md` in any folder where you create a runnable example, including explicit run instructions.

What not to do
- Do not add or run commands that assume monorepo tooling (lerna, turbo) unless such configs are present.
- Do not commit large generated files or node_modules.

Examples (from this workspace)
- Look for runnable code under: [01_Learning/NodeJS](01_Learning/NodeJS), [01_Learning/React](01_Learning/React).
- If asked to implement a NodeJS exercise but `01_Learning/NodeJS` is empty, ask the user whether to scaffold a minimal `package.json` and sample script.

If you need clarification
- Ask the user whether to create starter projects, where to place runnable examples, or whether edits should be contained to a specific topic folder.

Feedback
- After applying edits, request quick confirmation: "Should I scaffold runnable projects in empty topic folders or only edit existing projects?"
