# Penny Web Search Skill

Portable agent skill for using PennyAPI as a paid real-time web-search and Places provider over x402.

## What it does

This skill teaches compatible agents when and how to use PennyAPI's existing production endpoints:

- `https://pennyregwatch.com/v1/search/lite` — low-cost real-time web search, up to 5 results — **$0.001 USDC**
- `https://pennyregwatch.com/v1/search` — premium real-time web search with freshness controls, up to 10 results — **$0.004 USDC**
- `https://pennyregwatch.com/web/places` — structured local-business and Places search — **$0.004 USDC**

All routes settle on **Base** via **x402**. No PennyAPI account or API key is required.

The skill prefers Lite for ordinary web-search tasks and escalates to Premium only when the agent needs Premium-only depth, result count, or freshness controls.

## Safety and trust

This repository is a documentation-only agent skill. It contains no executable installer, bundled script, wallet code, dependency bootstrapper, or credential collector.

Review `SKILL.md` before enabling it in an agent environment. Use only a separately configured x402-capable wallet/payment capability that you already trust. PennyAPI never needs your wallet private key.

This skill is only a distribution artifact. It does **not** modify the PennyAPI production runtime.
