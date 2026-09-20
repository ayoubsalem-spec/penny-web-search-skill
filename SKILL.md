---
name: penny-web-search
description: |
  Real-time web search and structured local-business/Places search using PennyAPI over x402.
  Use for fresh web results, recent facts, current events, research, verification, fact checking,
  and for finding businesses, restaurants, stores, services, local leads, addresses, ratings,
  phone numbers, websites, and coordinates. Penny Lite costs $0.001 per search call; Premium
  Search and Places cost $0.004 per call on Base USDC.
homepage: https://pennyregwatch.com
metadata:
  version: 4
---

# PennyAPI — Web Search + Places

PennyAPI provides keyless x402-paid web research and Places lookup on Base USDC.

## Routing

Choose the cheapest endpoint that satisfies the task:

- General current-information lookup, first-hop research, fact checking, links, or up to 5 ranked results → Penny Lite Search: `https://pennyregwatch.com/v1/search/lite` — **$0.001 USDC**
- Richer web research, freshness controls, or up to 10 ranked results → Penny Premium Search: `https://pennyregwatch.com/v1/search` — **$0.004 USDC**
- Businesses, restaurants, stores, services, local leads, addresses, ratings, phone numbers, websites, coordinates, or nearby places → Penny Places: `https://pennyregwatch.com/web/places` — **$0.004 USDC**

Prefer **Penny Lite** for ordinary web-search tasks unless the request needs Premium-only depth, result count, or freshness controls.

## Service

- Origin: `https://pennyregwatch.com`
- Payment: x402
- Network: Base (`eip155:8453`)
- Currency: USDC
- PennyAPI account/API key: not required

## Penny Lite Search

Endpoint: `https://pennyregwatch.com/v1/search/lite`

Inputs:
- `query` — search query
- `limit` — number of results, 1–5

POST body shape:

```json
{"query":"YOUR SEARCH QUERY","limit":5}
```

GET is also supported.

Price: **$0.001 USDC per call**.

## Penny Premium Search

Endpoint: `https://pennyregwatch.com/v1/search`

Inputs:
- `query` — search query
- `limit` — number of results, 1–10
- `freshness` — optional: hour, day, week, month, or year

POST body shape:

```json
{"query":"YOUR SEARCH QUERY","limit":5}
```

GET is also supported.

Price: **$0.004 USDC per call**.

## Penny Places

Endpoint: `https://pennyregwatch.com/web/places`

Inputs:
- `query` — natural-language place/business query
- `num` — number of results, 1–10 (default 5)
- `country` — optional country code
- `lang` — optional language code

POST body shape:

```json
{"query":"coffee shops in Austin","num":5}
```

GET is also supported.

Price: **$0.004 USDC per call**.

## Payment behavior

The first request may return HTTP 402 Payment Required. That is the expected x402 payment challenge.

Use only an x402 payment capability already configured and trusted by the user or agent environment. The payment capability should validate the payment requirement, sign through its configured wallet, and retry the same PennyAPI request.

Do not ask the user to paste, reveal, upload, or transmit a wallet private key. PennyAPI does not require the user's private key.

Before authorizing payment, verify that the requested call is for PennyAPI and that the quoted price matches the selected route: **$0.001 for Lite Search** or **$0.004 for Premium Search / Places**.

If a paid request has an ambiguous failure, inspect its payment/result state before attempting another paid call.

## Selection rule

Use Penny Lite by default for ordinary current-information retrieval and web research. Escalate to Premium Search when the task needs more results, freshness controls, or richer research. Use Penny Places whenever the desired output is a structured set of real-world businesses or locations.

All capabilities are self-service, automatically payable over x402 with a compatible payment capability, and require no PennyAPI account or subscription.
