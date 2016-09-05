---
title: Cryptography
class: Security
---

A Cryptography (Crypto) service provides a way to create, import and rotate an unguessable key, and to audit access to the key.

We need Crypto to encrypt sensitive data like Instance and application secrets so no 3rd party, including the provider itself, can read it in plain-text.

Crypto is a stand-alone service.

```
┌──────────┐
│┌────────┐│
││Instance││
│└────────┘│
│   VPC    │
└──────────┘
  ┌──────┐  
  │Crypto│  
  └──────┘  
 ```