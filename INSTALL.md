# How to install

i-have-asd uses the same layout and mechanisms as [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd). Only Claude Code is written out in full here. For the other runtimes the entry points are listed below; follow that project's `INSTALL.md` for the runtime and replace `i-have-adhd` with `i-have-asd` and `ayghri` with `hamidasiblog`.

This is output shaping, not medical advice. See the disclaimer in [README.md](README.md).

## Claude Code

### Install

```bash
claude plugin marketplace add hamidasiblog/i-have-asd
claude plugin install i-have-asd@i-have-asd
```

Restart Claude Code.

### Turn on and off

```text
/i-have-asd          turn on for this session
stop asd mode       turn off for this session ("normal mode" also works)
```

### Always-on (optional)

A `SessionStart` hook loads the full ruleset at the start of every session, with no `/i-have-asd` needed:

```bash
touch ~/.claude/.i-have-asd-always
```

If you use a custom Claude configuration directory, create the flag there instead:

```bash
touch "$CLAUDE_CONFIG_DIR/.i-have-asd-always"
```

Back to on-demand:

```bash
rm ~/.claude/.i-have-asd-always
```

The hook only fires when the flag file exists, so installing the plugin changes nothing by itself. "stop asd mode" still turns it off for the current session.

### Uninstall

```bash
claude plugin uninstall i-have-asd
claude plugin marketplace remove i-have-asd
```

## Other runtimes

| Runtime | Entry point in this repository |
| --- | --- |
| Codex | `.codex-plugin/plugin.json`, `.agents/plugins/marketplace.json`, `hooks/hooks.json` |
| Cursor | `.cursor/skills/i-have-asd/SKILL.md` |
| OpenCode | `.opencode/plugins/i-have-asd.mjs`, `.opencode/command/i-have-asd.md` (flag file: `~/.config/opencode/.i-have-asd-always`) |
| Gemini CLI | `gemini-extension.json`, `GEMINI.md` |
| Kimi Code CLI | `kimi.plugin.json` |
| Qwen Code | `qwen-extension.json` |
| Pi / OMP | `package.json`, `extensions/i-have-asd.ts` (`/i-have-asd [on|off]`, `--asd` flag) |

Only the hook scripts have been run in this repository's tests. The other entry points are adapted from i-have-adhd by renaming and have not been exercised in each runtime.
