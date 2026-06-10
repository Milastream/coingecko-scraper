[Coingecko Scraper](https://apify.com/plantane/coingecko-scraper?fpr=data)

Apify actor that scrapes cryptocurrency data from CoinGecko's free public API.

## Features

- **Markets mode** — Top coins by market cap with full pricing data
- **Trending mode** — Currently trending coins on CoinGecko
- **Search mode** — Search for specific coins by name/symbol
- **Optional detail enrichment** — Fetch extra data (description, links, sentiment) per coin

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `mode` | string | `"markets"` | `markets`, `trending`, or `search` |
| `vs_currency` | string | `"usd"` | Target currency for prices |
| `per_page` | integer | `100` | Results per API page (max 250) |
| `max_items` | integer | `10` | Maximum items to return |
| `search_query` | string | `""` | Query for search mode |
| `order` | string | `"market_cap_desc"` | Sort order for markets |
| `include_details` | boolean | `false` | Fetch extra detail per coin |

## Output

### Markets mode

Full market data: id, symbol, name, image, current_price, market_cap, market_cap_rank, fully_diluted_valuation, total_volume, high_24h, low_24h, price_change_24h, price_change_percentage_24h, circulating_supply, total_supply, max_supply, ath, ath_change_percentage, ath_date, atl, atl_change_percentage, atl_date, last_updated.

With `include_details`: also description, homepage, genesis_date, sentiment data.

### Trending mode

id, name, symbol, market_cap_rank, thumb, score.

### Search mode

id, name, symbol, market_cap_rank, thumb.

## Rate Limits

CoinGecko's free API allows ~10-30 requests/minute. The scraper adds 1.5s delays between requests and handles 429 responses with a 60s backoff.