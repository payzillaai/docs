# Payzilla docs

Payzilla lets agents and people pay for web services in USDC on Solana, from their own wallet, over x402. Sellers list a service, set a price and get paid to their own wallet.

Website: https://payzilla.ai · Developers: https://payzilla.ai/developers/ · Terms and Privacy: read them on payzilla.ai before you pay or sell.

## What is live today

| Part | State | Note |
|---|---|---|
| x402 payments | Live | An agent asks a service for something, gets a price (HTTP 402), signs a payment from its own wallet and asks again. |
| MCP tools and MCP payments | Live | `https://paywith.payzilla.ai/mcp`, with small limits. See [mcp.md](mcp.md). |
| Marketplace | Live | So far only Payzilla's own listings. Payzilla does not vouch for listings; Verified means Payzilla added its own mark, not a check of the seller. |
| Pay links | Live | A person pays a listed service from a web page with a compatible Solana wallet. See [pay-link.md](pay-link.md). |
| Selling | Live | Sign in at start.payzilla.ai, set your wallet, get your API key. See [sell.md](sell.md). |
| Cards | Mock only | The card rail uses a mock card provider. |
| Agent protocols (UCP, ACP, AP2, A2A) | None live | Watching, nothing built. |

## What does not change
- Your agent or wallet signs with its own key. Payzilla never asks for a key or a seed phrase.
- A Solana transaction cannot be undone.
- Today the money goes from the buyer's wallet to the seller's wallet.
- Limits are small to start. Nothing is charged yet.

## In this repo
- [mcp.md](mcp.md): the MCP server, its four tools and limits
- [sell.md](sell.md): list a service and get paid
- [pay-link.md](pay-link.md): how a person pays with a pay link

Examples: https://github.com/payzillaai/examples

Questions or problems: write to the address on payzilla.ai with the transaction link and what happened.

## License
MIT. See [LICENSE](LICENSE).
