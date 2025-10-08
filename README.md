 ---
# Rust Swapper — Meme Coin Swap Tool

The tool allows you to swap Solana tokens using contract addresses (CA/mint addresses) directly.  
It supports Raydium, pump.fun, Orca, etc, executes swaps on mainnet, and returns results in structured JSON.
It’s designed to run on an **AWS Windows Server 2016** instance and can be controlled via the **command line**.  
You can integrate the executable into your own **REST API**, or simply run it directly for quick testing.
 ---

 ## ⚙️ How to Run

 ### 1. Set Up Your Environment

 Create a file named **`.env`** in the same folder as the binary:

 ```bash
 PRIVATE_KEY=<your_wallet_private_key
 WALLET_ADDRESS=<your_public_wallet_address
 ```

 Your wallet must contain:

 - A small amount of **SOL** for network fees (≈ 0.002 SOL)
 - The **input token** you plan to swap from (e.g., BONK)

 ---

 ### 2. Run from Command Line

 **Syntax:**

 ```bash
 SWAP.exe <input_mint <output_mint <amount [slippage_bps]
 ```

 | Parameter | Description |
 |------------|-------------|
 | `<input_mint` | Mint address of the token to swap **from** |
 | `<output_mint` | Mint address of the token to swap **to** |
 | `<amount` | Human-readable token amount (e.g., `5` = 5 tokens) |
 | `[slippage_bps]` | *(Optional)* Slippage tolerance in basis points — `50` = 0.5 % |

 ---

 ### Example

 Swap **50000 BONK → WIF** with **1 % slippage**:

 ```bash
 SWAP.exe DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB263 EKpQGSJtjMFqKZ9KQanSqYXRcF8fBopzLHYxdM65zcjm 50000 100
 ```

 ---

 ### Recap

 - Runs on **AWS Windows 2016**  
 - Swaps **Solana-based tokens**  
 - Controlled via **CLI** or integrated into your **API**  
 - Requires a wallet with **SOL** for fees and the **input token**
