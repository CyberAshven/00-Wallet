# 00 Wallet

Self-custody crypto wallet & privacy suite — no servers, no accounts, runs in your browser.

**Live:** [0penw0rld.com](https://0penw0rld.com)

---

## Features

### Wallet
BIP44 HD wallet (`m/44'/145'/0'`) supporting BCH, Stealth BCH, BTC, ETH, XMR, USDC, USDT. Seed backup, multiple profiles, Ledger hardware support, UTXO coin control, gap-limit scanning.

### Chat
Split-knowledge encrypted messaging. Messages are XOR-split into two halves — one embedded on-chain via OP_RETURN, one sent through Nostr ephemeral events. Each half is encrypted with X25519 ECDH + AES-256-GCM. Neither the blockchain nor the relay can read the message alone.

### Stealth BCH
ECDH stealth payments — one-time addresses derived from X25519 key exchange so every payment is unlinkable on-chain. Combined with 6-phase CoinJoin mixing coordinated over Nostr.

### Onion Payments
Multi-hop stealth payments using HTLC contracts and onion-routed paths. Payments are relayed through intermediary nodes — no direct link between sender and recipient. Coordinated via Nostr.

### Swap
Atomic cross-chain swaps (BCH ↔ BTC, BCH ↔ XMR) with on-chain HTLC contracts. Peer-to-peer OTC orderbook published on Nostr.

### DEX
Cauldron DEX integration — on-chain BCH token swaps with liquidity pools.

### Loan
Moria Protocol integration — borrow MUSD stablecoins using BCH as collateral. On-chain, decentralized, no intermediary.

### Vault
Stealth multisig vaults using MuSig2 — multi-party signing with key aggregation. Vault state synced over Nostr.

### Mesh
Nostr-based social network — posts, DMs, relay management, contact discovery.

### Identity
Sovereign decentralized ID — Nostr keypair as identity, publishable profile card with BCH address, stealth code, and vault pubkey.

### Fusion
CashFusion-style CoinJoin coordinated over Nostr. Multiple wallets combine inputs and outputs into a single transaction — breaks the tx graph with no central coordinator.

---

## Tech Stack

- **Pure HTML/CSS/JS** — no framework, no build step, no bundler
- **PWA** — installable, offline-first via Service Worker
- **Desktop-first** — sidebar navigation at 900px+
- **`@noble/curves`** — secp256k1, X25519, ed25519, Schnorr
- **`@noble/hashes`** — SHA-256, RIPEMD-160, HMAC, PBKDF2, keccak
- **Fulcrum ElectrumX** — blockchain queries over WebSocket
- **Nostr relays** — coordination, notifications, social, sync
- **Monero-ts** — XMR wallet scanning & atomic swap support
- **WalletConnect v2** — optional ETH wallet connection

All crypto dependencies loaded at runtime via [esm.sh](https://esm.sh) — zero server-side code.

---

## Run

Open [0penw0rld.com](https://0penw0rld.com) in a browser. That's it.

Or serve `landing/` locally:
```bash
npx serve landing
```

---

## Structure

```
landing/
  index.html        Dashboard
  wallet.html       Wallet + Unlock
  pay.html          Payment Terminal
  swap.html         Atomic Swaps
  swap-xmr.html     XMR Swaps
  dex.html          Cauldron DEX
  loan.html         Moria Lending
  chat.html         Encrypted Chat
  onion.html        Onion Payments
  vault.html        Stealth Multisig
  id.html           Identity
  mesh.html         Nostr Social
  fusion.html       CoinJoin
  config.html       Settings
  docs.html         Documentation
  desktop.css       Desktop layout
  shell.js          Shared sidebar
  sw.js             Service Worker
  lib/              Monero WASM
  icons/            Coin & PWA icons
```

---

## License

MIT
