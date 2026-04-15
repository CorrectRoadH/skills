---
name: calibre
description: Convert ebooks between formats (EPUB, MOBI, PDF, AZW3, etc.) using Calibre's ebook-convert CLI. Use when the user wants to convert book files, prepare files for Kindle (.mobi), produce PDFs from ebooks, or batch-convert a folder of books. Triggers on "convert to mobi/pdf/epub", "kindle 格式", "转换电子书", "tomobi", "topdf".
version: 1.1.0
---

# Calibre Ebook Conversion

`ebook-convert` (ships with Calibre) is the atomic command; don't wrap it in a script unless you need something genuinely more than one line. This skill is documentation + a couple of reusable command patterns.

## Prerequisite

```bash
command -v ebook-convert || echo "Install Calibre and make sure ebook-convert is on PATH"
```

If `ebook-convert` isn't on PATH, resolve it per-platform (macOS app bundle, Linux package, Windows install dir) — don't hardcode a symlink path in the skill.

## Core command

```bash
ebook-convert INPUT OUTPUT [options]
```

Format is inferred from the output extension.

```bash
ebook-convert novel.epub novel.mobi         # → Kindle
ebook-convert novel.epub novel.pdf          # → PDF
ebook-convert novel.mobi novel.epub         # → EPUB
ebook-convert novel.epub novel.azw3         # → AZW3
```

## Batch convert

Bash one-liner — parallel, one output per input, same basename:

```bash
for f in *.epub; do ebook-convert "$f" "${f%.*}.mobi" & done; wait
```

Replace `*.epub` and `.mobi` with your source glob and target extension.

## Kindle-tuned conversion

```bash
ebook-convert in.epub out.mobi \
  --output-profile kindle_pw3 \
  --mobi-file-type both \
  --no-inline-toc
```

Other useful flags:
- `--cover path/to/cover.jpg` — override cover image
- `--authors "Name"` / `--title "..."` — set metadata
- `--margin-left/right/top/bottom 20` — for PDF output
- `--pdf-page-numbers` — for PDF output

Full reference: `ebook-convert --help` or `ebook-convert in.epub out.mobi --help` (format-specific options show up after the filenames).
