## Create your dapp with one click (recommended)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fd1onys1us%2Fdapp-slaps&env=VITE_WEB3MODAL_PROJECT_ID&root-directory=packages%2Fapp)

## What's included ⚡

- SvelteKit app
  - Auto-generated and fully-typed ABIs using wagmi-generate
  - Web3modal connect button using wagmi-core
- Foundry contracts
  - Configured for easy multi-chain deployments

## Manual setup

1. Click "Use this template" > "Create a new repository" > "Create repository from template"
2. Clone repo (eg. `git clone https://github.com/repo_name`) and `cd <repo_name>` (replace `repo_name`)
3. Execute the setup script `sh setup.sh` (installs foundry deps, node deps, and copies env vars)
4. [Obtain a mnemonic](https://iancoleman.io/bip39/) for test accounts.
   - Set mnemonic phrase in `packages/.env`
5. [Obtain a project id for web3modal](https://cloud.walletconnect.com/sign-in).
   - Set web3modal project id in `packages/app/.env`
6. Load environment variables: `source .env && source packages/app/.env`

Your environment is ready to go! Use these commands to get started deploying a contract and start buidling.

1. Start local chain: `anvil -m $MNEMONIC`
2. Start ABI generation in separate window: `pnpm wagmi generate --watch ../contracts/broadcast/`
3. Deploy the Foo contract: `forge script Deploy --broadcast --rpc-url $FOUNDRY`
4. Start app: `pnpm -F app dev`

## Common commands

### Start local anvil chain from mnemonic

```sh
anvil -m $MNEMONIC
```

### Deploy contracts to a chain

> Note: some L2s require a `--legacy` flag if EIP-1559 is not yet supported.

```sh
forge script Deploy --broadcast --rpc-url $SEPOLIA
```

### Regenerate ABIs from Foundry

```sh
pnpm -F app wagmi-generate
```

### Automatically regenerate ABIs from Foundry deployments

```sh
pnpm wagmi generate --watch ../contracts/broadcast/
```

### Install a Foundry package

1. Start by installing the package (example: openzeppelin-contracts):

```sh
forge install OpenZeppelin/openzeppelin-contracts
```

2. Regenerate the remappings for the contract imports (run this from the project root):

```sh
forge remappings > remappings.txt
```

## Troubleshooting

- Try resetting account in MetaMask
- Try clearing all browser storage
- Try disconnecting account and reconnecting
- Ensure all env vars are set
