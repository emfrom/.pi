---
name: manage-pi-skills
description: Manage this Pi configuration's skills, skill sources, updates, and setup.
disable-model-invocation: true
---

# Manage Pi skills

Use this skill when the user invokes `/manage-pi-skills` to set up or explain this repository, activate or deactivate skills, switch a submodule between a fork and its upstream, or merge upstream changes into tracked forks.

## Work from current evidence

Treat the repository as the source of truth, not this document's assumptions. Start by locating its root and inspecting the current Git status, submodule configuration and status, skill packages, active Pi skill links, and relevant remotes. Read the relevant files and query hosting metadata when it can establish fork relationships or default branches. Derive names, counts, paths, source relationships, and available operations from that evidence each time; do not maintain a copied inventory or assume every source follows the same layout.

Preserve unrelated user changes in both the parent repository and submodules. Distinguish a package's source from its Pi-facing activation link, a submodule URL from its pinned commit, and a fork's remote from its upstream. Before changing anything, establish which of these the user's request concerns. If the intended skill, set, repository, or source is ambiguous, explain the evidence and ask only for the missing choice.

## Handle the requested operation

- **Setup or help:** Explain the current repository from its files and live state. For setup, inspect what is already initialized and activated, identify any missing prerequisites, and complete only the setup the user wants. Give commands only for steps that genuinely require human intervention.
- **Activate or deactivate:** Resolve the requested skill or skillset against the current packages and sources. If the request describes a broad set rather than naming packages, infer a reasonable set from the user's stated goal and the live inventory; summarize that selection before applying it when the scope is consequential. Preview the link changes, then use the repository's actual package manager and layout. Verify each requested skill resolves to the intended source. Deactivation removes only its Pi-facing link; preserve its package and source.
- **Switch a submodule source:** Determine whether the user means changing the submodule's configured URL, changing the fork's fetch/push remotes, or changing the pinned source commit. Verify the desired fork/upstream relationship using current metadata and repository configuration. Before switching the configured URL or gitlink, ensure the pinned commit is available from the destination and identify any fork-only commits that would be lost or become unreachable. Preserve them; if the choice cannot be made safely from evidence, describe the tradeoff and ask.
- **Update forks from upstream:** Discover which tracked submodules are actually forks, identify each upstream and its current default branch, and compare their histories with the tracked fork branches. Inspect worktrees before updating. Merge upstream commits without rewriting fork history; do not force-push. Push only to the verified user's fork when the request clearly asks to update those remote forks. Update the parent repository's submodule pointers to the resulting commits and report those changes. Stop on conflicts, dirty worktrees, unexpected ownership, or unclear branch relationships rather than guessing.

Adapt commands to the state discovered in this run; avoid scripts or fixed package/repository lists that bake in today's inventory. If a task spans several repositories, make a concise plan, execute independent safe steps, and verify each repository separately.

## Changes and completion

Make the smallest change that satisfies the request. Never discard or overwrite unrequested changes. Do not commit or push the parent configuration repository unless the user explicitly asks. Before any commit, follow the repository's secret/privacy review instructions. Never force-push or publish a private source. Finish by verifying the active links, submodule URLs and commits, and repository status relevant to the operation; report what changed, what remains, and any blockers.
