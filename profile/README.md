# ⚡ payload.wtf

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
| TypeScript / Node.js | [web3-sdk](https://github.com/payload-wtf/web3-sdk) | `@payload-wtf/web3` |
| Python | [python-sdk](https://github.com/payload-wtf/python-sdk) | `payload_wtf` |
| Rust | [rust-sdk](https://github.com/payload-wtf/rust-sdk) | `payload-wtf-sdk` |

---

## 🧠 Example Use Case

```ts
import { sendPayloadTransaction } from "@payload-wtf/web3";

const signature = await sendPayloadTransaction(connection, transaction, {
  tipLamports: 100_000,
  mode: "jito", // or "quicknode", "helius"
});
