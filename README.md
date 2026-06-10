[Coingecko Scraper](https://apify.com/makework36/coingecko-scraper?fpr=data)

# CoinGecko Crypto Scraper

Get cryptocurrency prices, market rankings, trending coins, and global market stats from the CoinGecko API. No API key required.

## What data does it extract?

### Markets / Coin Detail mode

| Field | Description |
| --- | --- |
| `id` | CoinGecko identifier (e.g. `bitcoin`) |
| `symbol` | Ticker symbol (e.g. `btc`) |
| `name` | Full coin name |
| `currentPrice` | Current price in your chosen currency |
| `marketCap` | Market capitalization |
| `marketCapRank` | Rank by market cap |
| `volume24h` | 24-hour trading volume |
| `priceChange24h` | Absolute 24h price change |
| `priceChangePercent24h` | Percentage 24h price change |
| `high24h` | 24-hour high price |
| `low24h` | 24-hour low price |
| `ath` | All-time high price |
| `athDate` | Date of all-time high |
| `circulatingSupply` | Coins currently in circulation |
| `totalSupply` | Total supply |
| `image` | Coin logo URL |

### Trending mode

| Field | Description |
| --- | --- |
| `id` | CoinGecko identifier |
| `symbol` | Ticker symbol |
| `name` | Coin name |
| `marketCapRank` | Market cap rank |
| `priceBtc` | Price in BTC |
| `priceUsd` | Price in USD |
| `score` | Trending score |
| `thumb` | Thumbnail image URL |
| `marketCap` | Market capitalization |
| `totalVolume` | Trading volume |

### Global mode

| Field | Description |
| --- | --- |
| `activeCryptocurrencies` | Number of active cryptocurrencies |
| `markets` | Number of active markets |
| `totalMarketCapUsd` | Total market cap in USD |
| `totalVolumeUsd` | Total 24h volume in USD |
| `btcDominance` | Bitcoin dominance percentage |
| `ethDominance` | Ethereum dominance percentage |
| `marketCapChangePercent24hUsd` | 24h market cap change % |
| `marketCapPercentage` | Market cap share per coin |
| `updatedAt` | Last update timestamp |

## Use cases

- **Portfolio dashboards** -- Pull live prices for your holdings into Google Sheets or a database.
- **Market screening** -- Rank the top 500 coins by market cap and filter by price change.
- **Trend spotting** -- Check which coins are trending on CoinGecko right now.
- **DeFi research** -- Filter by category (e.g. `decentralized-finance-defi`) to analyze specific sectors.
- **Market snapshots** -- Get a daily global overview of total crypto market cap and BTC dominance.

## How to use

**Get the top 50 coins by market cap:**

```
{
    "mode": "markets",
    "vsCurrency": "usd",
    "maxResults": 50
}
```

**See what's trending right now:**

```
{
    "mode": "trending"
}
```

**Get details for specific coins in EUR:**

```
{
    "mode": "coin_detail",
    "coinIds": ["bitcoin", "ethereum", "solana"],
    "vsCurrency": "eur"
}
```

## Input parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `mode` | enum | `"markets"` | `markets`, `trending`, `global`, or `coin_detail` |
| `vsCurrency` | string | `"usd"` | Quote currency (e.g. `usd`, `eur`, `btc`) |
| `maxResults` | integer | `100` | Max coins to return in markets mode (1-500) |
| `coinIds` | string[] | `[]` | CoinGecko IDs for coin_detail mode |
| `category` | string | `""` | Category filter for markets mode (e.g. `layer-1`, `meme-token`) |

## Output example

```
{
    "id": "bitcoin",
    "symbol": "btc",
    "name": "Bitcoin",
    "currentPrice": 67432.00,
    "marketCap": 1328456789012,
    "marketCapRank": 1,
    "volume24h": 28945678901,
    "priceChange24h": 1234.56,
    "priceChangePercent24h": 1.87,
    "high24h": 68100.00,
    "low24h": 66200.00,
    "ath": 73750.00,
    "athDate": "2025-11-14T09:15:00.000Z",
    "circulatingSupply": 19623450,
    "totalSupply": 21000000,
    "image": "https://assets.coingecko.com/coins/images/1/large/bitcoin.png"
}
```

## Performance & cost

- Markets mode fetches up to 250 coins per API call, so 500 coins takes just 2 requests.
- A 2.5-second delay is applied between pages to respect CoinGecko's free tier rate limits (10-30 req/min).
- A typical run for 100 coins completes in under 10 seconds and costs less than $0.01 on Apify.

## FAQ

**Do I need a CoinGecko API key?**
No. The actor uses the free public API. Rate limits are 10-30 requests per minute, and the actor handles retries with exponential backoff on 429 responses.

**What coin IDs should I use in coin_detail mode?**
CoinGecko IDs are lowercase slugs like `bitcoin`, `ethereum`, `solana`. You can find them on any CoinGecko coin page in the URL, or use markets mode first to discover IDs.

**Can I get prices in EUR or BTC?**
Yes. Set `vsCurrency` to any currency CoinGecko supports: `usd`, `eur`, `gbp`, `jpy`, `btc`, `eth`, and many more.

**How current is the data?**
CoinGecko updates prices every 1-2 minutes on the free tier. The data you get is near real-time.