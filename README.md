# herdr-new-workspace

A [herdr](https://herdr.dev) plugin: a popup for picking a project directory and
an agent before creating a workspace.

1. **Pick a project**: a fuzzy list of ★ pinned projects, ● directories of open
   panes, and ◷ ones you've used before, with a git/file preview. Type a path
   starting with `~/`, `/` or `./` to browse anywhere; `tab` goes into a folder,
   and a path that doesn't exist yet is offered to be created.
2. **Pick an agent** to start in the new workspace (claude, copilot, codex,
   gemini, opencode, amp, cursor-agent, whichever are installed) or none. Your
   last choice is preselected.
3. **Confirm the label** (defaults to the directory name).

| Key      | In the project list        |
| -------- | -------------------------- |
| `enter`  | select                     |
| `tab`    | browse into the folder     |
| `ctrl-p` | pin / unpin the project    |
| `ctrl-e` | edit the pinned list       |
| `esc`    | cancel                     |

## Install

Requires herdr 0.9.5+, `zsh`, `git`, `jq`, and `fzf` 0.60+.

```sh
herdr plugin install bethanyj28/herdr-new-workspace
```

Then bind a key in `~/.config/herdr/config.toml`. To replace the built-in
new-workspace key:

```toml
[keys]
new_workspace = "prefix+alt+n"  # move the built-in out of the way

[[keys.command]]
key = "prefix+shift+n"
type = "plugin_action"
command = "bethanyj28.new-workspace.open"
description = "new workspace"
```

Pinned projects live in `projects` in the plugin's config directory
(`herdr plugin config-dir bethanyj28.new-workspace`), one directory per line.
