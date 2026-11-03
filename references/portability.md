# Portability

This skill follows the Agent Skills layout: `SKILL.md` plus optional `references/`. Keep instructions in Markdown. Do not add OS-specific scripts unless the same behavior is also provided for Windows, macOS, and Linux.

## Agents

- Pi: `~/.pi/agent/skills/ui-reskin/`
- Claude Code and compatible clients: `~/.claude/skills/ui-reskin/` or the project `.claude/skills/ui-reskin/`
- Codex and other clients that read `~/.agents/skills/`: `~/.agents/skills/ui-reskin/`
- Grok, DeepSeek, or another client: use its documented skills directory. If it accepts the Agent Skills standard, point it at this directory without rewriting the skill.

`~` means the user home directory on every system. Project-scoped copies belong in the project skill directory, not in the source tree being restyled.

## Tools

- Filesystem and editing: use the tools exposed by the current agent.
- Shell: use POSIX syntax by default. Use PowerShell syntax only when the current shell is PowerShell.
- Git: require a working `git` command. Never embed a machine-specific Git path in this skill.
- Browser: use an installed browser only to render an HTML prototype. If no browser exists, read the prototype source and state that it was not visually rendered.
- Build tools: use the project’s existing command, such as Gradle, npm, Cargo, or Xcode. Do not require one build tool globally.

## Source types

Android/Compose paths in `source-map.md` are examples for Vela Browser. For iOS, web, Windows, macOS, Linux, Flutter, or another stack, map the equivalent theme, components, navigation, assets, and state files before editing. The behavior boundary is the same.

## Git identity

Do not infer an author from the operating system or from another contributor. If commit identity is absent, ask the user. Never amend or force-push a published commit unless the user explicitly requests it.
