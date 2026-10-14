# .pi

My personal [Pi](https://github.com/badlogic/pi-mono) configuration. Skills are managed with GNU Stow; upstream skill repos are tracked as submodules.

To set it up:

```sh
git clone --recurse-submodules <repo-url> ~/.pi
cd ~/.pi
stow --dir=stow --target=. mattpocock-skills
```

If you already cloned it without submodules, run `git submodule update --init --recursive` first. The `agent/skills/` links are tracked in this repo; Stow connects them to the skills in the submodule.
