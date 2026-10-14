# .pi

My personal [Pi](https://github.com/badlogic/pi-mono) configuration. Skills are managed with GNU Stow; upstream skill repos are tracked as submodules.

To set it up, activate all distinct skills from the submodules:

```sh
git clone --recurse-submodules <repo-url> ~/.pi
cd ~/.pi
for dir in stow/*/; do
  package=${dir#stow/}
  stow --dir=stow --target=. "${package%/}"
done
```

This activates all **173 distinct submodule skills** by default. It is useful for discovery, but probably too much for daily workloads: Pi loads every active skill's name and description into its prompt. Deactivate skills you do not use with Stow, and activate them again when needed. Local skills live directly under `agent/skills/` and are not managed by Stow. If you cloned without submodules, run `git submodule update --init --recursive` first.

Three upstream entries duplicate skill names, which Pi cannot load twice: this setup uses Matt Pocock's `code-review` and `retro`, and OpenAI's curated `openai-docs`. The alternative versions remain in their submodules.

For example:

```sh
# Activate
stow --dir=stow --target=. mattpocock-code-review

# Deactivate (removes only the Pi-facing link; keeps the submodule source)
stow --dir=stow --target=. --delete mattpocock-code-review
```

Package names use `<source>-<skill>`, such as `phuryn-outcome-roadmap` or `openai-security-threat-model`. Replace the example package name with the skill you want to manage.
