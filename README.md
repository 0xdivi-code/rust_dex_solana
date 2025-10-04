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
