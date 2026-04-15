# Calibre Skill — Convert Ebooks to EPUB / MOBI / PDF / AZW3 via `ebook-convert`

An AI agent skill that wraps [Calibre](https://calibre-ebook.com)'s `ebook-convert` CLI so an agent can convert ebook files between formats — EPUB, MOBI, PDF, AZW3, KFX input, FB2, and more — including Kindle-tuned conversions and parallel batch jobs on a folder of books.

No scripts bundled. No external shell dependencies. The skill is pure documentation + command patterns that call `ebook-convert` directly.

## What it does

- **Single-file conversion** — any format Calibre supports, inferred from output extension
- **Batch conversion** — parallel one-liner over a glob (e.g. every `.epub` in a folder → `.mobi`)
- **Kindle-tuned output** — `--output-profile kindle_pw3`, `--mobi-file-type both`, cover overrides, metadata injection
- **PDF tuning** — margins, page numbers, paper size
- **Format-specific help** — how to discover flags via `ebook-convert in.epub out.mobi --help`

## When the skill triggers

- "convert to mobi / pdf / epub"
- "kindle 格式", "转换电子书"
- "tomobi", "topdf"
- Preparing ebooks for Kindle, reMarkable, or Kobo
- Batch-converting a folder of books

## Install

```bash
npx skills add CorrectRoadH/skills
```

## Dependencies

- [Calibre](https://calibre-ebook.com) installed locally with `ebook-convert` on PATH.

Verify:
```bash
command -v ebook-convert
```

That's the only requirement — no wrapper scripts, no symlinks hardcoded into the skill.

## Keywords

Calibre · ebook-convert · EPUB to MOBI · EPUB to PDF · MOBI to EPUB · AZW3 converter · Kindle format · Kindle Paperwhite · batch ebook conversion · CLI ebook converter · AI agent skill · Claude skill
