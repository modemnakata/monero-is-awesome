# Monero (XMR) — The Complete Onboarding & Advocacy Hub

> **Private. Secure. Untraceable. Digital cash that works like cash.**

This repository is a comprehensive resource for understanding, using, and advocating for Monero — the world's leading privacy-focused cryptocurrency.

---

## 🎯 Why Monero? (TL;DR)

| Feature | Monero | Bitcoin | Traditional Banking |
|---------|--------|---------|---------------------|
| **Privacy by Default** | ✅ Mandatory | ❌ Transparent | ❌ Full surveillance |
| **Fungibility** | ✅ 1 XMR = 1 XMR always | ❌ Tainted coins exist | ❌ Frozen/seized funds |
| **Decentralization** | ✅ ASIC-resistant, CPU/GPU mining | ⚠️ Mining centralization | ❌ Central authority |
| **Scalability** | ✅ Dynamic block size | ❌ Fixed block size | ✅ But centralized |
| **Development** | ✅ Community-funded, no pre-mine | ✅ But corporate influence | ❌ Profit-driven |

**Bottom line:** Monero is the only major cryptocurrency where every transaction is private by default, every coin is fungible, and no one — not governments, not corporations, not chain analysis firms — can track your financial activity.

---

## 🚀 Quick Start: Get Monero in 5 Minutes

### 1. Get a Wallet (Choose One)

