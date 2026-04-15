# Skills

Claude Code skills 仓库。每个子目录是一个独立的 skill，通过其 `SKILL.md` 被 Claude 自动触发。

Claude Code skills. Each subdirectory is a self-contained skill; Claude triggers it automatically via the `SKILL.md` frontmatter.

---

## 中文

### 包含的 skills

| 目录 | 作用 | 触发场景 |
|------|------|----------|
| [`neodb/`](./neodb) | NeoDB API 集成，搜索书影音游戏等媒体条目 | 查询书/电影/音乐元数据、对接 neodb.social |
| [`calibre/`](./calibre) | 封装 Calibre `ebook-convert`，一键转 mobi / pdf / epub | 电子书格式转换、Kindle 推送准备 |
| [`startup-mirror/`](./startup-mirror) | 基于 Loot Drop 7 大失败反模式的创业点子挑战 | 新点子评审、创业前 pre-mortem、创业模式挑战 |

### 安装方式

```bash
npx skills add neodb
npx skills add calibre
npx skills add startup-mirror
```

### 依赖

- `calibre` 需要本机安装 Calibre，并让 `ebook-convert` 在 PATH 中（macOS：`ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin/ebook-convert`）。
- `neodb` 直接用 `curl` 调公共 API，无需鉴权。
- `startup-mirror` 无外部依赖，纯 prompt 方法论。

---

## English

### Included skills

| Directory | Purpose | Triggers |
|-----------|---------|----------|
| [`neodb/`](./neodb) | NeoDB API integration — search books, films, music, games, TV, podcasts | Media metadata lookups, neodb.social integrations |
| [`calibre/`](./calibre) | Wrapper around Calibre's `ebook-convert` — quick mobi / pdf / epub conversion | Ebook format conversion, Kindle prep |
| [`startup-mirror/`](./startup-mirror) | Startup-idea stress test using Loot Drop's 7 failure antipatterns | New-venture pre-mortems, founder self-assessment, "challenge my idea" |

### Install

```bash
npx skills add neodb
npx skills add calibre
npx skills add startup-mirror
```

### Requirements

- `calibre` requires Calibre installed locally with `ebook-convert` on PATH (macOS: `ln -s /Applications/calibre.app/Contents/MacOS/ebook-convert /usr/local/bin/ebook-convert`).
- `neodb` uses public endpoints via plain `curl` — no auth, no extra deps.
- `startup-mirror` has no external deps — pure prompt methodology.

---

## Layout

```
skills/
├── README.md                 # this file
├── neodb/SKILL.md
├── calibre/SKILL.md
└── startup-mirror/SKILL.md
```

Each skill is pure documentation — no bundled scripts. The underlying tools (`curl`, `ebook-convert`, prompts) are already on the user's system; the skills teach Claude how to drive them, rather than re-wrap them.

## Credits

- `neodb` methodology from `~/.openclaw/skills/neodb`.
- `calibre` references the user's existing `~/Script/tomobi.sh` and `~/Script/topdf.sh`.
- `startup-mirror` methodology from [Loot Drop](https://www.loot-drop.io).
