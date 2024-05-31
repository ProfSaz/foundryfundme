# FundMe Contract

A sample funding contract that allows users to fund the contract based on the ETH/USD price feed. This project uses Foundry for development and testing.

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
    - [Deploy](#deploy)
    - [Test](#test)
    - [Test-Coverage](#test-coverage)
3. [Environment Variables](#environment-variables)
4. [Features](#features)
6. [Contributing](#contributing)
7. [License](#license)
8. [Contact](#contact)

## Installation

To get started, clone the repository and install the dependencies.

```bash
# Clone the repository
git clone https://github.com/ProfSaz/foundryfundme.git

# Navigate to the project directory
cd foundryfundme

# Install Foundry
curl -L https://foundry.paradigm.xyz | bash
foundryup

# Install dependencies using foundry
forge install
```

## Usage

### Deploy 

```bash

forge script script/DeployFundMe.s.sol

```

### Test

We tested accross 2 test tiers.
    1. Unit
    2. Integration 

To run a general test for this project use the following command 

```bash 

forge test

```

To run very specific test, use the matching test command with the name of the function you want to test

```bash 

forge test --mt testFunctionName

```
### Test Coverage

To check how much test coverage you have in the project 

```bash 

forge coverage

```

## Environment Variables 

This project uses environment variables to manage sensitive information. Create a `.env` file in the root directory of your project based on the provided `.env.example` file.

```bash 

PRIVATE_KEY=XXXXXXXXX
RPC_URL=http://0.0.0.0:8545
ETHERSCAN_API_KEY=XXXX

```

## Features

- Fund the Contract: Users can fund the contract based on the ETH/USD price feed.
- Withdraw Funds: Only the owner can withdraw all the funds from the contract.
- Cheaper Withdraw: An optimized method for withdrawing funds.

## Deploying to a Testnet or Mainnet 

1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file, similar to what you see in `.env.example`.

- `PRIVATE_KEY`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```bash 
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY

```

