# 🛡️ Setup Aztec Validator Node (CLI Method)

## 🔄 First Step: For Existing Sequencer Node Operators

### If you are already running a Sequencer Node:
1. **Reattach to your existing screen session**:
   ```bash
   screen -r aztec
   ```
2. **Stop your current node** by pressing `Ctrl + C`
3. **Follow the installation steps below**
4. **Skip the "Start Screen Session" part** - use your existing screen

### If you are NOT running a Sequencer Node:
- Follow all steps including creating a new screen session

---

## 🚀 Installation Steps

### Step 1: Install Dependencies
```bash
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-lite.sh && chmod +x depedency-lite.sh && sudo ./depedency-lite.sh
```

### Step 2: Install Aztec (Individual Commands)

#### Command 1: Download and run Aztec installer
```bash
bash -i <(curl -s https://install.aztec.network)
```

#### Command 2: Add Aztec to PATH
```bash
echo 'export PATH=$PATH:/root/.aztec/bin' >> ~/.bashrc
```

#### Command 3: Reload bash profile
```bash
source ~/.bashrc
```

#### Command 4: Start Aztec with specific version
```bash
aztec-up -v 1.2.1
```

### ⚠️ Important Instructions:
- **Run each command one at a time**
- **Wait for each command to complete** before running the next one
- **After Command 1**, you might need to restart your terminal or run `source ~/.bashrc` if the aztec command isn't recognized
- **Command 4** will download and set up the Aztec version 1.2.1

---

## 🖥️ CLI Node Setup

### Step 3: Start Screen Session (Skip if already have one)
```bash
screen -S aztec
```
> **Note**: Skip this step if you already have an existing screen session from a previous sequencer setup.

### Step 4: Run Aztec Validator Node
```bash
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL \
  --l1-consensus-host-urls CONSENSUS_HOST_URL \
  --sequencer.validatorPrivateKeys 0xPrivateKey \
  --sequencer.coinbase 0xPublicAddress \
  --p2p.p2pIp IP \
  --sequencer.governanceProposerPayload 0x54F7fe24E349993b363A5Fa1bccdAe2589D5E5Ef
```

---

## 🔧 Required Configuration Changes

Replace the following placeholders with your actual values:

| Placeholder | Replace With | Description |
|-------------|--------------|-------------|
| `RPC_URL` | Your Sepolia RPC URL | Ethereum Sepolia testnet RPC endpoint |
| `CONSENSUS_HOST_URL` | Your Beacon RPC URL | Ethereum Beacon Chain RPC endpoint |
| `0xPrivateKey` | Your wallet's private key | Your EVM wallet private key (with 0x prefix) |
| `0xPublicAddress` | Your wallet address | Your EVM wallet public address |
| `IP` | Your VPS public IP address | Get with: `curl ifconfig.me` |

### 🔒 Fixed Parameters:
- **Governance Payload**: `0x54F7fe24E349993b363A5Fa1bccdAe2589D5E5Ef` (fixed for this version)
- **Network**: `alpha-testnet`
- **Version**: `1.2.1`

---

## 📱 Screen Management

### Detach from Screen
```bash
# Press: Ctrl + A, then D
```

### Reattach to Screen
```bash
screen -r aztec
```

### Check Screen Sessions
```bash
screen -ls
```

---

## 🌐 Getting RPC URLs

You can get **free RPC URLs** from these providers:

| Provider | Website | Notes |
|----------|---------|--------|
| **Alchemy** | [alchemy.com](https://www.alchemy.com) | Recommended, generous free tier |
| **Infura** | [infura.io](https://infura.io) | Popular choice, reliable |
| **QuickNode** | [quicknode.com](https://quicknode.com) | Fast performance |
| **Ankr** | [ankr.com](https://ankr.com) | Decentralized option |

### Required RPC Types:
- ✅ **Sepolia RPC URL** (for L1 transactions)
- ✅ **Beacon Chain RPC URL** (for consensus)

---

## ⚠️ Important Notes

- 🔐 **Keep your private key secure** and never share it
- ⏳ **Your node will need time to sync** initially
- 🔄 **Make sure you have valid** Sepolia RPC and Beacon RPC URLs
- 📊 **Monitor your node status** regularly
- 💾 **The governance payload is fixed** for version 1.2.1

---

## 🔧 Useful Commands

| Command | Description |
|---------|-------------|
| `screen -ls` | List all screen sessions |
| `screen -r aztec` | Reattach to Aztec screen |
| `Ctrl + A + D` | Detach from screen session |
| `curl ifconfig.me` | Get your external IP |
| `aztec -h` | Show Aztec help menu |

---

## 🆘 Troubleshooting

### Common Issues:

1. **Aztec command not found**:
   ```bash
   source ~/.bashrc
   # or restart terminal
   ```

2. **Node not syncing**:
   - Check your RPC URLs are working
   - Verify your IP address is correct
   - Ensure firewall allows necessary ports

3. **Screen session lost**:
   ```bash
   screen -ls  # Check existing sessions
   screen -S aztec  # Create new session if needed
   ```

4. **Private key format error**:
   - Ensure your private key starts with `0x`
   - Check there are no extra spaces

---

## 📋 Pre-Flight Checklist

Before starting your validator node:

- [ ] Dependencies installed
- [ ] Aztec CLI installed and in PATH
- [ ] Valid Sepolia RPC URL
- [ ] Valid Beacon Chain RPC URL
- [ ] Private key ready (with 0x prefix)
- [ ] Public wallet address ready
- [ ] External IP address obtained
- [ ] Screen session created/available

---

*Guide created by FasoNodez*
