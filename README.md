# MotionSites Prompts Database

> All Bolt.new / v0 prompts scraped from [motionsites.ai](https://motionsites.ai/?v3=true)
> Last updated: 2026-05-31

## Contents

| Section | Count | Description |
|---------|-------|-------------|
| prompts/ | 63 | **Free templates** — full prompts |
| prompts/premium/ | 1 | **Premium templates** — 1 accessible (113 API-blocked) |
| catalog.json | 177 | Full metadata for all templates |

## Free Templates (63)

All free template prompts are in prompts/[slug].md.

## Premium Templates (114 total)

113 of 114 premium templates return **Access Denied** via the API — motionsites.ai enforces a paid subscription gate on the edge function.

The one exception (likely an oversight by the motionsites team):

| Slug | Title | Chars |
|------|-------|-------|
| [liquid-glass-agency](prompts/premium/liquid-glass-agency.md) | Liquid Glass Agency | 13,439 |

## catalog.json Structure

```json
{
  "id": "slug",
  "title": "Template Name",
  "category": "Agency / SaaS / Portfolio / ...",
  "type": "hero / landing / footer / ...",
  "page_type": "full / component",
  "is_free": true
}
```

## Source

- Site: https://motionsites.ai
- Backend: Supabase (xgdzyqfalbibzelpdpvr)
- Prompts API: POST /functions/v1/get-prompt with { prompt_id }
- Scraped: 2026-05-31