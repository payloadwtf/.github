# ⚡ payloadwtf

**Solana transactions, tipped and turbocharged.**

`payload.wtf` is an edge-native routing layer for Solana transactions. It enables faster inclusion, priority lanes, and MEV-protected routing with zero protocol changes — just by wrapping your existing `sendTransaction` flow.

We provide lightweight SDKs to help you route transactions through the `payload.wtf` network while automatically handling tip logic, RPC lane selection, and transaction forwarding.

---

## 🚀 What is payload.wtf?

`payload.wtf` is a Solana-compatible API that:

- Accepts standard base64-encoded `sendTransaction` payloads  
- Enforces a tip-based routing policy  
- Routes transactions to high-performance RPC providers like QuickNode, Helius, or Jito  
- Drops transactions that don't meet tip thresholds  
- Logs telemetry for land rate, block inclusion rate, and tip volume  

All without changing your Solana codebase — just send to a new endpoint.

---

## 🧰 SDKs

| Language | Repo | Package |
|----------|------|---------|
| TypeScript / Node.js | [web3-sdk](https://github.com/payloadwtf/web3-sdk) | `@payload-wtf/web3` |
| Python | [python-sdk](https://github.com/payloadwtf/python-sdk) | `payload_wtf` |
| Rust | [rust-sdk](https://github.com/payloadwtf/rust-sdk) | `payload-wtf-sdk` |

---

## 🧠 Example Use Case

```ts
import { sendPayloadTransaction } from "@payload-wtf/web3";

const signature = await sendPayloadTransaction(connection, transaction, {
  tipLamports: 100_000,
  mode: "jito", // or "quicknode", "helius"
});
```

Behind the scenes, we:
- Append a `SystemProgram.transfer()` to your tip wallet
- Serialize and forward to `https://api.payload.wtf/sendTransaction`
- Return the tx signature (or drop with a 403 if tip is missing)

---

## 📈 Features

- ⚡ Edge-hosted API  
- 💸 Incentivized routing with native SOL tips  
- 🛠 Compatible with all Solana wallets + libraries  
- 🧠 Smart routing logic (QuickNode, Helius, Jito, etc.)  
- 📊 Land/block inclusion analytics (coming soon)

---

## 👷 Contributing

We welcome contributions to any of the SDKs or the core infrastructure!

- File an issue or feature request  
- Submit a PR in any language repo  
- Add test coverage or example projects

---

## 📡 Production Endpoint

```bash
POST https://api.payload.wtf/sendTransaction
Content-Type: text/plain
Body: base64-encoded signed Solana transaction
```

---

## 📜 License

MIT
