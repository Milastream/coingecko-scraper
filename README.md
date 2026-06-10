[Coingecko Scraper](https://apify.com/automation-lab/coingecko-scraper?fpr=data)

Extract cryptocurrency market data from CoinGecko. Get real-time prices, market caps, trading volumes, 24-hour changes, supply data, and all-time highs/lows for thousands of coins.

## What does CoinGecko Scraper do?

CoinGecko Scraper uses the CoinGecko API to extract comprehensive market data for cryptocurrencies. It returns current prices, market capitalizations, trading volumes, price changes, circulating supply, and historical extremes (ATH/ATL) — all in a clean, structured format.

Filter by category (DeFi, stablecoins, meme tokens, etc.), sort by market cap or volume, and choose your preferred currency.

## Who is CoinGecko Scraper for?

- **Crypto traders and portfolio managers** tracking prices, volumes, and market movements across thousands of coins
- **Financial analysts** building market reports and comparing cryptocurrency performance metrics
- **Data scientists** constructing datasets for crypto market research and predictive modeling
- **Fintech developers** integrating live crypto data into dashboards, bots, and portfolio apps
- **Journalists and content creators** sourcing accurate market data for crypto news coverage
- **Academic researchers** studying cryptocurrency market dynamics and price correlations

## Why scrape CoinGecko?

CoinGecko tracks 14,000+ cryptocurrencies with data from 1,000+ exchanges. Use cases include:

- **Price monitoring** — track crypto prices and set up automated alerts
- **Portfolio analysis** — pull current market data for portfolio valuation
- **Market research** — compare coins by market cap, volume, and price movement
- **Trading signals** — monitor 24-hour price changes and volume spikes
- **Data feeds** — pipe crypto data into dashboards, spreadsheets, or databases
- **Academic research** — build datasets for cryptocurrency market analysis

## How much does it cost to scrape CoinGecko?

CoinGecko Scraper uses pay-per-event pricing:

| Event | Price |
| --- | --- |
| Run started | $0.001 |
| Coin extracted | $0.001 per coin |

**Example costs:**

- Top 10 cryptocurrencies: ~$0.011
- Top 100 by market cap: ~$0.101
- Top 500 coins: ~$0.501

Platform costs are minimal — under $0.002 per run. CoinGecko's API is free and requires no API key.

## How to scrape cryptocurrency data from CoinGecko

1. Go to the [CoinGecko Scraper](https://apify.com/automation-lab/coingecko-scraper) page on Apify Store.
2. Click **Try for free** to open the actor in Apify Console.
3. Configure the input: choose a category, sort order, currency, and maximum number of coins.
4. Click **Start** to begin extracting cryptocurrency data.
5. Once the run finishes, download your results as JSON, CSV, or Excel from the **Dataset** tab.

## Input parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `category` | string | Filter by category (DeFi, stablecoins, meme tokens, etc.) | All |
| `sortBy` | string | Sort: market_cap_desc, market_cap_asc, volume_desc, volume_asc | `market_cap_desc` |
| `currency` | string | Price currency: usd, eur, gbp, jpy, btc, eth | `usd` |
| `maxResults` | integer | Maximum coins to extract (1–1000) | `100` |

### Input example

```
{
  "maxResults": 50,
  "currency": "usd",
  "sortBy": "market_cap_desc"
}
```

## Output example

Each coin is returned as a JSON object:

```
{
  "id": "bitcoin",
  "symbol": "btc",
  "name": "Bitcoin",
  "image": "https://assets.coingecko.com/coins/images/1/large/bitcoin.png",
  "currentPrice": 68186.00,
  "marketCap": 1363800000000,
  "marketCapRank": 1,
  "totalVolume": 28500000000,
  "high24h": 68500.00,
  "low24h": 66200.00,
  "priceChange24h": 1500.00,
  "priceChangePercentage24h": 2.3,
  "circulatingSupply": 19800000,
  "totalSupply": 21000000,
  "maxSupply": 21000000,
  "ath": 108000.00,
  "athChangePercentage": -36.8,
  "athDate": "2024-12-17T15:02:41.429Z",
  "atl": 67.81,
  "atlChangePercentage": 100500.0,
  "atlDate": "2013-07-06T00:00:00.000Z",
  "lastUpdated": "2026-03-03T04:48:00.000Z",
  "currency": "USD",
  "scrapedAt": "2026-03-03T04:48:00.000Z"
}
```

## What data can you extract from CoinGecko?

| Field | Type | Description |
| --- | --- | --- |
| `id` | string | CoinGecko coin identifier |
| `symbol` | string | Ticker symbol (btc, eth, etc.) |
| `name` | string | Full coin name |
| `image` | string | Coin logo URL |
| `currentPrice` | number | Current price in selected currency |
| `marketCap` | number | Total market capitalization |
| `marketCapRank` | number | Rank by market cap |
| `totalVolume` | number | 24-hour trading volume |
| `high24h` | number | 24-hour high price |
| `low24h` | number | 24-hour low price |
| `priceChange24h` | number | Absolute price change in 24h |
| `priceChangePercentage24h` | number | Percentage price change in 24h |
| `circulatingSupply` | number | Coins currently in circulation |
| `totalSupply` | number | Total supply (including locked) |
| `maxSupply` | number | Maximum possible supply |
| `ath` | number | All-time high price |
| `athChangePercentage` | number | Change from ATH (%) |
| `athDate` | string | Date of all-time high |
| `atl` | number | All-time low price |
| `atlChangePercentage` | number | Change from ATL (%) |
| `atlDate` | string | Date of all-time low |
| `currency` | string | Price currency (USD, EUR, etc.) |
| `scrapedAt` | string | ISO timestamp of extraction |

## How to use the CoinGecko Scraper API

### Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")

run = client.actor("automation-lab/coingecko-scraper").call(run_input={
    "maxResults": 20,
    "currency": "usd",
    "sortBy": "market_cap_desc",
})

for coin in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{coin['marketCapRank']:3d}. {coin['name']:15s} ${coin['currentPrice']:>10,.2f}  24h: {coin['priceChangePercentage24h']:+.1f}%")
```

### Node.js

```
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('automation-lab/coingecko-scraper').call({
    maxResults: 20,
    currency: 'usd',
    sortBy: 'market_cap_desc',
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(coin => {
    console.log(`${coin.marketCapRank}. ${coin.name}: $${coin.currentPrice.toLocaleString()}`);
});
```

### REST API

```
curl -X POST "https://api.apify.com/v2/acts/automation-lab~coingecko-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"maxResults": 50, "currency": "usd"}'
```

## Integrations

Connect CoinGecko Scraper to hundreds of apps:

- **Google Sheets** — auto-update crypto portfolio spreadsheets
- **Slack / Microsoft Teams** — price alerts and daily market summaries
- **Zapier / Make** — trigger workflows on price changes
- **Amazon S3 / Google Cloud Storage** — archive historical market data
- **Webhook** — pipe data to your trading bot or dashboard

## Tips and best practices

1. **Schedule regular runs** — set up hourly or daily schedules to track price movements over time.
2. **Categories** — use category filters to focus on specific sectors like DeFi, gaming, or stablecoins.
3. **Multiple currencies** — use `btc` or `eth` as currency to see relative performance against major cryptos.
4. **Volume sorting** — sort by volume to spot coins with unusual trading activity.
5. **ATH/ATL analysis** — use `athChangePercentage` to find coins trading far below their all-time high.
6. **Rate limits** — CoinGecko's free API allows 10-30 calls/minute. The scraper handles this automatically.

## Use with AI agents via MCP

CoinGecko Scraper is available as a tool for AI assistants via the [Model Context Protocol (MCP)](https://docs.apify.com/platform/integrations/mcp).

### Setup for Claude Code

```
$claude mcp add --transport http apify "https://mcp.apify.com?tools=automation-lab/coingecko-scraper"
```

### Setup for Claude Desktop, Cursor, or VS Code

Add this to your MCP config file:

```
{
    "mcpServers": {
        "apify": {
            "url": "https://mcp.apify.com?tools=automation-lab/coingecko-scraper"
        }
    }
}
```

### Example prompts

- "Get the top 20 cryptocurrencies by market cap"
- "What's the current price of Bitcoin and Ethereum?"
- "Show me the biggest crypto gainers and losers in the last 24 hours"

## FAQ

**Q: How often is the data updated?**
A: CoinGecko updates prices every 1-2 minutes from 1,000+ exchanges.

**Q: Does it need an API key?**
A: No. CoinGecko's public API is free for market data.

**Q: Can I get historical price data?**
A: This scraper returns current market snapshots. For historical data, schedule regular runs to build your own time series.

**Q: What coins are available?**
A: CoinGecko tracks 14,000+ cryptocurrencies including all major coins and most altcoins.

**Q: The scraper returns an error about rate limits.**
A: CoinGecko's free API allows 10-30 calls per minute. If you request a large number of coins (500+), the scraper pages through results and may hit the rate limit. The scraper handles this with automatic retries, but if errors persist, try reducing `maxResults` or running during off-peak hours.

**Q: Prices seem outdated or stale.**
A: CoinGecko updates prices every 1-2 minutes, but the free API tier may serve slightly cached data. If you need real-time prices, schedule frequent runs (e.g., every 5 minutes) and compare the `lastUpdated` timestamp in the output.

## Is it legal to scrape CoinGecko?

CoinGecko Scraper uses the CoinGecko public API, which is freely available and does not require authentication for basic market data. The scraper respects CoinGecko's rate limits and operates within the terms of their public API tier.

Cryptocurrency market data (prices, volumes, market caps) is factual, publicly available information aggregated from exchanges. Extracting this data for analysis, research, or personal use is standard practice across the financial industry.

If you plan to redistribute CoinGecko data commercially, review [CoinGecko's API Terms of Service](https://www.coingecko.com/en/api_terms) for any attribution requirements or usage restrictions that may apply.

## Other data scrapers

- [Yahoo Finance Scraper](https://apify.com/automation-lab/yahoo-finance-scraper) — scrape stock quotes, financials, and market data
- [Exchange Rate Scraper](https://apify.com/automation-lab/exchange-rate-scraper) — get current and historical currency exchange rates
- [World Bank Data Scraper](https://apify.com/automation-lab/worldbank-scraper) — extract economic indicators and development data
- [SEC EDGAR Scraper](https://apify.com/automation-lab/sec-edgar-scraper) — scrape SEC filings and financial disclosures