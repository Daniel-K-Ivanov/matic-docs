---
id: develop
title: Build on zkEVM
sidebar_label: Build on zkEVM
description: Guide to start building on Polygon zkEVM
keywords:
  - docs
  - zk rollups
  - polygon
  - proof
  - efficiency
  - develop
  - zkEVM
image: https://matic.network/banners/matic-network-16x9.png
---

# **Build on Polygon zkEVM**

## **Introduction**

Polygon zkEVM is the first zero-knowledge scaling solution that is **fully equivalent to an EVM**. All existing smart contracts, developer toolings and wallets work seamlessly. Polygon zkEVM harnesses the power of zero-knowledge proofs in order to reduce transaction costs and massively increase throughput, all while inheriting the security of Ethereum.

Building dApps on zkEVM is completely similar to Ethereum. Simply switch to the zkEVM RPC and start building on a network with much higher throughput and lower fees. Polygon zkEVM provides a complete EVM-like experience for Developers and Users alike. So you do not need special toolings or new wallets for building or interacting with zkEVM.

:::info Reminder

You don't need special toolings or Wallets to build or interact with Polygon zkEVM.

:::

Developers will be able to deploy their existing contracts to the zkEVM, and Users can deposit assets from Ethereum and transact off-chain. These transactions are grouped into batches with zero-knowledge proof attesting to the validity of each transaction.

## **Connecting to zkEVM**

In order to add the **Polygon zkEVM** network to your wallet, you will need to enter the following details:

- **Network Name**: Polygon zkEVM Testnet
- **RPC URL**: [https://public.zkevm-test.net:2083](https://public.zkevm-test.net:2083)
- **Chain ID**: 1402
- **Currency Symbol**: ETH
- **Block Explorer URL**: [https://public.zkevm-test.net:8443](https://public.zkevm-test.net:8443)

Also, for moving assets across chains, you will need to use the zkEVM Bridge. The bridge is available on [https://public.zkevm-test.net/](https://public.zkevm-test.net/).

Check out this video tutorial on how to add Polygon zkEVM Testnet to Metamask and deploy smart contracts:

<video autoplay width="100%" height="100%" controls="true" >
  <source type="video/mp4" src="/img/zkevm/tutorial.mp4"></source>
  <p>Your browser does not support the video element.</p>
</video>
