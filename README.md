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
