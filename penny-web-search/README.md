# Penny Web Search Skill

Portable agent skill for using PennyAPI as a paid real-time web-search and Places provider over x402.

## What it does

This skill teaches compatible agents when and how to use PennyAPI's existing production endpoints:

- `https://pennyregwatch.com/v1/search` — real-time web search
- `https://pennyregwatch.com/web/places` — structured local-business and Places search

Current advertised price: **$0.004 USDC per call** on **Base** via **x402**.

## Safety and trust

This repository is a documentation-only agent skill. It contains no executable installer, bundled script, wallet code, dependency bootstrapper, or credential collector.

Review `SKILL.md` before enabling it in an agent environment. Use only a separately configured x402-capable wallet/payment capability that you already trust. PennyAPI never needs your wallet private key.

This skill is only a distribution artifact. It does **not** modify the PennyAPI production runtime.
