# NeoDB Skill — Search Books, Movies, Music, Games & Podcasts via NeoDB API

An AI agent skill for querying [NeoDB](https://neodb.social)'s public API — search and fetch metadata for books, movies, TV shows, music albums, video games, podcasts, and live performances. Zero-auth search, optional token-based shelf management.

[neodb.social](https://neodb.social) is a federated, open-source media cataloging platform (the ActivityPub-based alternative to Douban / Goodreads / Letterboxd). This skill teaches an AI agent how to drive the API without wrapping it in bespoke scripts.

## What it does

- **Catalog search** — full-text search across NeoDB's unified media catalog (`/api/catalog/search`)
- **Item lookup** — fetch rich metadata by UUID for any category: `book`, `movie`, `tv`, `music`, `game`, `podcast`, `performance`
- **Shelf management** (auth required) — read/write the user's `wishlist`, `progress`, and `complete` shelves; mark items with ratings and comments
- **Typed response shape** — TypeScript interface for NeoDB `Item` included in the skill docs

## When the skill triggers

- Searching for book / movie / music / game metadata
- Building a media tracking or collection feature
- Integrating with the NeoDB platform or federated cataloging
- Looking up ISBNs, cast, ratings, cover images, or localized titles

## Install

```bash
npx skills add CorrectRoadH/skills
```

## Dependencies

- `curl` (or `fetch`) — that's it. Public endpoints require no authentication.
- `jq` recommended for projecting large responses on the CLI.

## Keywords

NeoDB API · neodb.social · federated media catalog · ActivityPub books · Douban alternative · Goodreads alternative · Letterboxd alternative · book metadata API · movie metadata API · media cataloging · social reading · AI agent skill · Claude skill
