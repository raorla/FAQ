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

🔐 TEE Application Errors
Error: "Failed to establish encrypted channel to CAS"
Symptom
[SCONE|FATAL] Attestation failed - Invalid certificate: UnknownIssuer

Solution

Update to latest sconifier image version

Verify CAS version compatibility with worker setup

Follow official TEE documentation

🛠️ SCONE Tools Access
Problem
No response after requesting SCONE build tools access.

Solution
Typical activation delay: 2-24 hours

No response after 24h? → Recontact Scontain team directly

📦 Node.js Compatibility
Error: "Unsupported Node v16"
Solution

Use Node.js v14 in Dockerfile

dockerfile
Copy
FROM node:14-alpine
🔧 SDK Customization
Changing Default SMS Service
javascript
Copy
const configArgs = { 
  ethProvider: window.ethereum,
  chainId: 134 
};

const configOptions = {
  smsURL: 'https://v7.sms.debug-tee-services.bellecour.iex.ec'
};

const iexec = new IExec(configArgs, configOptions);
⚠️ Critical Update: SMS Migration v8.3
Impact
Secrets created before migration will become inaccessible.

Action Required

Read official migration announcement

Follow migration guide

🐍 Python SDK Workaround
Temporary Solution
Wrap Node.js CLI in Python:

python
Copy
import subprocess

def run_iexec(command):
    try:
        result = subprocess.run(
            ['iexec'] + command,
            capture_output=True,
            text=True,
            check=True
        )
        return result.stdout
    except subprocess.CalledProcessError as e:
        print(f"Error: {e.stderr}")
        return None

# Example usage
print(run_iexec(['--version']))
🛠️ Frontend Issues
"Buffer is not defined" in Vite
Solution
Add buffer polyfill:

Install package:
npm install buffer

Configure vite.config.js:

javascript
Copy
import { defineConfig } from 'vite'
import polyfillNode from 'rollup-plugin-polyfill-node'

export default defineConfig({
  plugins: [polyfillNode()],
})
💱 RLC Transfers
Centralized Exchange → Bellecour
Process

CEX → Ethereum Mainnet (Withdraw)

Mainnet → Bellecour via iExec Bridge

⏳ Task Processing Delays
Factors Contributing to Delay

Phase	Typical Duration
Order Matching	2-3 minutes
Image Download	1-5+ minutes
SGX Attestation	1-2 minutes
Task Execution	Variable
Result Upload	1-3 minutes
Optimization Roadmap

PoCo Boost protocol upgrade

SGX attestation improvements

Multi-language worker optimization

🕸️ The Graph Integration
CORS Errors
Solution

Verify query syntax at:
https://thegraph.bellecour.iex.ec/subgraphs/name/bellecour/poco-v5

Check request headers:

http
Copy
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,POST
Common Syntax Errors
graphql
Copy
# Bad
{ orders(first: 5 where: {status: "ACTIVE"}) }

# Good
{ orders(first: 5, where: {status: "ACTIVE"}) {
  id
  status
}}
Copy

Ce format inclut :
- Une structure claire avec sommaire visuel via emojis
- Une mise en page responsive
- Des blocs de code syntaxiquement corrects
- Des tableaux pour les données structurées
- Des liens cliquables
- Une hiérarchie visuelle cohérente
- Des icônes/emoji pour le balayage rapide
- Des exemples concrets avant/après pour les erreurs courantes
