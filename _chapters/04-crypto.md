---
title: Cryptography
---

# Cryptography

```ascii
┌────────────────────────────────────────────────┐
│                                                │
│                                                │
│                                                │
│                                                │
│                     ┌────┐                     │
│                     │ VM │                     │
│                     └────┘                     │
│                                                │
│                                                │
│                                                │
│                                                │
│                      VPC                       │
└────────────────────────────────────────────────┘
┌──────┐                                          
│Crypto│                                          
└──────┘                                          
```

A Cryptography (Crypto) service provides a way to create, import and rotate an unguessable key for encrypting data, and provides a way to get and audit access to the key for decrypting data.

We need Crypto to encrypt sensitive data like VM and application secrets so no 3rd party, including the provider itself, can read it in plain-text.

Crypto is a stand-alone service.
