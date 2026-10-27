# Sell a service

Get paid in USDC for your web service. Add your service and its price, set your wallet, get your API key. Start at https://start.payzilla.ai (sign-in emails you a code).

## Four steps to your first payment
1. **Sign in with your email** in the start app at start.payzilla.ai, with an email code.
2. **Set your receiving wallet by signing a message.** Your first wallet is your main wallet and cannot be changed. You can add more, up to 5 in all.
3. **Get your API key.** Your code sends only the service id; Payzilla takes the price from the service.
4. **Fund your receiving wallet once.** Before your first payment, send 0.01 USDC to your receiving wallet from another wallet so it can receive USDC; payments are refused until then.

## What a paid call looks like
Your server answers 402 with the price set on your service, the buyer pays, you answer 200.

```
1 GET /weather/current
2 Your server asks Payzilla for a payment (the service id)
3 402 Payment Required   PAYMENT-REQUIRED: <price, who gets paid>
4 GET /weather/current   PAYMENT-SIGNATURE: <signed payment>
5 200 OK                 after Payzilla has settled it
```

API base address: `https://api-mainnet.payzilla.ai`. Send your API key in a header named `x-api-key`. Reference: https://payzilla.ai/developers/

## Marketplace and pay link
- Tick "List in the registry" and the service appears in the Marketplace within about a minute, labelled Unverified, once you have a receiving wallet on Solana mainnet. Remove it at any time.
- Tick "Allow a pay link" and a person can pay it with a compatible Solana wallet, currently up to 5 USDC a payment by default. Your service must be an x402 endpoint on an https web address (a name, not an IP address).

Up to 20 services for now. Nothing is charged yet. Payzilla does not check what you sell. Today the money goes from the buyer's wallet to yours.
