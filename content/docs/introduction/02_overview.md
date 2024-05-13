---
title: "Overview"
description: ""
summary: ""
date:
lastmod:
draft: false
weight: 102
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

Airetos solution consists of two key components:

#### Airetos Bundler

Airetos bundler is a specialized cluster contains multiple nodes that allows users to submit transactions in a bundled format (User Operation), enabling the execution of multiple operations within a single transaction.

In the Airetos, the bundler is designed to process bundled transactions that include a primary transaction (e.g., a token transfer) and one or more auxiliary transactions for additional services (e.g., KYT or KYC).

#### JavaScript SDK

A JavaScript Software Development Kit (SDK) based on Viem and Permissionless.js is provided to simplify the integration of account abstraction and the custom bundler into dApps.

The SDK abstracts away the complexities of interacting with the custom bundler, enabling developers to easily incorporate KYT, KYC, and other services into their applications.
