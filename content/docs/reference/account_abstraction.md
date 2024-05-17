---
title: "Account Abstraction"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 901
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Account abstraction is a concept in Ethereum and blockchain technology that aims to improve the usability and flexibility of user accounts. In the traditional Ethereum account model, there are two types of accounts: Externally Owned Accounts (EOAs) controlled by private keys, and Contract Accounts, which are smart contracts deployed on the blockchain.

Account abstraction introduces a more generalized account model that allows for different types of accounts beyond the traditional EOA and contract accounts. The key idea is to separate the authentication mechanism (how an account is controlled) from the execution layer (how an account's code is executed).

With account abstraction, accounts can have associated code (like smart contracts) that defines custom authentication schemes and execution rules. This code can be executed before or after transactions, enabling features like:

1. **Multi-signature wallets**:
Accounts can require multiple signatures or approvals before executing transactions.

2. **Account recovery mechanisms**:
Accounts can have built-in recovery mechanisms in case the private key is lost or compromised.

3. **Programmable access control**: Accounts can implement custom access control logic, such as whitelisting or time-based restrictions.

4. **Batched transactions**: Multiple transactions can be batched and executed together, potentially saving gas costs.

5. **Programmable execution logic**: Accounts can have custom execution logic, enabling features like subscriptions, recurring payments, or complex financial instruments.

## Further reading

- Read [the gentle guide](https://ethereum.org/en/roadmap/account-abstraction/) on the Ethereum blockchain.
