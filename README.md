**English** | [简体中文](README.zh-CN.md)

# Google Ads Transparency API

See the ads any advertiser is running on Google, by domain or advertiser ID, with formats and first/last shown dates as JSON.

Powered by [Serpent API](https://apiserpent.com). Full reference: **[Google Ads Transparency API docs](https://apiserpent.com/google-ads-transparency-api)**.

## Quick start

1. Get an API key at [apiserpent.com](https://apiserpent.com). Every account starts with 10 free API calls.
2. Call the endpoint with your key in the `X-API-Key` header:

```bash
curl -G "https://apiserpent.com/api/google-ads/transparency" \
  --data-urlencode "q=nike.com" \
  --data-urlencode "region=US" \
  -H "X-API-Key: $SERPENT_API_KEY"
```

## Endpoint

`GET https://apiserpent.com/api/google-ads/transparency`

| Parameter | Required | Description |
| --- | --- | --- |
| `q` | Yes | A website domain (`nike.com`) or an advertiser ID (`AR` + 20 digits) |
| `region` | No | Two-letter country code, default `US` |
| `ad_format` | No | `all` (default), `text`, `image`, `video` |
| `page_token` | No | `next_page_token` from the previous response |

## Response

`success`, `query`, `region`, `ad_format`, `ads[]` (up to 40), `next_page_token`. Each ad has `ad_id`, `advertiser_id`, `advertiser_name`, `format`, `first_shown`, `last_shown`, `image_url`, `preview_url`, `ad_url`.

See the [docs](https://apiserpent.com/google-ads-transparency-api) for the complete field list and sample responses.

## Examples

| File | Language | Run |
| --- | --- | --- |
| [`example.py`](example.py) | Python 3 (`pip install requests`) | `SERPENT_API_KEY=sk_live_... python example.py` |
| [`example.mjs`](example.mjs) | Node.js 18+ (no dependencies) | `SERPENT_API_KEY=sk_live_... node example.mjs` |

## Use cases

- Competitor ad research
- Creative and campaign monitoring
- Agency reporting

## More from Serpent API

- [Serpent API docs](https://apiserpent.com/docs) - Google, Bing, Yahoo, DuckDuckGo and Brave search, plus AI rank tracking
- [All SDKs and tools on GitHub](https://github.com/apiserpent)

## License

MIT
