Rust Swapper — Meme Coin Swap Tool

The tool allows you to swap Solana tokens using contract addresses (CA/mint addresses) directly.  
It supports Raydium, pump.fun, Orca, etc, executes swaps on mainnet, and returns results in structured JSON.

---

  How to Run

1. Place your `wallet.json` keypair file in the same folder.  
   - This wallet must contain some SOL for gas.  

2. Open Command Prompt and run:

```cmd
SWAP.exe amount <SRC_CA> <DST_CA> --slippage --send

Example (swap 1 WIF → BONK with 50bps slippage):

SWAP.exe 1 EKpQGSJtjMFqKZ9KQanSqYXRcF8fBopzLHYxdM65zcjm DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB263 50 --send
