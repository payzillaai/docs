# Pay with a pay link

A pay link is a web page where a person pays a listed service with a compatible Solana wallet. Each Marketplace listing with a pay link has its page at `https://paywith.payzilla.ai/p/<listing id>`; the Marketplace is at https://paywith.payzilla.ai/registry/.

1. Open the pay link. Before any wallet signs, the pay page checks the seller's answer against the registered price and wallet.
2. You see the price in the payment request before anything is signed.
3. Approve in your wallet. You pay that amount in USDC from your own wallet; Payzilla's fee payer pays the Solana network fee.
4. Each settled payment shows a link to its Solana transaction.

You need a Solana wallet with a little USDC. Tested by Payzilla: Phantom, Solflare, Trust Wallet and MetaMask. Use a wallet that holds only what you can afford to lose.

A Solana payment cannot be undone. Payzilla does not refund payments and does not decide disputes between a buyer and a seller. Never send a key or a seed phrase.
