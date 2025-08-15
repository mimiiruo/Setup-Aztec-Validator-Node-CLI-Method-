# Setup-Aztec-Validator-Node-CLI-Method-
# First Step: For Existing Sequencer Node Operators

If you are already running a Sequencer Node:
1. Reattach to your existing screen session:
  
screen -r aztec
2. Stop your current node by pressing Ctrl + C
3. Follow the installation steps below
4. Skip the "Start Screen Session" part - use your existing screen

If you are NOT running a Sequencer Node:
- Follow all steps including creating a new screen session

---

## Step 1: Install Dependencies
wget https://raw.githubusercontent.com/ezlabsnodes/autoinstall/main/depedency-lite.sh && chmod +x depedency-lite.sh && sudo ./depedency-lite.sh
## Step 2: Install Aztec (Individual Commands)

### Command 1: Download and run Aztec installer
bash -i <(curl -s https://install.aztec.network)
### Command 2: Add Aztec to PATH
echo 'export PATH=$PATH:/root/.aztec/bin' >> ~/.bashrc
### Command 3: Reload bash profile
source ~/.bashrc
### Command 4: Start Aztec with specific version
aztec-up -v 1.2.1
### Instructions:
- Run each command one at a time
- Wait for each command to complete before running the next one
- After Command 1, you might need to restart your terminal or run source ~/.bashrc if the aztec command isn't recognized
- Command 4 will download and set up the Aztec version 1.2.1

## Step 3: CLI Node Setup

### Start Screen Session (Skip if already have one)
screen -S aztec
Note: Skip this step if you already have an existing screen session from a previous sequencer setup.

### Run Aztec Validator Node
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL \
  --l1-consensus-host-urls CONSENSUS_HOST_URL \
  --sequencer.validatorPrivateKeys 0xPrivateKey \
  --sequencer.coinbase 0xPublicAddress \
  --p2p.p2pIp IP \
  --sequencer.governanceProposerPayload 0x54F7fe24E349993b363A5Fa1bccdAe2589D5E5Ef
## Required Configuration Changes

Replace the following placeholders with your actual values:

- RPC_URL → Your Sepolia RPC URL
- CONSENSUS_HOST_URL → Your Beacon RPC URL  
- 0xPrivateKey → Your wallet's private key
- 0xPublicAddress → Your wallet address
- IP → Your VPS public IP address

## Screen Management

### Detach from Screen
- Press: Ctrl + A, then D

### Reattach to Screen
screen -r aztec
## Important Notes

- Make sure you have valid Sepolia RPC and Beacon RPC URLs
- Keep your private key secure and never share it
- The governance payload 0x54F7fe24E349993b363A5Fa1bccdAe2589D5E5Ef is fixed for this version
- Your node will need time to sync initially

## Getting RPC URLs

You can get free RPC URLs from:
- [Alchemy](https://www.alchemy.com)
- [Infura](https://infura.io)
- [QuickNode](https://quicknode.com)
- [Ankr](https://ankr.com)

Make sure you have both:
- Sepolia RPC URL (for L1 transactions)
- Beacon Chain RPC URL (for consensus)
