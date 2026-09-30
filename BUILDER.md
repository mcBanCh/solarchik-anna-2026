# BUILDER COMMAND — Solarchik Anna Edition

Paste the block below into the builder as the only task.

---

You are the builder for **Solarchik Anna Edition**.

Do this entire job in one pass. Do not ask for extra product decisions. Do not touch Solana Mobile CLOCK IN. Do not edit `mcBanCh/Solarchik`. Work only in `https://github.com/mcBanCh/solarchik-anna-2026`.

## Why this repo exists

Same product family as Solarchik, different track:

- Hackathon: Anna AI App Builder Program — https://dorahacks.io/hackathon/2349
- Deadline: 31 October 2026 (extended)
- Prize: $6,000 on DoraHacks (hackathon)
- Separate program: Anna Founding Builder Program — grants only AFTER the App is published and has Qualified App MAU. Not upfront cash. Rules: https://forum.anna.partners/t/205
- Anna said Solarchik is eligible if the submitted App is AI-native, complete, and passes App Review. Game-like / companion UX is OK. Executa is optional. Docs: https://anna.partners/developers and https://forum.anna.partners/t/build-on-anna-101/228
- Anna confirmed: keep Solana for wallets/settlement; the Anna App itself must be a complete experience.

Vadym already told Anna the secretary would stay. For THIS hackathon build Vadym changed that: drop the secretary. Prediction agents are the AI core.

## Hard isolation

- Repo: `mcBanCh/solarchik-anna-2026` only.
- Forbidden: `mcBanCh/Solarchik`, CLOCK IN, APK, MWA, Seed Vault, lastClockDay, signedDay, 1200m stamp, Seeker dApp Store.
- Forbidden to mix: Ringcheck, Stocklana, Slice tab, MunichTech-only pitch.
- You MAY read `mcBanCh/Solarchik` as reference for Work / prediction agents / catalog, then copy the needed pieces into this repo. Never commit back to that repo.

## Product for Anna (this edition only)

Solarchik is an AI companion desk inside a playable UI.

Keep:
- Roof runner / yard as the playable shell (no CLOCK IN stamp).
- Work desk with prediction agents only.
- Three single-lane NFTs: Crypto, Events, Weather.
- One combo NFT: all three lanes.
- User connects THEIR Solana wallet (Phantom / any wallet adapter). No app-generated cabinet / room key.

Remove completely from this edition:
- AI secretary / `SecretaryDesk` / call screening / Zadarma / DID.
- Cabinet / room / agent wallet (`ensureWallet`, `revealRoomSecret`, generated keypair, Devnet faucet «Поповнити»).
- Work tab «Гаманець» as a hidden built-in purse.
- Slice tab and Slice stock buys.
- Titan × Backpack / classId 2 / `sku-dex-arb` / house trading keys / IOC.
- Any UI that asks the user to paste Backpack / Titan / house secrets.

Work desk tabs after the cut:
1. Connect (user wallet only)
2. Store (buy NFT)
3. Work (run owned agents: crypto / events / weather)

No fourth tab.

## Catalog and prices

USD list prices, paid on Solana mainnet as USDC (Token-2022 or classic USDC mint used by Phantom by default: `EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`).

| SKU | Name | Lanes | Price |
| --- | --- | --- | --- |
| `sku-pred-alpha` | Bitcoin Windows | crypto | **$20 USDC** |
| `sku-pred-events` | Events Scout | events | **$20 USDC** |
| `sku-pred-weather` | Weather Station | weather | **$20 USDC** |
| `sku-combo-prime` | Combo Prime | crypto + events + weather | **$50 USDC** |

Do not sell class 2. Combo is class 3. Singles are class 1.

Show both USD and live USDC amount. Amount must be exact: 20_000_000 and 50_000_000 base units (6 decimals). No SOL price, no «free mint, chain fee only».

## Payment and unlock

Treasury (receive only, already public):

`H7zKmmnMNfnsMtib6mopdT8XsPYAyPBFuaQeWhBYTpQg`

