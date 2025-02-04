# iExec FAQ - Troubleshooting and Common Issues

## 🔹 Deployment Issues on Bellecour Sidechain

### Problem  
Deploying smart contracts on the iExec Sidechain "Bellecour" (EVM-compatible) may encounter specific errors.

### Solution  
Possible causes and fixes :
- 🕵️ **Whitelisting Required**  
  Only whitelisted wallets can deploy contracts.  
  → [Request whitelisting via support ticket]

- 🔐 **Incorrect Wallet**  
  Verify you're using your whitelisted deployment wallet.

- ⛽ **Gas Configuration**  
  - Set gas price to **0 Wei**
  - Ensure sufficient gas limit (minimum 2M recommended)

```solidity
// Example deployment configuration
const tx = {
  gasPrice: 0,
  gasLimit: 2_000_000
};
