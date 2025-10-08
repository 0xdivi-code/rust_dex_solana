<<<<<<< HEAD
 ---
 #  SWAP Tool — Solana Token Swapper
=======
Rust Swapper — Meme Coin Swap Tool

The tool allows you to swap Solana tokens using contract addresses (CA/mint addresses) directly.  
It supports Raydium, pump.fun, Orca, etc, executes swaps on mainnet, and returns results in structured JSON.
>>>>>>> 2acfe64879b0de149d0c1c7633cbe299e1b39961

 ### Overview

<<<<<<< HEAD
 The **SWAP Tool** allows you to easily exchange **Solana tokens** — including **USDC**, **WSOL**, and popular meme coins such as **WIF**, **BONK**, and many others — directly on the **Solana mainnet**.  

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

=======
  How to Run

1. Place your `wallet.json` keypair file in the same folder.  
   - This wallet must contain some SOL for gas.  

2. Open Command Prompt and run:

```cmd
SWAP.exe amount <SRC_CA> <DST_CA> --slippage --send
```
```cmd
Example (swap 1 WIF → BONK with 50bps slippage):
```
```cmd
SWAP.exe 1 EKpQGSJtjMFqKZ9KQanSqYXRcF8fBopzLHYxdM65zcjm DezXAZ8z7PnrnRJjz3wXBoRgixCa6xjnB7YaB1pPB263 50 --send
```
# Create a Solana Wallet Using the Solana CLI

A quick guide to setting up a Solana wallet from scratch using the official **Solana Command Line Interface (CLI)**.

---

##  1. Install the Solana CLI

Run the following command in your terminal:

```bash
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
```

Verify the installation:

```bash
solana --version
```

---

##  2. Generate a New Wallet (Keypair)

Create a new keypair file:

```bash
solana-keygen new --outfile ~/.config/solana/wallet.json
```

- Follow the prompts to **save your seed phrase** (your recovery phrase).
- The file `wallet.json` contains your **private key**—keep it secret and secure.

---

##  3. Set Your Wallet as the Default

```bash
solana config set --keypair ~/.config/solana/wallet.json
```

---

##  4. Choose a Cluster (Network)

Set your environment to the **Devnet** (a testing network):

```bash
solana config set --url https://api.devnet.solana.com
```

**Common networks:**
- Devnet: `https://api.devnet.solana.com`
- Mainnet: `https://api.mainnet-beta.solana.com`

---

##  5. Check Configuration

```bash
solana config get
```

This will display your current network, keypair path, and commitment level.

---

##  6. View Your Wallet Address and Balance

```bash
solana address
solana balance
```

---

##  7. (Optional) Get Some Devnet SOL

Use this to request free test tokens:

```bash
solana airdrop 2
```

*(Only works on Devnet.)*

---
>>>>>>> 2acfe64879b0de149d0c1c7633cbe299e1b39961
