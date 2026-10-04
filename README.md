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

The paper carries **one thread**, powered by [giscus](https://giscus.app) over GitHub Discussions
on this same repo — [`fa11up/infer-whitepaper`](https://github.com/fa11up/infer-whitepaper/discussions),
category *General*. The thread is mounted the first time the panel opens and never unmounted, so a
half-written comment survives closing the panel, scrolling the paper and coming back.

It is keyed by the stable term `infer/paper` rather than by heading text or URL, so it survives
retitling, renumbering and a new IPFS CID. Readers responding to a particular section quote it.

### If comments stop loading, check the repo before the code

The widget needs four things, and three of them live outside `index.html`:

| Requirement | Where | Current |
|---|---|---|
| `repo` / `repoId` / `categoryId` match | `index.html` | `fa11up/infer-whitepaper`, `R_kgDOU5OLCg`, `DIC_kwDOU5OLCs4DHAL2` |
| Discussions **enabled** | Settings → Features | on |
| Repo **public** | Settings | public — readers need no account |
| [giscus app](https://github.com/apps/giscus) installed | GitHub App | installed on this repo |

Check the whole chain without a browser. `Discussion not found` is the healthy answer for a term
nobody has commented on yet — giscus creates the discussion on the first comment:

```bash
curl -s "https://giscus.app/api/discussions?repo=fa11up%2Finfer-whitepaper\
&term=infer%2Fpaper&category=DIC_kwDOU5OLCs4DHAL2&strict=false&number=&first=20&last="
```

`giscus is not installed on this repository` means the app, not the config — and installing an app
is a browser authorisation that no API token can perform. That error is what you get by pointing
the widget at a repo the app was never installed on; it is how this broke once already, when
`index.html` still named `fa11up/comp-protocol` after the site moved here.

## Deploying

Pushing to `main` pins the site and prints the new CID in the workflow summary. Updating the
ENS record is deliberately manual: automating it would mean putting a wallet key in CI, and the
wallet that controls `miyagod.eth` is not a key that belongs in a GitHub secret.

1. Push to `main`; read the CID from the Actions run summary.
2. Set the `contenthash` of `infer.miyagod.eth` to `ipfs://<CID>` at
   [app.ens.domains](https://app.ens.domains).

## Licence

Public domain. Fork freely.
