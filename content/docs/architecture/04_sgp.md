---
title: "Service Governance Platform"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 204
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

The Airetos Service Governance Platform (SGP), in simple terms, is a set of smart contracts deployed on EVM compatible blockchains that serve the following purposes:

{{< figure
  src="images/airetos_sgp.png"
  alt="Airetos Service Governance Platform"
  caption="Airetos Service Governance Platform"
>}}

## Fee management
---
- This component manages the fee tokens accepted by the platform for executing services.

- Administrators can register, enable, or disable various tokens (e.g., USDT, USDC, DAI, ETH) as accepted fee tokens.

- Users need to pay the execution fee (specified by the service provider) for the services they add to the prescript.

## Service management
---
- This component handles the registration and staking process for service providers.

- Service providers can register their offered services and specify the corresponding execution fees (e.g., KYC - 1 USDT).

- To prove their trustworthiness and commitment, service providers are required to lock up a specified amount of the Airetos native token as a stake. A slashing mechanism is in place to penalize service providers who provide harmful or unreliable services.

## Treasury management
---
- The Treasury Management component is responsible for distributing the collected fees and managing the staking and slashing mechanisms.

- It distributes a portion of the total fees received from users to the respective service providers as compensation for their services.

- Additionally, the Treasury Management component can allocate funds for a token buyback program, where a portion of the fees is used to purchase and burn the Airetos native token, thereby increasing its scarcity and value.
