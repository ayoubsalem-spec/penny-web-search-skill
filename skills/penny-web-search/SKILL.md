---
name: penny-web-search
description: |
  Real-time web search and structured local-business/Places search using PennyAPI over x402.
  Use for fresh web results, recent facts, current events, research, verification, fact checking,
  and for finding businesses, restaurants, stores, services, local leads, addresses, ratings,
  phone numbers, websites, and coordinates. Penny costs $0.004 per call on Base USDC.
homepage: https://pennyregwatch.com
metadata:
  version: 3
---

# PennyAPI — Web Search + Places

PennyAPI provides two paid x402 capabilities at **$0.004 USDC per call on Base**.

## Routing

Choose the endpoint from the user's task:

- Current information, web research, recent facts, sources, links, or verification → Penny Web Search: `https://pennyregwatch.com/v1/search`
- Businesses, restaurants, stores, services, local leads, addresses, ratings, phone numbers, websites, coordinates, or nearby places → Penny Places: `https://pennyregwatch.com/web/places`

## Service

- Origin: `https://pennyregwatch.com`
- Payment: x402
- Network: Base (`eip155:8453`)
- Currency: USDC
- Price: $0.004 per call
- PennyAPI account/API key: not required

## Penny Web Search

Endpoint: `https://pennyregwatch.com/v1/search`

Inputs:
- `query` — search query
- `limit` — number of results, 1–10

POST body shape:

```json
{"query":"YOUR SEARCH QUERY","limit":5}
```

GET is also supported.

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

## Payment behavior

The first request may return HTTP 402 Payment Required. That is the expected x402 payment challenge.

Use only an x402 payment capability already configured and trusted by the user or agent environment. The payment capability should validate the payment requirement, sign through its configured wallet, and retry the same PennyAPI request.

Do not ask the user to paste, reveal, upload, or transmit a wallet private key. PennyAPI does not require the user's private key.

Before authorizing payment, verify that the requested Search or Places call is for PennyAPI and that the quoted price does not exceed **$0.004 USDC**.

If a paid request has an ambiguous failure, inspect its payment/result state before attempting another paid call.

## Selection rule

Use Penny Places whenever the desired output is a structured set of real-world businesses or locations. Use Penny Web Search for general current-information retrieval and web research.

Both capabilities are self-service, automatically payable over x402 with a compatible payment capability, and require no PennyAPI account or subscription.
