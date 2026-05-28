## Abhyuday

Senior frontend engineer on the real-time layer of trading products: live market data, charts and order flow. Currently on a live multi-chain trading terminal (Solana, BNB, Base, Ethereum), with 92 PRs to production across 7 repos in under 5 months.

| | Before | After |
|---|---|---|
| Solana token click → first candles | 900–1,160 ms | 35–117 ms |
| Live feed staleness across tabs | 48–85 s | ~1 s |
| Hidden tab memory after 42 min | 2,569 MB | 68 MB |
| Balance shown after a trade | 10.3 s | 0.8 s |

TypeScript · React · Next.js · WebSockets / SharedWorkers · TradingView · Cloudflare Workers · Solana · Rust · Go

[LinkedIn](https://www.linkedin.com/in/abhyuday911/) · <sub>most of my work is in private repos</sub>

<details><summary>More detail</summary>

### More results

| | Before | After |
|---|---|---|
| Token switch on the new trade page (beta) | 386–482 ms | 92–102 ms |
| Peak open candle sockets on the live site | 108 | 4 |
| Chart requests per page load, Trending board | 241 | 0 |
| Repeat coin-metadata lookup | 0.93 s | 3 ms |

### How

- **Sockets:** one SharedWorker owns every connection. Tabs subscribe to topics over one multiplexed WebSocket with sequence-based resume, on a Go socket protocol I specified.
- **Charts:** a persistent TradingView Advanced Charts host, a shared candle cache and prefetching of the rows in view.
- **Memory:** traced retained memory to decoded bitmaps pinned outside the JS heap, which earlier profiling had missed.
- **Edge:** R2-backed chunk retention ends post-deploy ChunkLoadErrors, Worker edge caches answer repeat lookups, and first-load JS is down ~130 KB gzip.
- **Testing:** money paths get tests that are themselves tested; one reconcile module's suite catches 773 of 814 mutants.

### Before this

First frontend engineer at a startup (0 → 1: Next.js, Three.js product configurators, 3D payloads cut ~90%), Solana DeFi frontends and Anchor programs, and 150+ students mentored in frontend engineering.

</details>
