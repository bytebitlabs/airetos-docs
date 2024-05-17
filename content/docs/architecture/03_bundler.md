---
title: "Bundler"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 203
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

The Airetos bundler consists of 3 main components:

{{< figure
  src="images/airetos_bundler.png"
  alt="Airetos bundler architecture"
  caption="Airetos bundler architecture"
>}}

## UserOperation handler
---
### Prerequisite Estimation
- This component estimates all the necessary data required to execute the UserOperation (the bundled transaction) that users send to the bundler.

- It calculates gas estimations, determines the appropriate paymaster (if applicable), and gathers any other prerequisite information.

### Validation
- The Validation component ensures that the UserOperation sent by the user adheres to the required format and meets all necessary criteria.

- It performs various checks, such as verifying the validity of the sender's account, checking the balance for gas fees, and ensuring the transactions are properly structured.

### Prescript Extraction
- This component extracts the prescript (the auxiliary transactions for requested services like KYT or KYC) from the UserOperation.

- It identifies the specific services the user wants to execute and separates them from the primary transaction.

### Bundling
After validation, the Bundling component adds the valid UserOperations to the bundler's mempool (memory pool), where they await further processing.

## ServiceProvider handler
---
### Router
The Router component analyzes the prescript data and routes it to the appropriate service adapter (e.g., KYT or KYC) based on the requested service.

### Provider adapter
Each service (KYT, KYC, or others) has a dedicated Adapter responsible for handling requests for that specific service.

- Validation
  - The Adapter's Validation component verifies the fee payment for executing the service and ensures that all required parameters are provided correctly.

- Execution
  - After validation, the Execution component calls the corresponding service provider's contract to execute the requested operation (either on-chain or off-chain, depending on the provider's implementation).

### Aggregator
The Aggregator collects and aggregates the results from multiple service executions (e.g., combining the results of KYT and KYC checks).

### Decision Maker
- Based on the aggregated results from the Aggregator, the Decision Maker component determines whether to allow the primary transaction to proceed or halt it.

  - If the aggregated result is positive (e.g., the KYT and KYC checks are successful), the primary transaction is permitted to continue.

  - If the aggregated result is negative (e.g., one or more service checks fail), the Decision Maker halts the entire bundled transaction.

## Execution handler
---
### Validation
This component validates the UserOperations received from other nodes in the network to ensure consistency and prevent potential attacks.

### ABCI (Application Blockchain Interface)
- The ABCI component facilitates communication between the bundler and the underlying consensus engine (Tendermint, in this case).

- It allows the bundler to participate in the consensus process, share valid UserOperations with other nodes, and reach an agreement on the valid block containing the UserOperations.

### Batch Execution
- The node responsible for producing the next block (the block producer) uses the Batch Execution component to send the UserOperations from its mempool to the Ethereum Virtual Machine (EVM) for execution on the blockchain.-

- This component batches multiple UserOperations together for efficient execution and includes them in the new block.


*We now have a blockchain network that generates blocks with a list of UserOperations in them.*
