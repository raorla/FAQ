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


## 🔹 Error: Failed to Establish an Encrypted Channel to CAS

### Problem
When running a SCONE-based TEE Dapp, you might encounter the following error:
```
[SCONE|WARN] rust-cache/cargo/registry/src/github.com-1ecc6299db9ec823/rustls-0.19.1/src/session.rs:798:Sending fatal alert BadCertificate
[SCONE|FATAL] src/process/init.c:379:__scone_prepare_secure_config(): Could not initialize enclave state: Attestation failed
Caused by: Failed to establish an encrypted channel to CAS
Caused by: I/O error
Caused by: invalid certificate: UnknownIssuer 
```

### Solution  
This error happens when the image used to build the application does not match the CAS version set-up in the worker.
To solve the issue, please make sure that:
- You are building your Dapp using the latest version of the sconifier image
- You are following the instructions provided in the [documentation](https://protocol.docs.iex.ec/for-developers/confidential-computing/create-your-first-sgx-app).


## 🔹 Accessing the SCONE build tools

### Problem
You have requested access to the SCONE build tools via email but have not received a response, and the tools are not appearing on GitLab.

### Solution  
Access to the SCONE tools is typically granted within 2 to 24 hours. If you haven't received a reply after this period, it's advisable to contact the Scontain team again.


## 🔹 Unable to sconify with node v16

### Problem
Users attempting to sconify Node.js v16 encounter the following error message:
```
ERROR: Sorry, this node version is not supported!
```

### Solution  
To address the issue, ensure that you are using Node.js version 14 in your Docker file when sconifying. Scone currently supports only Node.js version 14.
 
Keep in mind that it's important to stay updated on Scone's compatibility requirements, and check for any future announcements regarding support for newer Node.js versions. This will help prevent delays and ensure a smoother development process. If you continue to face issues, consider reaching out to our support team for further assistance.


## 🔹 Buffer is not defined

### Problem
ReferenceError : "Buffer is not defined" on a vite project .

### Solution  
Configuring a polyfill for the Buffer
https://stackoverflow.com/questions/70714690/buffer-is-not-defined-in-react-vite 

## 🔹 Can I bridge RLC from a centralized exchange to The iExec Sidechain "Bellecour"?

### Problem
You are holding RLC on a centralized exchange (such as Binance, Kraken or Coinbase) and want to transfer some of your balance to iExec Sidechain “Bellecour” so you can use them with iExec, for example for requesting tasks.

### Solution  
The iExec sidechain “Bellecour” is an EVM-compatible chain that is only bridged to Ethereum Mainnet. iExec does not support direct transfers of funds from any centralized exchange to a wallet on Bellecour.
This means that to use your RLC balance on iExec Sidechain “Bellecour” you will need to first use the “Withdraw” feature of your exchange to transfer RLC to a wallet on Ethereum Mainnet, and then you can use the iExec bridge to transfer RLC from that wallet to your wallet on iExec Sidechain “Bellecour”.
