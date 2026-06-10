[Coingecko Scraper](https://apify.com/parseforge/coingecko-scraper?fpr=data)

![ParseForge Banner](https://images.apifyusercontent.com/RHzPvdHJ2joNXJHSWjeziGDTOTaycOsfmbNq9q8ZVRM/w:1800/cb:1/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL1BhcnNlRm9yZ2UvYXBpZnktYXNzZXRzL21haW4vYmFubmVyLmpwZw.webp)

# 💰 CoinGecko Cryptocurrency Scraper

> 🚀 Collect real-time prices, market cap, volume, supply metrics, and ATH/ATL records for 15,000+ cryptocurrencies. Filter by category, sort by market cap or volume, and export in seconds.

> 🕒 Last updated: 2026-04-17

CoinGecko Scraper pulls live market data for thousands of cryptocurrencies. Each record includes the current price, market cap, 24h trading volume, fully diluted valuation, circulating and max supply, all-time high and low with dates, price change percentages across six timeframes (1h, 24h, 7d, 14d, 30d, 1y), and 7-day sparkline data for charting. You can filter by category (DeFi, gaming, layer-1, stablecoins) and sort by market cap or volume.

Crypto traders use this to monitor price movements across their watchlist. DeFi builders feed it into protocol dashboards. Analysts compare performance across token categories. Portfolio tool developers pull live data without managing API keys or rate limits. If you need structured crypto market data at scale, this actor handles the collection and delivers clean, ready-to-use records.

| Target | CoinGecko (15,000+ cryptocurrencies) |
| --- | --- |
| Use Cases | Portfolio tracking, market analysis, price monitoring, DeFi research |

---

## 📋 What it does

- 💰 **Live market data.** Current price, market cap, volume, and fully diluted valuation for each coin.
- 📈 **Multi-timeframe changes.** Price change percentages over 1h, 24h, 7d, 14d, 30d, and 1 year.
- 📊 **Supply metrics.** Circulating, total, and maximum supply for token economics analysis.
- 🏆 **ATH and ATL tracking.** All-time high and low prices with exact dates and distance from current price.
- 🔍 **Category filtering.** Narrow results to DeFi, gaming, smart contract platforms, layer-2, stablecoins, and more.

Each record represents one cryptocurrency with 30+ data points. Sparkline arrays provide 7-day price history for chart rendering right out of the box.

> 💡 **Why it matters:** Manually tracking prices and market caps across hundreds of tokens means switching between tabs and copying numbers. This actor delivers everything in a single structured dataset, updated on demand.

---

## 🎬 Full Demo

*🚧 Coming soon: a 3-minute walkthrough showing how to go from sign-up to a downloaded dataset.*

---

## ⚙️ Input

| Input | Type | Default | Behavior |
| --- | --- | --- | --- |
| `vsCurrency` | string | `"usd"` | Base currency for prices. Options: usd, eur, gbp, jpy, btc, eth. |
| `maxItems` | integer | `10` | Maximum coins to return. Free users are limited to 10. Paid users can set up to 1,000,000. |
| `category` | string | - | Filter by category slug (e.g. "decentralized-finance-defi", "gaming"). Leave empty for all coins. |
| `order` | string | `"market_cap_desc"` | Sort order. Options: market_cap_desc, market_cap_asc, volume_desc, volume_asc. |

**Example: top 100 coins by market cap in USD.**

```
{
  "vsCurrency": "usd",
  "maxItems": 100,
  "order": "market_cap_desc"
}
```

**Example: DeFi tokens sorted by volume.**

```
{
  "vsCurrency": "usd",
  "category": "decentralized-finance-defi",
  "maxItems": 50,
  "order": "volume_desc"
}
```

> ⚠️ **Good to Know:** CoinGecko tracks over 15,000 cryptocurrencies. Large requests (1,000+ coins) may take a few minutes to complete. Category slugs can be found on the CoinGecko categories page.

---

## 📊 Output

Each record contains **30+ fields**. Download as CSV, Excel, JSON, or XML.

### 🧾 Schema

| Field | Type | Example |
| --- | --- | --- |
| 🖼️ `imageUrl` | string | `"https://assets.coingecko.com/coins/images/1/large/bitcoin.png"` |
| 🏷️ `name` | string | `"Bitcoin"` |
| 🔤 `symbol` | string | `"btc"` |
| 💰 `currentPrice` | number | `67234.00` |
| 📊 `marketCap` | number | `1324567890123` |
| 🏅 `marketCapRank` | integer | `1` |
| 📈 `totalVolume` | number | `28456789012` |
| 📉 `priceChangePercentage24h` | number | `2.45` |
| 🔄 `circulatingSupply` | number | `19700000` |
| 🏆 `ath` | number | `73750.07` |
| 📅 `athDate` | string | `"2024-03-14T07:10:36.635Z"` |
| 📉 `atl` | number | `67.81` |

### 📦 Sample records

 
 
 

---

## ✨ Why choose this Actor

|  | Capability |
| --- | --- |
| 💰 | **15,000+ coins.** Access market data for virtually every listed cryptocurrency. |
| 📈 | **Six timeframes.** Price changes over 1h, 24h, 7d, 14d, 30d, and 1 year in one record. |
| 🏆 | **ATH and ATL records.** All-time high and low prices with exact dates for historical context. |
| 📊 | **Sparkline data.** 7-day price arrays ready for chart rendering without extra API calls. |
| 🔍 | **Category filtering.** Focus on DeFi, gaming, layer-1, or any other token category. |
| 💱 | **Multi-currency.** View prices in USD, EUR, GBP, JPY, BTC, or ETH. |
| ⚡ | **Fast collection.** Hundreds of coins returned in seconds with structured, consistent fields. |

> CoinGecko tracks over 15,000 cryptocurrencies across 800+ exchanges, making it one of the largest crypto data aggregators in the world.

---

## 📈 How it compares to alternatives

| Approach | Cost | Coverage | Refresh | Setup |
| --- | --- | --- | --- | --- |
| **⭐ CoinGecko Scraper** *(this Actor)* | $5 free credit, then pay-per-use | 15,000+ coins, 30+ fields | **Live per run** | ⚡ 2 min |
| Official API (free tier) | Free | Rate-limited, fewer fields | Real-time | 15 min |
| Manual browsing | Free (your time) | One coin at a time | Manual | Slow |
| Third-party data providers | $100+/month | Varies | Hourly or daily | Hours |

Pick this actor when you need bulk crypto market data without managing API keys, rate limits, or pagination.

---

## 🚀 How to use

1. 📝 **Sign up.** [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=vmoqkp) (takes 2 minutes).
2. 🌐 **Open the Actor.** Go to the CoinGecko Scraper page on the Apify Store.
3. 🎯 **Set input.** Choose your base currency, category filter, sort order, and max items.
4. 🚀 **Run it.** Click **Start** and let the Actor collect your data.
5. 📥 **Download.** Grab your results in the **Dataset** tab as CSV, Excel, JSON, or XML.

> ⏱️ Total time from signup to downloaded dataset: **3-5 minutes.** No coding required.

---

## 💼 Business use cases

| ### 📈 Trading and Analytics     - Monitor price changes across your watchlist in real time - Track volume spikes to identify momentum shifts - Compare ATH distances to find undervalued tokens - Build screeners filtered by category and market cap | ### 🏗️ DeFi and Protocol Development     - Feed live token prices into protocol dashboards - Track circulating supply changes for tokenomics modeling - Monitor competitor token market caps and volumes - Build automated alerts for price threshold crossings |
| --- | --- |
| ### 📊 Research and Reporting     - Analyze performance trends across token categories - Compare layer-1 vs layer-2 market cap ratios over time - Study ATH/ATL patterns for market cycle research - Generate weekly market summary reports automatically | ### 🛠️ Portfolio and App Development     - Power real-time portfolio trackers with live price feeds - Build comparison tools showing side-by-side token stats - Create leaderboard views sorted by any metric - Feed sparkline data into chart components directly |

---

---

## 🌟 Beyond business use cases

Data like this powers more than commercial workflows. The same structured records support research, education, civic projects, and personal initiatives.

| ### 🎓 Research and academia     - Empirical datasets for papers, thesis work, and coursework - Longitudinal studies tracking changes across snapshots - Reproducible research with cited, versioned data pulls - Classroom exercises on data analysis and ethical scraping | ### 🎨 Personal and creative     - Side projects, portfolio demos, and indie app launches - Data visualizations, dashboards, and infographics - Content research for bloggers, YouTubers, and podcasters - Hobbyist collections and personal trackers |
| --- | --- |
| ### 🤝 Non-profit and civic     - Transparency reporting and accountability projects - Advocacy campaigns backed by public-interest data - Community-run databases for local issues - Investigative journalism on public records | ### 🧪 Experimentation     - Prototype AI and machine-learning pipelines with real data - Validate product-market hypotheses before engineering spend - Train small domain-specific models on niche corpora - Test dashboard concepts with live input |

## 🤖 Ask an AI assistant about this scraper

Open a ready-to-send prompt about this ParseForge actor in the AI of your choice:

- 💬 [**ChatGPT**](https://chat.openai.com/?q=How%20do%20I%20use%20the%20CoinGecko%20Cryptocurrency%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🧠 [**Claude**](https://claude.ai/new?q=How%20do%20I%20use%20the%20CoinGecko%20Cryptocurrency%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🔍 [**Perplexity**](https://perplexity.ai/search?q=How%20do%20I%20use%20the%20CoinGecko%20Cryptocurrency%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🅒 [**Copilot**](https://copilot.microsoft.com/?q=How%20do%20I%20use%20the%20CoinGecko%20Cryptocurrency%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)

## ❓ Frequently Asked Questions

### 💳 Do I need a paid Apify plan to run this actor?

No. You can start right now on the free Apify plan, which includes **$5 in free monthly credit**. That is enough to run this actor several times and explore the output before committing to anything. Paid plans unlock higher limits, more concurrent runs, and larger datasets. [Create a free Apify account here](https://console.apify.com/sign-up?fpr=vmoqkp) to get started.

### 🚨 What happens if my run fails or returns no results?

Failed runs are not charged. If the source site changes, proxies get rate-limited, or a specific input matches nothing, re-run the actor or open our [contact form](https://tally.so/r/BzdKgA) and we will investigate. You can also check the run log in the Apify console to see why the run stopped.

### 📏 How many items can I scrape per run?

Free users are limited to **10 items per run** so you can preview the output and confirm the actor works for your use case. Paid users can raise `maxItems` up to **1,000,000** per run. [Upgrade here](https://console.apify.com/sign-up?fpr=vmoqkp) if you need full scale.

### 🕒 How fresh is the data?

Every run fetches live data at the moment of execution. There is no cache or delay: the records you get reflect what the source returned at that moment. Schedule the actor to maintain a rolling snapshot of the data you need.

### 🧑‍💻 Can I call this actor from my own code?

Yes. Apify exposes every actor as a REST endpoint and ships first-class SDKs for [Node.js](https://docs.apify.com/sdk/js) and [Python](https://docs.apify.com/sdk/python). You can start a run, read the dataset, and handle webhooks from your own app in a few lines. All you need is your Apify API token.

### 📤 How do I export the data?

Every Apify dataset can be downloaded in one click from the console as CSV, JSON, JSONL, Excel, HTML, XML, or RSS. You can also pull results programmatically via the [Apify API](https://docs.apify.com/api/v2) or stream them into BigQuery, S3, and other destinations through built-in integrations.

### 📅 Can I schedule the actor to run automatically?

Yes. Use the Apify scheduler to run the actor on any cadence, from hourly to monthly. Results are saved to your dataset and can be delivered to webhooks, email, Slack, cloud storage, or automation tools such as Zapier and Make.

---

## 🔌 Automating CoinGecko Scraper

Control the scraper programmatically for scheduled runs and pipeline integrations:

- 🟢 **Node.js.** Install the `apify-client` NPM package.
- 🐍 **Python.** Use the `apify-client` PyPI package.
- 📚 See the [Apify API documentation](https://docs.apify.com/api/v2) for full details.

The [Apify Schedules feature](https://docs.apify.com/platform/schedules) lets you trigger this Actor on any cron interval. Schedule hourly runs to build a historical crypto price database.

## 🔌 Integrate with any app

CoinGecko Scraper connects to any cloud service via [Apify integrations](https://apify.com/integrations):

- [**Make**](https://docs.apify.com/platform/integrations/make) - Automate multi-step workflows
- [**Zapier**](https://docs.apify.com/platform/integrations/zapier) - Connect with 5,000+ apps
- [**Slack**](https://docs.apify.com/platform/integrations/slack) - Get run notifications
- [**Airbyte**](https://docs.apify.com/platform/integrations/airbyte) - Pipe data into your warehouse
- [**GitHub**](https://docs.apify.com/platform/integrations/github) - Trigger runs from commits
- [**Google Drive**](https://docs.apify.com/platform/integrations/drive) - Export datasets straight to Sheets

You can also use webhooks to trigger downstream actions when a run finishes.

---

## 🔗 Recommended Actors

- [**📊 FRED Economic Data Scraper**](https://apify.com/parseforge/fred-scraper) - Pull Federal Reserve economic time-series data
- [**💼 SEC EDGAR Full Text Search**](https://apify.com/parseforge/sec-edgar-full-text-search-scraper) - Search SEC filings by keyword
- [**📈 BLS Wage Data Scraper**](https://apify.com/parseforge/bls-wage-data-scraper) - Get employment and wage statistics
- [**🏥 OpenFDA Drug Scraper**](https://apify.com/parseforge/openfda-drug-scraper) - FDA drug labels and adverse events
- [**⚽ ESPN Sports Scraper**](https://apify.com/parseforge/espn-sports-scraper) - Live scores, standings, and rosters

> 💡 **Pro Tip:** browse the complete [ParseForge collection](https://apify.com/parseforge) for more data scrapers and tools.

---

**🆘 Need Help?** [**Open our contact form**](https://tally.so/r/BzdKgA) to request a new scraper, propose a custom data project, or report an issue.

---

> **⚠️ Disclaimer:** this Actor is an independent tool and is not affiliated with, endorsed by, or sponsored by CoinGecko. All trademarks mentioned are the property of their respective owners. Only publicly available data is collected.