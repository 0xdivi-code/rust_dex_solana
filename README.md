### Overview
The SWAP tool allows you to swap **Solana tokens (USDC, WSOL, and supported meme coins such as WIF, BONK, and current top 10 major memes etc.)** on **Solana mainnet**.  
Designed to run on your AWS Windows 2016 server and can be controlled from the command line.  
You will integrate this binary into your own REST API, but you can also run it directly for testing.

---

## 1️⃣ Files
- `SWAP.exe` → the main executable file (you run this).  
- `wallet.json` → your Solana wallet file (private key).  
  - The swap tool uses this wallet to sign and send transactions.  

---

## 2️⃣ Requirements
- Your AWS Windows Server 2016 must have **Internet access** → the tool communicates with the Solana blockchain.  
- Your `wallet.json` must have:  
  - **SOL balance** → for paying transaction fees (~0.000005 SOL per swap).  
  - **The token you want to swap** (USDC, WSOL, WIF, etc.).  

---

## 3️⃣ How to Run (Examples)

1. **Open Command Prompt** on your Windows server.  
2. Navigate to the folder containing `SWAP.exe` and `wallet.json`:  

   ```cmd
   cd C:\path\to\folder
Run commands in the following format:
Preview swap (does NOT send to blockchain):
cmd

SWAP.exe <amount> <source_token> <target_token>
Example:

cmd

SWAP.exe 1 usdc wif
→ Shows you how much WIF you would get for 1 USDC. No trade happens.

Execute swap (sends to Solana blockchain):
cmd

SWAP.exe <amount> <source_token> <target_token> --send
Example:

cmd

SWAP.exe 1 usdc wif --send
→ Sends a live swap of 1 USDC into WIF.

Change slippage tolerance (optional)
By default, max slippage is 0.5%.
You can adjust with the --slippage option:

cmd

SWAP.exe 1 usdc wif --slippage 100 --send
→ Executes with 1% slippage tolerance.

## 4️⃣ Understanding Output
On successful swaps, the tool prints:

text

💱 Quote: 1 usdc -> 1234 wif (slippage 50 bps)
🚀 Swap sent!
   Signature: 5HMSvzLVmyRhfeaJteeVr44...
   Solscan:   https://solscan.io/tx/5HMSvzLVmyRhfeaJteeVr44...
Quote: How much output token you’ll receive (estimate).
Signature: Blockchain transaction ID.


If something goes wrong:

“Token not yet added or not tradable” → that token is not currently supported by Jupiter (no liquidity).
“Insufficient balance” → your wallet does not have enough of the input token.

## 5️⃣ Supported Tokens
Always works for USDC and WSOL (wrapped SOL).
Works for major top 10 meme coins (e.g. WIF, BONK, POPCAT, MOTHER).
If a token is too new or not yet added, the tool will tell you "Token not yet added or not tradable".

## 6️⃣ Integration with Your API
You can call SWAP.exe from your REST API backend (using system() or similar command‑execution methods).
The output is plain text or can be parsed as structured JSON, e.g.:
JSON

{
  "status": "success",
  "signature": "5HMSvzLVmyRhfeaJteeVr44...",
  "solscan": "https://solscan.io/tx/5HMSvzLVmyRhfeaJteeVr44..."
}
Your API can parse this output easily and return it to users.

🛠 Troubleshooting

1. I only have SOL, but it says "insufficient funds"
The swap tool requires WSOL (Wrapped SOL).
To wrap SOL into WSOL from Phantom wallet:
Open SOL → select “Wrap SOL” → choose amount → approve.
From the command line (if you have Solana CLI installed):
cmd
spl-token wrap 0.1

This wraps 0.1 SOL into 0.1 WSOL.

2. Where can I check if my swap succeeded?
Follow the Solscan link or Explorer link printed in the output.
Example:
text

Solscan: https://solscan.io/tx/<signature>
You will see confirmation, tokens received, and fees paid.

3. I got "Token not yet added or not tradable"
We need to use paid servies for that kind production use, i.e switching to private RPCs.
Jupiter excludes new/illiquid tokens.
Try another supported token like usdc, wsol, wif, samo, popcat.

4. Swap fails with "insufficient funds"
Check that:
Your wallet has the source token balance.
Your wallet has at least 0.01 SOL extra for transaction fees and wrapping/unwrapping.
cmd

solana balance
spl-token accounts

5. Nothing happens when I run SWAP.exe
Ensure you opened Command Prompt (cmd), not PowerShell (some syntax differs).
Ensure SWAP.exe and wallet.json are in the same folder.
Run from that folder with:
cmd

SWAP.exe 1 usdc wif
