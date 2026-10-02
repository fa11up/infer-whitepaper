# INFER — whitepaper

Source for the INFER whitepaper, served from IPFS and named under ENS at
**[infer.miyagod.eth.limo](https://infer.miyagod.eth.limo)**.

*INFER — Inference-Backed Endogenous Financial Reserve.* A stablecoin whose supply, stability
and governance emerge from the economics of a decentralised AI compute network, plus a measured
account of what that network costs to run and what it should charge.

## This repository

| | |
|---|---|
| `index.html` | the entire paper — one self-contained file, no build step |
| `.github/workflows/ipfs.yml` | pins the paper to IPFS on every push to `main` |

The page is deliberately a single file: no bundler, no framework, no external stylesheet. The
only runtime dependencies are Google Fonts, and two optional feeds described below. It renders
and prints correctly with all of them blocked.

## Live figures

Dollar amounts denominated in IMD recompute from the live token price when the page is opened
online, because a spot price written into a document is stale within hours. Sources:

- **[DexScreener](https://dexscreener.com)** — IMD/ETH price, deepest-liquidity pair
- **[api.imd.fun/swarm](https://api.imd.fun/swarm)** — network health shown in the status strip

Both are CORS-open, so no proxy is needed. If either is unreachable every figure falls back to
the value published on 2 October 2026 at $6.00/IMD, and the status strip says so. Token counts,
inference costs and network scale are *not* live — they are measurements, not quotes.

## Discussion

Each of the thirteen top-level sections carries its own thread, powered by
[giscus](https://giscus.app) over GitHub Discussions on
[`fa11up/comp-protocol`](https://github.com/fa11up/comp-protocol/discussions).

Threads are keyed by stable terms — `infer/section-6`, `infer/appendix-c` — rather than by
heading text or URL, so they survive retitling, renumbering and a new IPFS CID.

## Deploying

Pushing to `main` pins the site and prints the new CID in the workflow summary. Updating the
ENS record is deliberately manual: automating it would mean putting a wallet key in CI, and the
wallet that controls `miyagod.eth` is not a key that belongs in a GitHub secret.

1. Push to `main`; read the CID from the Actions run summary.
2. Set the `contenthash` of `infer.miyagod.eth` to `ipfs://<CID>` at
   [app.ens.domains](https://app.ens.domains).

## Licence

Public domain. Fork freely.
