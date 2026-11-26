---
name: adlane
description: Ad library search with Adlane. See competitor ads across the Meta, TikTok, LinkedIn and Google ad libraries at once, save ads to boards and track competitors' new ads. Use when someone asks what ads a brand or competitor is running, wants an ad spy or ad intelligence lookup, wants ad examples for ad creative research on a product or keyword, or wants to build a swipe file.
---

# Adlane: ad library search

Adlane (https://adlane.app) searches the public ad libraries of Meta (Facebook, Instagram), TikTok, LinkedIn and Google (Search, YouTube, Display) in one call and returns normalised ads.

## Connect

- MCP (Streamable HTTP): `https://adlane.app/mcp`. Sign in with OAuth to your Adlane account (any plan; a free account includes 5 searches, no card), or send `Authorization: Bearer adl_…` (Pro API key).
- REST: `https://adlane.app/v1/…` with the same bearer key. Reference: https://adlane.app/mcp/

## Tools

| Tool | What it does | Cost |
|---|---|---|
| `search_ads` | `query` plus optional `mode` (keyword, advertiser, domain), `platforms`, `country`. Returns ads per platform and a `search_id`. | One search from the plan (Free: 5 in total, one time; Starter 250 a month; Pro 800 a month). Repeats within 12 hours are cached. |
| `get_usage` | Plan, searches left, limits. | No search used |
| `list_boards`, `get_board`, `create_board` | Read and organise boards. | No search used |
| `save_ad` | `search_id` + `ad_key` from `search_ads`, optional `board_id` and `note`. | No search used |
| `list_competitors`, `track_competitor` | Tracked brands and their new ads; start tracking one. | Counts toward the competitor limit; on Free the first check uses one free search |

## How to search well

1. When the user names a company, search its website domain (`mode: "domain"`, e.g. `allbirds.com`). It is the most precise query and the only one Google accepts besides the advertiser name.
2. For ideas in a category, use `mode: "keyword"` with the words a customer would use, on Meta, TikTok and LinkedIn.
3. Ads that started long ago and are still active are usually the ones that work. Point those out first.
4. Quote the ad copy, hook and offer; link to `library_url` so the user can see the original.
5. Before many searches, call `get_usage`. When a plan limit is reached the tool says so and links to https://adlane.app/pricing/.

Adlane is independent of Meta, TikTok, LinkedIn and Google and shows only what their libraries publish (no spend estimates).
