# MapTrader Crypto Markets

Vietnamese, buildless crypto dashboard inspired by CoinMarketCap and Top100Token, created alongside the existing Kronos research project at https://github.com/xulytiengviet/maptrader.

## Run
Serve `dist/` with any static HTTP server. No installation, API key, wallet or sign-in is needed. The deployment manifest targets `dist/`.

## Data
- CoinGecko `/api/v3/coins/markets`: top 100 by market cap, USD, hourly/24h/7d change and 7-day sparklines. `/global` supplies market-wide metrics.
- DEX Screener `/latest/dex/search`: search by name or contract, filter returned pairs by chain. Default SOL search, sorted by volume. This is a search result, not a comprehensive trending ranking. Pool-level prices may differ and token names are not verified identities.
- DefiLlama `/v2/chains`: TVL rankings. TVL is distinct from token market cap.

These are public third-party APIs, not a claim that their services are all open-source. Provider limits, availability and CORS rules apply. DefiLlama publishes open-source adapters separately.

The app attempts a live refresh on startup and every 120 seconds while visible. Each dataset has its own status. Bundled actual API captures and localStorage caches are explicitly labeled as saved data when live calls fail. Provider timestamps are shown on coin details; fetch time is shown on each table. A live fetch is not a guarantee that an upstream observation is current. Missing values remain dashes; there are no generated market values or forecast curves.

## Features
Responsive light/dark layout, asset detail dialogs, historical sparklines, sort, search, DEX chain filters, chain rankings, local watchlist, equal-cell change heatmap, CSV export (formula injection neutralized). No transaction execution.

## Kronos
The original repository is a Python OHLCV prediction model and Flask UI. This dashboard is a companion UI, not a port of the ML runtime. Kronos Lab explains its unconnected state and links to the existing code; predictions require the original Python backend and model weights. Existing model/training code is unchanged.

## Validation
JavaScript syntax checked with `node --check dist/app.js`. Browser checks covered live API market rendering, DEX results, watchlist add and filter, and Bitcoin detail history. No secret keys are embedded. Public provider data is escaped before HTML rendering; outbound URLs use HTTPS.
