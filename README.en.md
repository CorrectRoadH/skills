# Skills

> [中文版 → README.md](./README.md)

Skill repository. Each subdirectory is a self-contained skill, auto-triggered via its `SKILL.md` frontmatter.

## Included skills

| Directory | Purpose | Triggers |
|-----------|---------|----------|
| [`neodb/`](./neodb) | NeoDB API integration — search books, films, music, games, TV, podcasts | Media metadata lookups, neodb.social integrations |
| [`calibre/`](./calibre) | Wrapper around Calibre's `ebook-convert` — quick mobi / pdf / epub conversion | Ebook format conversion, Kindle prep |
| [`startup-mirror/`](./startup-mirror) | Startup-idea stress test using Loot Drop's 7 failure antipatterns | New-venture pre-mortems, founder self-assessment, "challenge my idea" |

## Install

```bash
npx skills add CorrectRoadH/skills
```

## Requirements

- `calibre` requires Calibre installed locally.
- `neodb` uses public endpoints via plain `curl` — no auth, no extra deps.
- `startup-mirror` has no external deps — pure prompt methodology.

## Layout

```
skills/
├── README.md                 # Chinese version
├── README.en.md              # this file
├── neodb/SKILL.md
├── calibre/SKILL.md
└── startup-mirror/SKILL.md
```

Each skill is pure documentation — no bundled scripts. The underlying tools (`curl`, `ebook-convert`, prompts) are already on the user's system; the skills teach the agent how to drive them, rather than re-wrap them.

## Credits

- `startup-mirror` methodology from [Loot Drop](https://www.loot-drop.io).
