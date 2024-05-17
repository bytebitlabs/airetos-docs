---
title: "Techstack"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 201
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Airetos comprises three main layers, each serving a distinct purpose and leveraging various technologies and components. The tech stack is designed to facilitate the integration of extensible services, such as KYT and KYC, into blockchain transactions while maintaining a modular and extensible architecture.

{{< figure
  src="images/airetos_techstack.png"
  alt="Airetos techstack consists of 3 main layers"
  caption="Airetos techstack consists of 3 main layers"
>}}

## dApp layer
---
The dApp layer encompasses the user-facing components and the tools necessary for seamless interaction with the core protocol.

### Metamask Snap
Metamask Snap is a technology that allows developers to extend the functionality of the popular Metamask wallet. In Airetos' powered dApp, a custom Metamask Snap is implemented to facilitate the integration of account abstraction and the custom bundler.

The Metamask Snap provides a user-friendly interface for interacting with smart contract-based accounts, enabling features such as KYT and KYC checks before executing transactions.

### Airetos JavaScript SDK
The JavaScript SDK is a crucial component that simplifies the integration of account abstraction and the custom bundler into decentralized applications (dApps).

Key features of the SDK include:

- **Bundler Interface**:
Exposes functions for creating bundled transactions, submitting them to the custom bundler, and retrieving transaction statuses.

- **Account Abstraction Layer**:
Handles the creation and management of smart contract-based accounts with custom logic.

- **Transaction Composition**:
Responsible for composing bundled transactions by combining the primary transaction with prescript which contains auxiliary transactions (e.g., KYT, KYC, or other services) for requested services.

## Core Airetos layer
---
The core protocol layer encompasses the cluster of bundler nodes and service providers that power the extensible services functionality.

### Custom Bundler
The custom bundler is a cluster of nodes first target the EVM compatible blockchains. Its primary function is to process bundled transactions, which consist of a primary transaction (e.g., a token transfer) and one or more auxiliary transactions for additional services (e.g., KYT or KYC).

The custom bundler includes the following key components:
- **Bundler Logic**: Handles the processing of bundled transactions, executing auxiliary transactions, and determining whether to proceed with the primary transaction based on the results.

- **Service Provider Registry**: Maintains a registry of approved service providers for KYT, KYC, and other services.

- **Transaction Pool**: Incoming bundled transactions are added to a queue for processing in a fair and secure manner.

- **Batching and Caching**: Implements batching and caching mechanisms to improve performance and efficiency.

### Service Providers
Service providers are smart contracts that offer specific services, such as KYT, KYC, or other compliance-related or value-added services. These providers are integrated into the core protocol and can be called by the custom bundler to execute auxiliary transactions.

Service providers must adhere to established standards and guidelines, ensuring data privacy, security, and compliance with relevant regulations.

## Blockchain layer
---
The blockchain layer encompasses the foundational components that enable account abstraction and the deployment of the core protocol on the Ethereum blockchain.

### Smart Account contract
The Smart Account Contract is a core component of the account abstraction technology. It enables the creation of smart contract-based accounts with custom logic, allowing for the enforcement of KYT, KYC, or other checks before executing transactions.

### Service Governance Platform (SGP)
Service Governance Platform (SGP) is a platform that simplifies the deployment and management of smart contracts on the EVM compatible blockchains. SGP plays a crucial role in Airetos network by facilitating service provider registration, fee management, and ensuring the trustworthiness and liveness of service providers.
