[English](README.md) | **简体中文**

# Google 广告透明度 API

按域名或广告主 ID 查询任意广告主在 Google 上投放的广告，以 JSON 返回广告形式及首次、最近展示日期。

由 [Serpent API](https://apiserpent.com) 提供。完整文档：**[Google Ads Transparency API 文档](https://apiserpent.com/google-ads-transparency-api)**。

## 快速开始

1. 在 [apiserpent.com](https://apiserpent.com) 注册并获取 API Key，每个账号赠送 10 次免费调用。
2. 在请求头 `X-API-Key` 中带上你的 Key 调用接口：

```bash
curl -G "https://apiserpent.com/api/google-ads/transparency" \
  --data-urlencode "q=nike.com" \
  --data-urlencode "region=US" \
  -H "X-API-Key: $SERPENT_API_KEY"
```

## 接口

`GET https://apiserpent.com/api/google-ads/transparency`

| 参数 | 必填 | 说明 |
| --- | --- | --- |
| `q` | 是 | 网站域名（如 `nike.com`）或广告主 ID（`AR` 加 20 位数字） |
| `region` | 否 | 两位国家代码，默认 `US` |
| `ad_format` | 否 | `all`（默认）、`text`、`image`、`video` |
| `page_token` | 否 | 上一次响应中的 `next_page_token`，用于翻页 |

## 返回结果

顶层字段：`success`、`query`、`region`、`ad_format`、`ads[]`（每次最多 40 条）、`next_page_token`。每条广告包含 `ad_id`、`advertiser_id`、`advertiser_name`、`format`、`first_shown`、`last_shown`、`image_url`、`preview_url`、`ad_url`。

完整字段列表和响应示例请参阅[文档](https://apiserpent.com/google-ads-transparency-api)。

## 示例代码

| 文件 | 语言 | 运行方式 |
| --- | --- | --- |
| [`example.py`](example.py) | Python 3（`pip install requests`） | `SERPENT_API_KEY=sk_live_... python example.py` |
| [`example.mjs`](example.mjs) | Node.js 18+（无需依赖） | `SERPENT_API_KEY=sk_live_... node example.mjs` |

## 应用场景

- 竞品广告调研
- 广告素材与投放监控
- 代理商报表

## Serpent API 的更多能力

- [Serpent API 文档](https://apiserpent.com/docs)：Google、Bing、Yahoo、DuckDuckGo 和 Brave 搜索结果，以及 AI 引用排名跟踪
- [GitHub 上的全部 SDK 与工具](https://github.com/apiserpent)

## 许可证

MIT
