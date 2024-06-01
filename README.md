# Foundry Simple Storage

This is part of the Cyfrin Updraft Solidity Blockchain Course.

*[Updraft | Foundry Simple Storage](https://updraft.cyfrin.io/courses/foundry/foundry-simple-storage/introduction-foundry-simple-storage)*

*[⭐️ YouTube (6:23:59) | Section 6 | Foundry Simple Storage](https://www.youtube.com/watch?v=umepbfKp5rI&t=22979s)*

- [Foundry Simple Storage](#foundry-simple-storage)
- [Getting Started](#getting-started)
  - [Requirements](#requirements)
    - [Optional Gitpod](#optional-gitpod)
  - [Setup](#setup)
  - [Usage](#usage)
    - [Deploying to a testnet](#deploying-to-a-testnet)
  - [zkSync instructions](#zksync-instructions)
    - [Prerequisites](#prerequisites)
    - [Run a local zkSync test node](#run-a-local-zksync-test-node)
    - [Deploy to zkSync](#deploy-to-zksync)
- [Thank you!](#thank-you)


# Getting Started

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`
  - You should also be able to run `anvil --version` and see a response like `anvil 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`


<!-- If you're installing foundry for the first time, you can put this in your `.bash_profile` or `.zshrc` depending on if you're using bash or zsh shell.

You can check which shell you are currently using by looking at the value of the SHELL environment variable or examining the current process name. Run the following command in your terminal:

```bash
echo $SHELL
```

And you'll see if you're using bash or zsh.


```bash
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
``` -->

<!-- If you are using zsh, make sure to place your configurations, aliases, and functions in the .zshrc file located in your home directory. If the file doesn't exist, you can create it with touch ~/.zshrc. -->

### Optional Gitpod

If you can't or don't want to run and install locally, you can work with this repo in Gitpod. If you do this, you can skip the `clone this repo` part.

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#github.com/PatrickAlphaC/foundry-simple-storage-f23)

## Setup

Clone this repo

```
git clone https://github.com/Cyfrin/foundry-simple-storage-f23
cd foundry-simple-storage-f23
```

## Usage

1. Setup your `anvil` chain by running the following in your terminal:

```bash
anvil
```

You'll get a large output where the ending looks something like:

```
==================

31337

Base Fee
==================

1000000000

Gas Limit
==================

30000000

Genesis Timestamp
==================

1717267365

Listening on 127.0.0.1:8545
```

2. Copy the number at the end of `Listening on XXX` and place it into your `.env` file similar to what's in `.env.example`, and add an `http://` to it.

`.env` Example:

```
RPC_URL=http://127.0.0.1:8545
```

3. Scroll up in the anvil output, and you'll see a section that looks like this:

```
Private Keys
==================

(0) 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
(1) 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d
(2) 0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a
(3) 0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6
(4) 0x47e179ec197488593b187f80a00eb0da91f1b9d0b13f8733639f19c30a34926a
(5) 0x8b3a350cf5c34c9194ca85829a2df0ec3153be0318b5e2d3348e872092edffba
(6) 0x92db14e403b83dfe3df233f83dfa3a0d7096f21ca9b0d6d6b8d88b2b4ec1564e
(7) 0x4bbbf85ce3377467afe5d46f804f221813b2bb87f24d81f60f1fcdbf7cbf4356
(8) 0xdbda1821b80551c9d65939329250298aa3472ba22feea921c0cf5d620ea67b97
(9) 0x2a871d0798f97d79848a013d4936a73bf4cc922c825d33c1cf7073dff6d409c6

Wallet
==================
Mnemonic:          test test test test test test test test test test test junk
Derivation path:   m/44'/60'/0'/0/
```

Grab the top key and place it into your `.env`. 

`.env` Example:

PRIVATE_KEY=11ee3108a03081fe260ecdc106554d09d9d1209bcafd46942b10e02943effc4a

4. Compile your code

Run

```
forge compile
```

5. Deploy your contract

```
forge create SimpleStorage --private-key <PRIVATE_KEY>
```


### Deploying to a testnet

Make sure you have a [metamask](https://metamask.io/) or other wallet, and export the private key.

**IMPORTANT**

USE A METAMASK THAT DOESNT HAVE ANY REAL FUNDS IN IT. Just in case you accidentally push your private key to a public place. I _highly_ recommend you use a different metamask or wallet when developing.

1. [Export your private key](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key), and place it in your `.env` file. DO NOT USE A KEY ASSOCIATED WITH REAL FUNDS. If you plan to, follow the instructions laid out in this section:
   1. [Never use a .env again](https://updraft.cyfrin.io/courses/foundry/foundry-simple-storage/never-use-a-env-file)
   2. [Or this one](https://www.youtube.com/watch?v=VQe7cIpaE54)
2. Go to [Alchemy](https://alchemy.com/?a=673c802981) and create a new project on the testnet of choice (ie, Sepolia)
3. Grab your URL associated with the testnet, and place it into your `.env` file.
4. Make sure you have [testnet ETH](https://faucets.chain.link/) in your account. You can [get some here](https://faucets.chain.link/). You should get testnet ETH for the same testnet that you made a project in Alchemy (ie, Sepolia)
5. Run

```bash
forge create SimpleStorage --private-key <PRIVATE_KEY> --rpc-url <ALCHEMY_URL>
```

Or, you can use a deploy script!

```bash
forge script script/DeploySimpleStorage.s.sol --private-key <PRIVATE_KEY> --rpc-url <ALCHEMY_URL>
```

## zkSync instructions

### Prerequisites
- [foundry-zksync](https://github.com/matter-labs/foundry-zksync)
  - You'll know you've done it right if you can run `forge-zksync --version` and you see a response like `forge-zksync 0.0.2 (816e00b 2023-03-16T00:05:26.396218Z)`
- [docker](https://docs.docker.com/engine/install/)
  - You'll know you've done it right if you can run `docker --version` and you see a response like `Docker version 20.10.7, build f0df350`
- [nodejs & npm](https://nodejs.org/en/download/package-manager)
  - You'll know you've done it right if you can run `node --version` and you see a response like `v14.17.0`
  - Additionally, you'll know you've done it right if you can run `npm --version` and you see a response like `6.14.13`


### Run a local zkSync test node

1. Setup the config

```bash
npx zksync-cli dev config 
```

Select `in-memory node` and no additional plugins.

2. Run the node

```bash
npx zksync-cli dev start
```

If you get an error like: `Command exited with code 1: Error response from daemon: dial unix docker.raw.sock: connect: connection refused`, this means docker is not running. 

### Deploy to zkSync

```bash
forge create src/SimpleStorage.sol:SimpleStorage --rpc-url  http://127.0.0.1:8011 --private-key xxx --legacy --zksync
```

or

```
forge script script/DeploySimpleStorage.s.sol --private-key xxx --rpc-url http://127.0.0.1:8011 --legacy --zksync --broadcast
```

# Thank you!

If you appreciated this, feel free to follow me or donate!

ETH/zkSync/Arbitrum/Optimism/etc Address: `cyfrin1.eth`: 0x3846c3A30E62075Fa916216b35EF04B8F53931f6 (Confirm the ENS matches the address!)

[![Patrick Collins Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/PatrickAlphaC)
[![Patrick Collins YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/channel/UCn-3f8tw_E1jZvhuHatROwA)
[![Patrick Collins Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/patrickalphac/)
[![Patrick Collins Medium](https://img.shields.io/badge/Medium-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@patrick.collins_58673/)
