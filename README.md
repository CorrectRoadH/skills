# Skills

> [English version → README.en.md](./README.en.md)

Skill 仓库。每个子目录是一个独立的 skill，通过其 `SKILL.md` 自动触发。

## 包含的 skills

| 目录 | 作用 | 触发场景 |
|------|------|----------|
| [`neodb/`](./neodb) | NeoDB API 集成，搜索书影音游戏等媒体条目 | 查询书/电影/音乐元数据、对接 neodb.social |
| [`calibre/`](./calibre) | 封装 Calibre `ebook-convert`，一键转 mobi / pdf / epub | 电子书格式转换、Kindle 推送准备 |
| [`startup-mirror/`](./startup-mirror) | 基于 Loot Drop 7 大失败反模式的创业点子挑战 | 新点子评审、创业前 pre-mortem、创业模式挑战 |

## 安装方式

```bash
npx skills add CorrectRoadH/skills
```

## 依赖

- `calibre` 需要本机安装 Calibre。
- `neodb` 直接用 `curl` 调公共 API，无需鉴权。
- `startup-mirror` 无外部依赖，纯 prompt 方法论。

## 目录结构

```
skills/
├── README.md                 # 本文件（中文）
├── README.en.md              # English version
├── neodb/SKILL.md
├── calibre/SKILL.md
└── startup-mirror/SKILL.md
```

每个 skill 都是纯文档 —— 不打包脚本。底层工具（`curl`、`ebook-convert`、prompt）已经在用户机器上；skill 只教 agent 怎么用它们，而不是再包一层。

## Credits

- `startup-mirror` 方法论来自 [Loot Drop](https://www.loot-drop.io)。