| Platform | Recommended Wallets | Best For |
|----------|---------------------|----------|
| **Desktop** | [Feather Wallet](https://featherwallet.org/) • [Monero GUI](https://www.getmonero.org/downloads/) | Daily use, full control |
| **Mobile** | [Monerujo](https://monerujo.io/) (Android) • [Cake Wallet](https://cakewallet.com/) (iOS/Android) | On-the-go payments |
| **Hardware** | [Trezor Model T](https://trezor.io/model-t/) • [Ledger](https://www.ledger.com/) + Monero app | Large holdings, cold storage |
| **CLI/Power Users** | `monero-wallet-cli` • `monero-wallet-rpc` | Automation, servers, advanced |

### 2. Buy Monero (No KYC Options)

| Method | Privacy Level | Speed | Notes |
|--------|---------------|-------|-------|
| **DEX / Atomic Swaps** | ⭐⭐⭐⭐⭐ | Minutes | [Trocador](https://trocador.app/), [BasicSwap](https://basicswapdex.com/), [UnstoppableSwap](https://github.com/comit-network/unstoppableswap) |
| **P2P / Local** | ⭐⭐⭐⭐ | Hours | [LocalMonero](https://localmonero.co/) (RIP), [HodlHodl](https://hodlhodl.com/), [Bisq](https://bisq.network/) |
| **No-KYC Exchanges** | ⭐⭐⭐ | Minutes | [TradeOgre](https://tradeogre.com/), [XMR.to](https://xmr.to/) (BTC→XMR), [SideShift](https://sideshift.ai/) |
| **KYC Exchanges** | ⭐ | Minutes | Kraken, Binance (delisting in some regions), KuCoin — *withdraw to your own wallet immediately* |

### 3. Receive Your First XMR

```
1. Open your wallet → "Receive"
2. Copy your **primary address** (starts with 4 or 8) or generate a **subaddress** (recommended for each sender)
3. Share with sender
4. Wait for 10 confirmations (~20 minutes) for full finality
```

---

## 📚 Core Concepts — Understand What You're Using

### Privacy Triad: How Monero Achieves Anonymity

```
┌─────────────────────────────────────────────────────────────┐
│                    MONERO TRANSACTION                       │
├─────────────────────────────────────────────────────────────┤
│  🔒 RING SIGNATURES (RingCT)                                │
│     → Hides the SENDER among a ring of decoys (16 rings)   │
│     → Proves you own funds without revealing which one     │
├─────────────────────────────────────────────────────────────┤
│  🔒 STEALTH ADDRESSES                                       │
│     → Hides the RECEIVER                                    │
│     → One-time address per transaction, unlinkable         │
│     → Only sender/receiver know destination                │
├─────────────────────────────────────────────────────────────┤
│  🔒 RING CONFIDENTIAL TRANSACTIONS (RingCT)                 │
│     → Hides the AMOUNT                                      │
│     → Commitments prove inputs = outputs without revealing │
│     → Implemented Jan 2017 (block 1220516)                 │
└─────────────────────────────────────────────────────────────┘
```

### Key Technical Specs

| Parameter | Value |
|-----------|-------|
| **Algorithm** | RandomX (CPU-optimized, ASIC-resistant) |
| **Block Time** | ~2 minutes |
| **Block Size** | Dynamic (median of last 100 blocks × 2) |
| **Supply** | ~18.4M XMR (tail emission: 0.6 XMR/block forever) |
| **Emission** | Smooth, no halving cliffs |
| **Ring Size** | 16 (fixed since v0.17) |
| **Address Format** | Base58 (mainnet: 4*/8*, testnet: 5*/9*) |

### Subaddresses & Integrated Addresses

```bash
# Primary address (don't reuse for different parties)
44AFFq5kSiGBoZ4NMDwYtN18obc8AemS33DBLWs3H7otXft3XjrpDtQGv7SqSsaBYBb98uNbr2VBBEt7f2wfn3RVGQBEP3A

# Subaddress (generate one per contact/service - unlinkable!)
86y7g... (starts with 8)

# Integrated address (address + payment ID combined - legacy, use subaddresses instead)
44AFF... + payment_id → single string
```

---

## 🛡️ OpSec Guide: Stay Private

### Wallet Hygiene
- ✅ **Use subaddresses** for every distinct counterparty
- ✅ **Never reuse addresses** — generate new subaddress per exchange, friend, service
- ✅ **Churn your funds** (send to yourself via multiple hops) if you received from KYC source
- ✅ **Run your own node** — don't leak your IP/view keys to remote nodes
- ✅ **Use Tor/I2P** — `monerod --tx-proxy=tor,127.0.0.1:9050`

### Node Setup (Maximum Privacy)

```bash
# 1. Install Monero
# Linux: sudo pacman -S monero / apt install monero / dnf install monero
# macOS: brew install monero
# Windows: Download from getmonero.org

# 2. Run over Tor (install tor first)
monerod --tx-proxy=tor,127.0.0.1:9050 --add-priority-node=zwt6vcp6d5tao4lv.onion

# 3. Or run as hidden service (receive inbound connections)
# /etc/tor/torrc:
# HiddenServiceDir /var/lib/tor/monero/
# HiddenServicePort 18080 127.0.0.1:18080
# HiddenServicePort 18089 127.0.0.1:18089

# 4. Connect wallet to your node
# Feather: Settings → Node → Remote Node → 127.0.0.1:18089
# CLI: monero-wallet-cli --daemon-address 127.0.0.1:18089
```

### Hardware Wallet + Monero
```bash
# Ledger: Install Monero app via Ledger Live → Connect to Feather/CLI
# Trezor Model T: Native support in Feather, Monero GUI, CLI
# Always verify address on device screen before confirming!
```

---

## 💡 Why People Should Use Monero

### For Individuals
- **Financial privacy is a human right** — your spending habits are nobody's business
- **Protection from discrimination** — medical purchases, political donations, adult content, legal but stigmatized goods
- **Fungibility guarantee** — your XMR can never be "tainted" or refused by merchants
- **No account freezes** — no bank can block your transaction
- **Borderless** — send any amount, anywhere, 24/7/365

### For Merchants
- **No chargebacks** — final settlement in ~20 minutes
- **Lower fees** — typically <$0.01, no percentage cuts
- **No PCI compliance** — you don't handle sensitive customer data
- **Global reach** — anyone with internet can pay
- **Privacy for customers** — competitive advantage

### For Activists / Journalists / NGOs
- **Censorship resistance** — no one can block donations
- **Source protection** — donors remain anonymous
- **Operational security** — funding trails don't expose networks
- **Proven track record** — used by WikiLeaks, Tor Project, Tails, etc.

### For Developers
- **Rich ecosystem** — RPC, ZMQ, WebSockets, multiple languages
- **No smart contract risk** — simple, audited, battle-tested codebase
- **Active community** — 500+ contributors, regular audits
- **Research-friendly** — cutting-edge cryptography (Bulletproofs+, Seraphis, FCMP++)

---

## 🔗 Essential Links Collection

### Official Resources
- 🌐 **Website:** <https://www.getmonero.org/>
- 📖 **User Guides:** <https://www.getmonero.org/resources/user-guides/>
- 🛠️ **Developer Docs:** <https://www.getmonero.org/resources/developer-guides/>
- 📝 **Whitepapers:** <https://www.getmonero.org/resources/research-lab/>
- 💬 **Community:** <https://www.getmonero.org/community/hangouts/>
- 🐛 **Bug Bounty:** <https://www.getmonero.org/community/bounties/>

### Wallets (Verified & Audited)
| Wallet | Platform | Type | Audited |
|--------|----------|------|---------|
| [Feather](https://featherwallet.org/) | Linux/macOS/Windows | Lightweight, Tor, multisig | ✅ |
| [Monero GUI](https://www.getmonero.org/downloads/) | All desktop | Official reference | ✅ |
| [Monerujo](https://monerujo.io/) | Android | Feature-rich, node control | ✅ |
| [Cake Wallet](https://cakewallet.com/) | iOS/Android | Multi-coin, swap built-in | ✅ |
| [Stack Wallet](https://stackwallet.app/) | Mobile/Desktop | New, clean UX | ✅ |
| [Trezor](https://trezor.io/model-t/) | Hardware | Cold storage | ✅ |
| [Ledger](https://www.ledger.com/) | Hardware | Cold storage | ✅ |

### Block Explorers (No JS, Tor-friendly)
- <https://xmrchain.net/> — Clean, detailed
- <https://moneroblocks.info/> — Minimal, fast
- <https://explorer.btc.xmr.pm/> — Onion: `xmrpm7q3v5zr.onion`
- <https://localmonero.co/blocks> — P2P marketplace blocks

### Exchange Aggregators (No KYC)
- <https://trocador.app/> — **Best overall**, compares 20+ exchanges, Tor, no JS
- <https://sideshift.ai/> — Fixed rate, email optional
- <https://xmr.to/> — BTC → XMR only
- <https://majesticbank.ch/> — EUR/CHF bank transfer → XMR
- <https://unstoppableswap.com/> — BTC ↔ XMR atomic swaps

### P2P / DEX
- <https://bisq.network/> — Decentralized exchange (BTC/XMR, fiat/XMR)
- <https://hodlhodl.com/> — P2P, multisig escrow, no KYC
- <https://peachbitcoin.com/> — Lightning → XMR (new)
- <https://basicswapdex.com/> — Cross-chain DEX

### Community & Learning
- **Reddit:** r/Monero, r/xmrtrader, r/MoneroMining
- **Matrix/IRC:** #monero:matrix.org, #monero on Libera.Chat
- **Twitter/X:** [@monero](https://twitter.com/monero), [@fluffypony](https://twitter.com/fluffypony)
- **YouTube:** [Monero Talk](https://www.youtube.com/c/MoneroTalk), [XMR Tutorials](https://www.youtube.com/@xmrtutorials)
- **Podcasts:** Monero Talk, Monero Standard, Delving Bitcoin (Monero eps)
- **Research:** [MRL Papers](https://www.getmonero.org/resources/research-lab/), [Breaking Monero](https://breakingmonero.com/) (attack analysis)

### Merchant Directories
- <https://moneroworld.com/map/> — Global map of merchants
- <https://acceptmonero.com/> — Curated list
- <https://monero-forum.com/> — Marketplace section
- <https://www.coinmap.org/> — Filter by Monero
- <https://xmrlist.com/> — Hand-reviewed directory of businesses that accept Monero, with user reviews and scam warnings [Added 2026-11-04]

---

## ⛏️ Mining Monero (Support the Network)

### Why Mine?
- Secures the network
- Earn XMR directly (no KYC)
- Learn how the protocol works
- It's profitable on efficient CPUs

### Quick Start (Linux)
```bash
# 1. Install XMRig (best miner)
# Download from https://github.com/xmrig/xmrig/releases

# 2. Configure (config.json)
{
  "pools": [
    {
      "url": "pool.supportxmr.com:3333",
      "user": "YOUR_WALLET_ADDRESS",
      "pass": "worker1",
      "tls": true,
      "keepalive": true
    }
  ],
  "randomx": { "mode": "auto", "1gb-pages": true },
  "cpu": { "enabled": true, "huge-pages": true, "hw-aes": null }
}

# 3. Run
./xmrig --config=config.json
```

### Recommended Pools (Decentralize!)
| Pool | Fee | Min Payout | Tor |
|------|-----|------------|-----|
| [SupportXMR](https://supportxmr.com/) | 0.6% | 0.0004 XMR | ✅ |
| [MoneroOcean](https://moneroocean.stream/) | 0% | 0.003 XMR | ✅ |
| [P2Pool](https://p2pool.io/) | 0% | PPLNS | ✅ **Most decentralized** |
| [Gupax](https://github.com/monero-ecosystem/gupax) | 0% | P2Pool GUI | ✅ |

### Hardware Recommendations (2024)
| CPU | Hashrate (RandomX) | Efficiency |
|-----|-------------------|------------|
| Ryzen 9 7950X | ~19 kH/s | ~35 W/kH |
| Ryzen 9 5950X | ~17 kH/s | ~40 W/kH |
| Threadripper 3970X | ~35 kH/s | ~30 W/kH |
| EPYC 7742 (64c) | ~45 kH/s | ~28 W/kH |
| i9-13900K | ~14 kH/s | ~55 W/kH |

> **Pro tip:** Enable 1GB huge pages in BIOS/OS for 5-15% boost. P2Pool solo mining = zero trust, full decentralization.

---

## 🔬 Advanced Topics

### View Keys — Audit Without Spending
```bash
# Private view key (share with auditor/accountant)
# Allows seeing INCOMING transactions only
# Cannot spend, cannot see outgoing, cannot see balance changes from spends

# Public view key (in address)
# Used by sender to create stealth address
```

### Multisig (2-of-3, 3-of-5, etc.)
- **Feather Wallet:** Native multisig wizard
- **CLI:** `multisig_import_needed`, `multisig_sign`
- Use cases: Treasury management, escrow, shared custody

### Atomic Swaps (Trustless Cross-Chain)
- **BTC ↔ XMR:** [UnstoppableSwap](https://github.com/comit-network/unstoppableswap), [BasicSwap](https://basicswapdex.com/)
- **ETH ↔ XMR:** In development (Seraphis/FCMP++ will enable)
- No wrapped tokens, no bridges, no custodians

### Seraphis / FCMP++ (Coming Upgrade)
- **Seraphis:** New transaction protocol — smaller txs, better UX, forward secrecy
- **FCMP++ (Full Chain Membership Proofs):** Removes ring signatures entirely
  - No more ring size limits
  - No decoy selection issues
  - Quantum-resistant (with curve changes)
  - **This is the endgame for Monero privacy**

---

## 📊 Monero vs. "Privacy Coins" Comparison

| Coin | Privacy Model | Default? | Fungible? | Dev Funding | Audit Status |
|------|---------------|----------|-----------|-------------|--------------|
| **Monero (XMR)** | RingCT + Stealth + Ring Sigs | ✅ Yes | ✅ Yes | Community (CCS) | ✅ Multiple |
| Zcash (ZEC) | zk-SNARKs (shielded pool) | ❌ Opt-in | ⚠️ Transparent pool exists | Company (ECC) | ✅ |
| Dash (DASH) | CoinJoin (PrivateSend) | ❌ Opt-in | ❌ Mixed/Unmixed | Treasury | ⚠️ |
| Pirate Chain (ARRR) | zk-SNARKs (mandatory) | ✅ Yes | ✅ Yes | Community | ⚠️ |
| Secret (SCRT) | SGX + CosmWasm | ❌ Opt-in | ⚠️ | Foundation | ⚠️ |

**Monero is the only one with: mandatory privacy + proven fungibility + no trusted setup + community governance + 10+ year track record.**

---

## 🗣️ Talking Points: How to Explain Monero

### To a Normie
> "Imagine digital cash that works exactly like physical cash — you hand it over, nobody knows who gave it to whom, and the recipient can spend it freely without anyone questioning where it came from. That's Monero. Bitcoin is like a glass bank vault where everyone sees every transaction forever. Monero is an opaque vault."

### To a Bitcoiner
> "Bitcoin has a privacy bug that will never be fixed at the base layer. Lightning helps but adds trust assumptions. Monero fixed privacy at layer 1 in 2017 with RingCT. Every XMR is fungible. No taint analysis possible. No chain analysis company can trace it. It's what Bitcoin *should have been*."

### To a Regulator / Compliance Person
> "Monero complies with the *spirit* of financial privacy laws — the right to private transactions. It doesn't comply with *surveillance* requirements. Exchanges can still do KYC on on/off ramps. The protocol itself is neutral technology, like encryption. Banning it bans financial privacy for everyone."

### To a Developer
> "RandomX makes mining actually decentralized. Tail emission secures the chain forever without fee markets. The codebase is clean C++17, well-documented RPC, multiple client implementations. No smart contract attack surface. The cryptography is peer-reviewed by academics. It's engineering over marketing."

---

## 🎨 Memes & Culture (For Sharing)

```
"Monero: Because your coffee purchase shouldn't be a matter of public record."

"Bitcoin: Don't trust, verify.
 Monero: Don't trust, verify *privately*."

"Fungibility isn't a feature. It's the absence of a bug."

"Ring size 16. Because 11 wasn't paranoid enough."

"Tail emission: The only monetary policy that admits security costs money."

"Your keys, your coins. Your node, your rules. Your privacy, your right."
```

---

## 🤝 Contributing to This Repo

This is a living document. PRs welcome for:
- Updated links / dead link fixes
- New wallet / exchange / service reviews
- Translations (see `/translations/`)
- OpSec improvements
- Merchant additions
- Technical corrections

### Style Guide
- **No fluff** — practical, actionable, verified
- **No shilling other coins** — this is Monero-only
- **Cite sources** — link to official docs, audits, research
- **Tor/onion links** — preferred for explorers/services
- **Date your additions** — `[Added 2024-01-15]`

---

## ⚖️ Disclaimer

> **This repository is for educational and informational purposes only.**
> 
> Monero is a decentralized, open-source protocol. No single entity controls it. This repo represents community knowledge, not official guidance. Always verify addresses, check signatures, test with small amounts first, and **do your own research**.
> 
> **Legal:** Monero is legal in most jurisdictions. Some exchanges have delisted it due to regulatory pressure. This does not make Monero illegal — it makes those exchanges non-private. Check your local laws.
> 
> **Tax:** In most countries, crypto-to-crypto trades and spending are taxable events. Consult a tax professional. Monero's privacy doesn't exempt you from tax obligations — it protects your financial data from *unauthorized* access.

---

## 📜 License

**CC0 1.0 Universal (Public Domain Dedication)**

To the extent possible under law, the authors have waived all copyright and related rights to this work. Use it, copy it, modify it, distribute it — freely.

> *"Privacy is necessary for an open society in the electronic age. Privacy is not secrecy. A private matter is something one doesn't want the whole world to know, but a secret matter is something one doesn't want anybody to know. Privacy is the power to selectively reveal oneself to the world."* — **Cypherpunk Manifesto, Eric Hughes, 1993**

---

**🔗 Short URL for sharing:** `https://github.com/modemnakata/monero-is-awesome`

**⭐ Star this repo if it helped you — helps others find it.**

---

*Last updated: 2024 | Maintained by the Monero community*
