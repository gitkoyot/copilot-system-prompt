# Copilot Engineering Workflow Instructions

A set of verification-first engineering system prompts for GitHub Copilot (or any
coding agent). There are three variants — pick one and install it; they are
alternatives, not layers to stack.

## The files

- **`copilot-instructions.md`** — the base prompt: a generic, tool-agnostic
  engineering workflow distilled from the Claude Code workflow publicly shared by
  Boris Cherny, creator of Claude Code at Anthropic.
- **`copilot-instructions-with-caveman.md`** — Part 1 is the base engineering
  workflow; Part 2 bundles the open-source Caveman Mode skill, an ultra-compressed
  communication style.
- **`copilot-instructions-boris-karpathy-caveman.md`** — Part 1 merges the Boris
  Cherny workflow with Andrej Karpathy's behavioral guidelines into one
  deduplicated set of rules; Part 2 is the always-on Caveman Mode skill. Compared
  to the other two variants, this one is more cautious: it asks when something is
  genuinely unclear instead of always proceeding on assumptions.

Maintenance note: Part 1 of `copilot-instructions-with-caveman.md` is a verbatim
copy of `copilot-instructions.md` — any edit to one must be mirrored in the other.

The guidelines are working if: fewer unnecessary changes in diffs, fewer rewrites
due to overcomplication, and clarifying questions come before implementation rather
than after mistakes.

## How it was created

1. **Research** — gathered Boris Cherny's Claude Code tips from his X threads and
   community collections (sources below).
2. **Generalize** — reworded Claude-Code-specific mechanics into tool-agnostic
   concepts (plan mode -> "plan first", subagents -> "decompose large work",
   `CLAUDE.md` -> "conventions file / lessons log") and dropped non-portable ones
   (worktrees, hooks).
3. **Compile** — wrote the result as a concise, scannable prompt, framed for
   `.github/copilot-instructions.md`.
4. **Extend** — bundled the open-source `caveman` skill, and merged in Andrej
   Karpathy's `CLAUDE.md` behavioral guidelines, to produce the two later variants.

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

- **A single repository.** Commit your chosen file to `.github/copilot-instructions.md`
  at the repo root; Copilot applies it automatically for that repo. (VS Code also
  auto-detects `AGENTS.md` and `CLAUDE.md` per workspace.)

- **A whole organization.** Copilot Business/Enterprise admins can set organization
  custom instructions that apply across every repo in the org.

When several apply, precedence is: personal (highest) -> repository -> organization.

## Sources

Engineering workflow (Boris Cherny):

- [How Boris Uses Claude Code](https://howborisusesclaudecode.com/) — 89 collected tips
- [@bcherny thread, Jan 2, 2026](https://x.com/bcherny/status/2007179832300581177)
- [@bcherny thread, Jan 31, 2026](https://x.com/bcherny/status/2017742741636321619)
- [@_catwu post, Apr 16, 2026](https://x.com/_catwu/status/2044808533905178822)
- [boris-team-tips.md gist](https://gist.github.com/joyrexus/e20ead11b3df4de46ab32b4a7269abe0)

Bundled / merged content:

- [caveman skill — SKILL.md](https://github.com/JuliusBrussee/caveman/blob/main/skills/caveman/SKILL.md) (JuliusBrussee/caveman)
- [Andrej Karpathy CLAUDE.md](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md) (multica-ai/andrej-karpathy-skills)

Generated with Claude in Cowork mode, 2026-05-24. The Boris Cherny workflow is a
generalized synthesis of his publicly documented practices; the caveman skill and
Karpathy guidelines are reproduced from their open-source originals.
