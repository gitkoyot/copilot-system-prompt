# Copilot Engineering Workflow Instructions

`copilot-instructions.md` is a generic, verification-first engineering system prompt
for GitHub Copilot (or any coding agent), distilled from the Claude Code workflow
publicly shared by Boris Cherny, creator of Claude Code at Anthropic.

## How it was created

1. **Research** — gathered Boris Cherny's Claude Code tips from his X threads and
   community collections (sources below).
2. **Generalize** — reworded Claude-Code-specific mechanics into tool-agnostic concepts
   (plan mode -> "plan first", subagents -> "decompose large work", `CLAUDE.md` ->
   "conventions file / lessons log") and dropped non-portable ones (worktrees, hooks).
3. **Compile** — wrote the result as a concise, scannable prompt, framed for
   `.github/copilot-instructions.md`.

## Install it system-wide

The prompt is not tied to one repo. Pick the scope you want:

- **Every repo in your IDE (VS Code).** Run **Chat: New Instructions File** from the
  Command Palette and save it to your **User profile** (not the workspace). User-profile
  instructions files load across all workspaces. Add this frontmatter so it applies to
  every file and chat request:

  ```
  ---
  applyTo: '**'
  ---
  ```

- **Every conversation on github.com.** Open Copilot Chat, click your profile picture
  (bottom-left) -> **Personal instructions**, paste the prompt body, and Save. This
  applies to all Copilot Chat conversations on the GitHub website.

- **A single repository.** Commit `copilot-instructions.md` to `.github/copilot-instructions.md`
  at the repo root; Copilot applies it automatically for that repo. (VS Code also
  auto-detects `AGENTS.md` and `CLAUDE.md` per workspace.)

- **A whole organization.** Copilot Business/Enterprise admins can set organization
  custom instructions that apply across every repo in the org.

When several apply, precedence is: personal (highest) -> repository -> organization.

## Sources

- [How Boris Uses Claude Code](https://howborisusesclaudecode.com/) — 89 collected tips
- [@bcherny thread, Jan 2, 2026](https://x.com/bcherny/status/2007179832300581177)
- [@bcherny thread, Jan 31, 2026](https://x.com/bcherny/status/2017742741636321619)
- [@_catwu post, Apr 16, 2026](https://x.com/_catwu/status/2044808533905178822)
- [boris-team-tips.md gist](https://gist.github.com/joyrexus/e20ead11b3df4de46ab32b4a7269abe0)

Generated with Claude in Cowork mode, 2026-05-24, as a generalized synthesis of
Boris Cherny's publicly documented practices.
