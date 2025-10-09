 ---
# Rust Swapper — Meme Coin Swap Tool

The tool allows you to swap Solana tokens using contract addresses (CA/mint addresses) directly.  
It supports Raydium, pump.fun, Orca, etc, executes swaps on mainnet, and returns results in structured JSON.
It’s designed to run on an **AWS Windows Server 2016** instance and can be controlled via the **command line**.  
You can integrate the executable into your own **REST API**, or simply run it directly for quick testing.
 ---

 ### 🔍 Purpose 
 It allows you to execute on‑chain token swaps directly from a wallet, with **no external libraries or DLLs**.  
 All network communication uses **pure‑Rust TLS (Rustls)** — meaning no installation of *libcrypto* or *libssl* is ever needed.

 ---

 ## ⚙️ 1 | Installation

 1. Unzip the folder and rename `.env.example` to `.env`
 2. Ensure `SWAP.exe` and `.env` are in the same folder  
 3. No other dependencies are required — run directly on Windows 10/11 or Server 2016+

 ---

 ## 🔑 2 | Configure .env (next to `SWAP.exe`) with your wallet details

 ```bash
 PRIVATE_KEY=<your base58 encoded secret key
 WALLET_ADDRESS=<your 44‑character public address
 ```

 **Example:**

 ```bash
 PRIVATE_KEY=2Lbyi6kNFs8n45PGixcYMpWGfMWp5SxRcCbQb9ckWuJSxLxeL2YA5f5ap3c3ukfzh37QzLQEkxZcuFexbM9Vkf
 WALLET_ADDRESS=H7a7ZpghWGK6VhknrnvyUJeKjBcJdYZvHhDcdjSdyonB
 ```

 ⚠ **Important:** no quotes, no spaces — use the exact keys shown.  
 Your wallet must contain some **SOL** for network fees (~0.002 SOL per swap).

 ---

 ## 🧮 3 | Command Syntax

 ```bash
 SWAP <input_mint <output_mint <amount [slippage_bps] [--send <output_file]
 ```

 | Parameter | Meaning |
 |------------|----------|
 | `input_mint` | Mint (contract) address of token to swap **from** |
 | `output_mint` | Mint (contract) address of token to swap **to** |
 | `amount` | Human amount (e.g., `1.5` = 1.5 tokens) |
 | `slippage_bps` | *(Optional)* Basis points (1% = 100 bps, default = 50 bps) |
 | `--send <file` | *(Optional)* Writes transaction signature or error to file (e.g. `1.txt`) |

 ---

 ## ▶ 4 | Examples

 **Swap 1 SOL → USDC (0.5% slippage):**

 ```powershell
 SWAP So11111111111111111111111111111111111111112 EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v 1 50
 ```

 **Swap 2 WIF → BONK (1% slippage) and save Tx ID to 1.txt:**

 ```powershell
 SWAP EKpQGSJtjMFqKZ9KQanSqYXRcF8fBopzLHYxdM65zcjm DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB263 2 100 --send 1.txt
 ```

 When successful, the console prints something like:

 ```text
  Token decimals = 5; sending raw amount = 200000  
  Swap executed!  
 Transaction ID: 4QAprUN...  
  Transaction ID written to 1.txt
 ```

 Validate the transaction on [Solscan](https://solscan.io/tx/4QAprUN...).

 ---

 ## 💾 5 | Output Files

 If you pass `--send <file`, that file is created in the same folder as `SWAP.exe`  
 and contains the transaction signature:

 ```text
 4QAprUNkq9F7xVHH8seqBBaJp4JqBJ2sbXyTQ56ysoB5PDf6rbeedgzewkQPByYTXgJrvmGiVWb9QcHYvkxMVqvA
 ```

 ---

 ## 🌐 6 | Troubleshooting

 | Issue | Cause | Fix |
 |--------|--------|------|
 | `PRIVATE_KEY not set` | `.env` missing or incorrect filename | Ensure the file name is exactly `.env` and is in the same folder |
 | `No route found` | Pair has no liquidity on Jupiter | Try swapping through USDC or SOL instead |
 | `Insufficient SOL` | Wallet balance too low for fee | Add ~0.005 SOL to the wallet |
 | No DLL errors appear | Rustls TLS build is self‑contained | 🟢 All good |

 ---


 ## 💡 Next Objectives (Phase 2)

 | Goal | Description |
 |-------|--------------|
 | **1 → REST API wrapper** | Building a lightweight Actix‑web service exposing HTTP endpoints:<br• `GET /quote?input=&output=&amount=` → returns current best route.<br• `POST /swap` → receives JSON payload and performs a swap (signed with server wallet). |
 | **2 → Deployment** | Hosting the API on **AWS EC2** (Windows Server or Linux container). |
