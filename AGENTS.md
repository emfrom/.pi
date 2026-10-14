# Repository instructions

## Skill activation and deactivation

When the user's intent is to activate or deactivate an upstream skill, change its GNU Stow link; keep the skill source in its submodule. Each upstream skill has an individual package under `stow/`, named `<source>-<skill>`.

- Activate: `stow --dir=stow --target=. <package>`
- Deactivate: `stow --dir=stow --target=. --delete <package>`

Find the package under `stow/` if the name is unknown. Verify activation by checking that `agent/skills/<skill>/SKILL.md` resolves into the intended submodule. Deactivation removes only the Pi-facing link, not the package or submodule source. Local skills stored directly under `agent/skills/` are not Stow-managed.

## Secret and privacy review before commits

Before committing any files, verify that the complete staged change is safe to publish:

1. Inspect every staged file and the full staged diff, including binary files and renames. Do not assume `.gitignore` protects files that are already tracked or staged.
2. Check for credentials and sensitive data: API keys, tokens, passwords, private keys, `.env` contents, personal or confidential records, private URLs, machine-specific paths, and logs or databases that may contain prompts or user data.
3. Use available secret-scanning tools when practical, and manually review their findings. Treat a clean scanner result as a useful check, not proof that content is safe.
4. If a file or value may be sensitive and you cannot establish that it is safe, exclude it from the commit and report the concern. Never print secret values into terminal output, reports, or commit messages.
5. Re-check the staged diff after any changes. Commit only when every staged file has been reviewed and no secret or unintended private information is being disclosed.
