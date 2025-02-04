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
- **Whitelisting Required**  
  Only whitelisted wallets can deploy contracts.  
  → [Request whitelisting via support ticket](https://iexecproject.atlassian.net/servicedesk/customer/portal/4/group/9/create/66)

- **Incorrect Wallet**  
  Verify you're using your whitelisted deployment wallet.

- **Gas Configuration**  
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
To solve the issue, configure a polyfill for Buffer by following this guide:  
[Buffer polyfill on StackOverflow](https://stackoverflow.com/questions/70714690/buffer-is-not-defined-in-react-vite)

## 🔹 Can I bridge RLC from a centralized exchange to The iExec Sidechain "Bellecour"?

### Problem
You are holding RLC on a centralized exchange (such as Binance, Kraken or Coinbase) and want to transfer some of your balance to iExec Sidechain “Bellecour” so you can use them with iExec, for example for requesting tasks.

### Solution  
The iExec sidechain “Bellecour” is an EVM-compatible chain that is only bridged to Ethereum Mainnet. iExec does not support direct transfers of funds from any centralized exchange to a wallet on Bellecour.
This means that to use your RLC balance on iExec Sidechain “Bellecour” you will need to first use the “Withdraw” feature of your exchange to transfer RLC to a wallet on Ethereum Mainnet, and then you can use the iExec bridge to transfer RLC from that wallet to your wallet on iExec Sidechain “Bellecour”.


## 🔹 CORS errors with The Graph

### Problem
The subgraph often responds with a CORS error, even though the actual issue might be something different, such as an invalid query or syntax errors in requests with The Graph.
```
Access to fetch at "x" from origin "y" has been blocked by CORS policy: Response to preflight request doesn't pass access control check:It does not have http ok status.
The GraphQL net::ERR_FAILED
```

### Solution  
Verify the syntax before further analysis, such as checking for missing curly braces, you can directly test the query on the following URL: [thegraph.bellecour.iex.ec](https://thegraph.bellecour.iex.ec/subgraphs/name/bellecour/poco-v5). This will allow you to quickly identify syntax errors.


## 🔹 Task processing is too long

### Problem
Users have reported a prolonged task processing time, with a minimum of 5 minutes, when working with the iExec Protocol.

### Solution  
**Explaination** 
-Order Matching: The system needs to meticulously match orders, considering various parameters, to ensure accuracy in task allocation.
-Docker Image Download: Retrieving the necessary Docker image for task execution is a critical step, and the time taken depends on the image size and network conditions.
-SGX Attestation Verification: Security is paramount, and the Dapp verifies the SGX attestation with Intel to ensure the integrity of the execution environment.
-Task Execution: The actual execution of the task involves complex computations, and the time taken is influenced by the nature and complexity of the task.
-Result Uploading: Once the task is executed, the results are uploaded, which can take time based on the size of the data and network conditions.
You can learn more about the task statuses in our documentation

**Future improvements** 
We acknowledge the concerns regarding the extended processing time and want our users to know that we are actively working on optimizing the performance of the iExec Protocol. Here are some aspects we are currently addressing:
-PoCo Boost - On-Chain Protocol Optimization:
We're optimizing our on-chain protocol with PoCo Boost to reduce transactions and lower gas usage per deal. This aims to significantly improve transaction speed and cost-effectiveness.
-Intel Collaboration and Research:
Constant collaboration with Intel includes in-depth research to enhance SGX attestation processes, ensuring a more secure and efficient iExec Protocol.
-Language Benchmarking:
We're benchmarking worker processes across different code languages, aiming to identify the most efficient ones for specific tasks. This optimization contributes to overall Protocol performance.


