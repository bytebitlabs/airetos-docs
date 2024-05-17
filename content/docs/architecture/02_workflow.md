---
title: "Workflow"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 202
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

The Airetos follows this general workflow:

## KYT enabled workflow

{{< figure
  src="images/airetos_kyt_workflow.png"
  alt="Airetos workflow for a KYT enabled transaction"
  caption="Airetos workflow for a KYT enabled transaction"
>}}

### dApp
---
#### Initialization
- The dApp developer can choose to either integrate the Metamask Snap or directly use the Airetos JavaScript SDK provided by the platform.

- When a user initiates a transaction, the dApp creates a bundled transaction that includes the primary transaction (e.g., a token transfer) and a prescript, which internally is an auxiliary transaction for the requested KYT service.

- The bundled transaction is then submitted to the Airetos bundler.

### Airetos bundler
---
#### Validation and Service Execution
- Upon receiving the KYT-enabled bundled transaction, the bundler validates the KYT requirements, such as ensuring sufficient fees and the availability of the requested service provider.

- If the validation is successful, the bundler calls the target KYT service provider to execute the KYT request.
#### Result Handling
- The KYT service provider performs the requested checks and returns the result to the bundler.

- Based on the KYT result, the bundler takes one of the following actions:

  - If the KYT result is positive (i.e., the transaction is deemed safe), the bundler allows the primary transaction to proceed and adds it to the transaction pool for execution.

  - If the KYT result is negative (i.e., the transaction is deemed unsafe), the bundler halts the entire bundled transaction and refunds the KYT service fee to the user.

### KYT service provider
---
#### Request Execution:
- When the KYT service provider contract receives a KYT request from the bundler, it executes the requested checks or operations.

- These checks can be performed on-chain or off-chain, depending on the specific service provider's implementation.

- After completing the checks, the service provider returns the KYT result (positive or negative) to the bundler.

### Blockchain
---
#### SmartAccount Contract Execution
- If the KYT result is positive and the bundler allows the primary transaction to proceed, the SmartAccount contract (enabled by account abstraction) executes the bundled transaction.
- The bundled transaction includes two transactions:

  - The first transaction is for paying the KYT service fee via the Service Governance Platform (SGP) platform.

  - The second transaction is the original transaction initiated by the user (e.g., the token transfer).

#### Fee Distribution
After executing the bundled transaction, the SGP platform distributes the collected KYT service fee according to the predetermined fee distribution mechanism. This may involve allocating portions of the fee to the service provider, the platform's treasury, and a token buyback program for the Airetos native token.
