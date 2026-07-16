# skills-library

A central library of Claude Code skills, kept here as the single source of
truth and copied into individual project repos' `.claude/skills/` as
needed.

## Why this exists

Installing plugins normally goes through Claude Code's `/plugin marketplace
add` / `/plugin install` commands, but those only work in a local CLI
session. On the hosted web/mobile app there's no local machine to clone
marketplace repos onto, so `/plugin` isn't available there. Keeping a
plain-file copy of each skill here, and copying the relevant folders into a
project's `.claude/skills/`, works everywhere `/plugin` doesn't — at the
cost of each project carrying its own copy instead of one shared install.

## Layout

- **`skills/`** — upstream sources, one subfolder per origin:
  - `public/` — Anthropic's built-in public skills (docx, pdf, pptx, xlsx, frontend-design, file-reading, pdf-reading, product-self-knowledge)
  - `examples/` — Anthropic's example skills (mcp-builder, skill-creator, doc-coauthoring, canvas-design, theme-factory, etc.)
  - `superpowers/` — from [obra/superpowers](https://github.com/obra/superpowers) (Jesse Vincent) — TDD, systematic debugging, brainstorming, code review, and other development-methodology skills
  - `impeccable/` — from [pbakaus/impeccable](https://github.com/pbakaus/impeccable) (Paul Bakaus) — design-language/polish skill
  - `andrej-karpathy-skills/` — from [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills)
  - `session-start-hook/` — from this environment's own Claude config

- **`.claude/skills/`** — every skill above, flattened to one directory per
  skill (`.claude/skills/<name>/SKILL.md`). This is the layout Claude Code
  auto-discovers, so opening this repo (or copying this folder into another
  repo) makes each skill callable directly as `/<skill-name>`.

## Using a skill in another project

Copy the folder(s) you want from `.claude/skills/` into the target repo's
own `.claude/skills/`, commit, and push. Example:

```bash
cp -r .claude/skills/systematic-debugging /path/to/other-repo/.claude/skills/
```

Or copy the whole directory to bring in everything at once:

```bash
cp -r .claude/skills /path/to/other-repo/.claude/
```

If you do have local CLI access, installing the original plugin via
`/plugin marketplace add` is preferable to copying — it gets you updates and
proper marketplace registration instead of a static snapshot.
