## Abhyuday

Senior frontend engineer. I build the real-time layer of trading products: live market data, charts and order flow that stay fast and correct under a constant stream of updates.

Now: remote contract on a live multi-chain trading terminal (Solana, BNB, Base, Ethereum), across a Next.js app on Cloudflare Workers, a React Native app and Go services. 92 PRs merged to production across 7 repositories in under 5 months.

### Selected results

| | Before | After |
|---|---|---|
| Token click → chart drawn | ~1 s | 35–120 ms |
| Token switch on the new trade page (beta) | 386–482 ms | 92–102 ms |
| Live feed staleness with several tabs open | 48–85 s | ~1 s |
| Hidden tab memory over 42 minutes | 267 → 2,569 MB | 50 → 68 MB |
| Balance shown after a trade (production median) | 10.3 s | 0.8 s |
| Peak open candle sockets on the live site | 108 | 4 |
| Chart requests per page load, Trending board | 241 | 0 |
| Repeat coin-metadata lookup | 0.93 s | 3 ms |

### How

- **Sockets:** one SharedWorker owns every connection. Tabs subscribe to topics over one multiplexed WebSocket with sequence-based resume, on a Go socket protocol I specified.
- **Charts:** a persistent TradingView Advanced Charts host, a shared candle cache and prefetching of the rows in view.
- **Memory:** traced retained memory to decoded bitmaps pinned outside the JS heap, which earlier profiling had missed.
- **Edge:** R2-backed chunk retention ends post-deploy ChunkLoadErrors, Worker edge caches answer repeat lookups, and first-load JS is down ~130 KB gzip.
- **Testing:** money paths get tests that are themselves tested; one reconcile module's suite catches 773 of 814 mutants.

### Focus

TypeScript · React · Next.js · WebSockets and Web Workers · TradingView · Cloudflare Workers · Solana (Anchor, web3.js) · Rust · Go

### Before this

First frontend engineer at a startup (0 → 1: Next.js, Three.js product configurators, 3D payloads cut ~90%), Solana DeFi frontends and Anchor programs, and 150+ students mentored in frontend engineering.

[LinkedIn](https://www.linkedin.com/in/abhyuday911/)

<sub>Most of this work lives in private repositories; the contribution graph includes it.</sub>
