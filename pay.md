# How to pay with Payzilla

Early. Real money. Use with caution. A Solana payment cannot be undone.

Pick the route that fits you. Each one pays a Marketplace listing in USDC on Solana.

| I am... | Use | Start here |
|---|---|---|
| a person with a wallet | a pay link | [pay-link.md](pay-link.md) |
| running an AI assistant | the payer tool | below |
| a developer building an agent | MCP or x402 | [mcp.md](mcp.md) |

## Let your AI assistant pay (the payer)

The payer gives your assistant a small wallet of its own. You put in a little USDC, set a cap per payment, and the assistant can pay verified Marketplace listings up to that cap. The key stays in your computer's keychain; Payzilla never sees it. The tool is free. You pay only the listing's price (from 0.01 USDC). Payzilla pays the network fee today.

You need Node.js 24 or newer, git, and an assistant that runs local MCP servers (tested with Claude Code on macOS).

1. **Get the code, pinned to the release.**
   ```bash
   git clone --branch v0.1.0 https://github.com/payzillaai/payer.git ~/payer && cd ~/payer
   npm ci --omit=dev --ignore-scripts
   ```
   git may print `is not a commit`; that is the annotated tag and is harmless.
2. **Make the small wallet.** It shows only an address; the key goes into the keychain.
   ```bash
   node src/small-wallet.ts init
   ```
3. **Fund it a little.** From your own wallet, send that address a small amount of USDC on Solana. For a first try, 0.20 USDC is enough. No SOL is needed to pay. Check the address before you send.
4. **Set the cap per payment.** The default is 0.50 USDC and the most is 10.
   ```bash
   node src/server.ts cap 0.10
   ```
5. **Connect your assistant.** Add the Marketplace (to find listings) and the payer (to pay).
   ```bash
   claude mcp add --transport http payzilla https://paywith.payzilla.ai/mcp/read
   claude mcp add payzilla-payer --scope user -- node "$HOME/payer/src/server.ts"
   ```
   If a server called `payzilla-payer` already exists, use another name, or start a clean session with only these two servers: put them in a file and run `claude --strict-mcp-config --mcp-config <file>`.
6. **Ask it to pay.** For example: "Find the Payzilla listing 'Test Payzilla with a real donation' and pay it." (0.10 USDC, a real donation to Payzilla.) Your assistant may ask you to approve the `pay_listing` tool the first time. That is expected.
7. **Check.** The answer is `settled` with a transaction. Look it up on a Solana explorer. Your small wallet's balance drops by the price.

When you are done: `node src/small-wallet.ts address` shows the balance, `withdraw <address> <USDC>` sends it out, and `remove` deletes the key (it refuses while USDC is left).

We ran these steps ourselves on 29 October 2026 with 0.05 USDC: the assistant paid our 0.01 USDC test listing, finalized on Solana. Our own test, not customer traffic.

## What protects you, and what does not

Only the small balance, the cap you set (at most 10 USDC), a limit of 10 payments an hour, and Payzilla's service limits (10 USDC per payment, 100 USDC a day for everyone). These are safety nets, not guarantees. An assistant can pay without asking each time and can be misled by listing text. Put in only what you are ready to lose.

Full details, other systems and the safety text: [the payer README](https://github.com/payzillaai/payer) and [Install the payer](https://payzilla.ai/for-agents/install/).
