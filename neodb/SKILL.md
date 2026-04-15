---
name: neodb
description: NeoDB API integration for searching and managing books, movies, music, TV shows, games, and podcasts. Use when working with NeoDB (neodb.social), querying media catalogs, building media tracking features, or integrating with NeoDB's social cataloging platform. Triggers on (1) searching for book/movie/music metadata, (2) building media collection features, (3) NeoDB API integration, (4) media catalog queries.
version: 1.1.0
---

# NeoDB API

Public endpoints are auth-free — reach for `curl`/`fetch` directly. No bundled scripts; this skill is pure documentation.

Base URL: `https://neodb.social`

## Endpoints

### Search (public)

```
GET /api/catalog/search?query={query}&page={page}
```

```bash
curl "https://neodb.social/api/catalog/search?query=The%20Matrix&page=1" \
  | jq '.data[] | {title: .display_title, year: (.pub_year // .year), url}'
```

Response: `{ data: Item[], pages, count }`

### Get item (public)

```
GET /api/{category}/{uuid}
```

Categories: `book`, `movie`, `tv`, `music`, `game`, `podcast`, `performance`

```bash
curl "https://neodb.social/api/movie/0TedD5jkKhyavhtwJkqOxi" \
  | jq '{title: .display_title, year, rating, cast: .actor[0:3]}'
```

Use `jq` to project only the fields you need — full responses can be large (descriptions, external_resources, localized_title, etc.).

### User shelf (auth required)

```
GET /api/me/shelf/{shelf_type}
Authorization: Bearer <token>
```

Shelf types: `wishlist`, `progress`, `complete`

### Mark item (auth required)

```
POST /api/me/shelf/item/{uuid}
Authorization: Bearer <token>
Content-Type: application/json

{"shelf_type": "complete", "rating_grade": 8, "comment_text": "Great!"}
```

## Item shape (abridged)

```typescript
interface Item {
  id: string;
  uuid: string;
  type: 'book' | 'movie' | 'tv' | 'music' | 'game' | 'podcast';
  url: string; api_url: string; category: string;
  title: string; display_title: string; orig_title: string;
  description: string; brief: string; cover_image_url: string;
  rating: number | null; rating_count: number;

  // Books
  author: string[]; translator: string[]; pub_house: string;
  pub_year?: number; pub_month?: number; pages: number;
  isbn: string; binding: string; price: string; series: string | null;

  // Movies/TV
  actor: string[]; year?: number;

  // Common
  language: string[]; subtitle: string | null;
  external_resources: { url: string }[];
  localized_title: { lang: string; text: string }[];
  localized_description: { lang: string; text: string }[];
}
```

## Implementation pattern (TS)

```typescript
async function searchNeoDB(query: string, page = 1) {
  const ctrl = new AbortController();
  const t = setTimeout(() => ctrl.abort(), 10_000);
  try {
    const q = encodeURIComponent(query.trim().slice(0, 200));
    const res = await fetch(`https://neodb.social/api/catalog/search?query=${q}&page=${page}`, { signal: ctrl.signal });
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return (await res.json()).data ?? [];
  } finally { clearTimeout(t); }
}
```

## Best practices

- Debounce search inputs ~500ms.
- 10s request timeout.
- Sanitize input: trim + cap at 200 chars.
- Validate `cover_image_url` before rendering.
- Display year: `pub_year || year`.
- For multi-language UIs, prefer `localized_title` over `title`.
- Always `jq`-project responses when calling from the CLI — raw JSON is token-heavy.
