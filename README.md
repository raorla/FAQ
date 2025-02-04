# Frequently Asked Questions (FAQ)

Welcome to the FAQ section. Here you'll find answers to common questions categorized for easy navigation.

## Table of Contents

- [Deployment Issues](#deployment-issues)
- [Error Messages](#error-messages)
- [Access and Permissions](#access-and-permissions)
- [Compatibility](#compatibility)
- [Configuration](#configuration)
- [Important Updates](#important-updates)
- [Language Support](#language-support)
- [General Inquiries](#general-inquiries)

---

## 🔹 Issues with deploying smart contracts on Bellecour

### Problem  
iExec Sidechain “Bellecour” is a standard EVM-based sidechain dedicated to the iExec protocol. This article lists some of the things that can go wrong when one attempts to deploy smart contracts on IExec Sidechain Bellecour.

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
}; ```

---
## Question 1

**Q: What is the purpose of this FAQ?**

**A:** This FAQ aims to provide answers to common questions about our project.