Flow:
1. User connects own wallet. App never creates a key.
2. User taps Buy on one SKU.
3. App builds a USDC transfer from the connected wallet to the treasury.
4. Memo / reference must identify `skuId` + buyer pubkey (short memo: `solarchik:<skuId>`).
5. User signs in their wallet. App does not hold the key.
6. Watch the signature to confirmation.
7. Only after confirmed credit on that treasury address: unlock / mint the purchased NFT to the connected pubkey and persist ownership keyed by that pubkey.
8. If the tx fails, is rejected, or lands on a different address — do not unlock.
9. Same SKU can be bought again by another wallet. Same wallet buying the same SKU twice: second payment still credits Vadym; do not invent a second identical agent unless the first already exists — show «already owned» and refuse a duplicate charge.

Do not send game payments to any other address. Do not use PAY_WALLET / room key. Do not put house trading keys in this repo.

## AI-native core (required for Anna Review + Qualified App Run)

Primary value is AI reasoning on the three lanes, not a static wrapper.

Each owned NFT can run and must return a non-trivial result:
- Crypto: BTC window prediction (existing Grok/Polymarket path).
- Events: non-BTC event scout.
- Weather: station high only when a real reading exists.
- Combo: all three lanes in one NFT.

A Qualified App Run for Anna = signed-in user starts a prediction job and gets a real forecast card (side, confidence, market, why). Opening the UI does not count.

If packaging on Anna Host LLM / reverse Sampling is faster than wiring Grok, use Anna LLM for the forecast text and keep market/weather fetches as tools. Either path is fine. The run must work inside the Anna App window with loading and error states.

## Anna packaging (do in this same repo)

Follow Build on Anna 101:

- `app.json` — name Solarchik, intro, category, bundled executas if any.
- `manifest.json` — windows, permissions, Host APIs. Use `bundled:<handle>` never a hard-coded platform `tool_id`.
- `bundle/` — `index.html`, `app.js` or the compiled UI, load `anna-tool-ids.js` before app JS.
- Optional `executas/<handle>/` if you wrap prediction as Executa + reverse Sampling.
- `SKILL.md` — rewrite: no secretary. Skill is «run my Solarchik prediction desk».
- `README.md` — English submission README for judges.

CLI target:

```bash
anna-app validate --strict
anna-app dev
# later, on Vadym's machine only:
anna-app apps publish
```

Do not invent Anna account passwords. Do not publish from CI with secrets. Leave publish as a documented last step for Vadym.

If the full `anna-app` CLI is not in this environment, still land the file layout + a working web UI that can be dropped into `bundle/` so Vadym can `init`/`publish` locally.

## DoraHacks BUIDL pack (write the copy in README)

Prepare text Vadym can paste:

- Title: Solarchik
- One paragraph: AI prediction companion desk (crypto / events / weather) with a playable UI. User connects their Solana wallet, pays USDC, unlocked agent runs a real forecast.
- How AI is used: agent reasons on a lane and returns a forecast card.
- How it connects to Anna: Anna App window + Host LLM/tools + optional `#solarchik` skill.
- GitHub: this repo.
- Demo: existing https://solarchikai.grok.me/ is reference only until the Anna build is live; do not claim CLOCK IN APK as the Anna demo.
- Video: point to https://www.youtube.com/watch?v=uHePyuWP-Zk as interim; note a new Anna-window clip is still needed.

## Implementation order

1. Scaffold / replace this repo so it is an app, not a 4-file stub.
2. Port Work + catalog + prediction lanes from Solarchik reference. Strip secretary, cabinet wallet, Slice, DEX class 2.
3. Wallet adapter: connect-only. Show connected pubkey in the header.
4. Store: four SKUs, $20 / $20 / $20 / $50, pay USDC to treasury, unlock on confirm.
5. Work: only owned NFTs run. Crypto / Events / Weather (and combo).
6. Anna files + SKILL.md + validate notes.
7. README for DoraHacks + Founding Builder (grants = MAU after publish, not an invoice).

## Done when

- Secretary gone from this repo.
- No generated cabinet wallet.
- Work lanes are only crypto, events, weather.
- Buy $20 or $50 USDC → confirmed credit on `H7zKmmnMNfnsMtib6mopdT8XsPYAyPBFuaQeWhBYTpQg` → that NFT unlocks for the signer.
- A prediction run returns a real card (AI-native, not a static page).
- `mcBanCh/Solarchik` git history unchanged.
- README explains hackathon submit + Anna publish steps for Vadym.

Owner: Vadym Bilobrovets (`mcBanCh`). Do not ask for private keys.
