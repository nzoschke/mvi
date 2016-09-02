---
title: Cryptography
---

A Cryptography (Crypto) service provides a way to create, import and rotate an unguessable key, and to audit access to the key.

We need Crypto to encrypt sensitive data like application secrets so no 3rd party, including the provider itself, can read it in plain-text.

Crypto is a stand-alone service.

```
           http                 
  ┌─────────▽──────────┐        
┌─┤   Load Balancer    ├───────┐
│ └────────────────────┘       │
│┌──────────┐┌──────────┐      │
││ ┏━━━━━┓  ││ ┏━━━━━┓  │      │
││ ┃web 1┃  ││ ┃web 2┃  │      │
││ ┗━━━━━┛  ││ ┗━━━━━┛  │      │
││Instance 1││Instance 2│      │
│└──────────┘└──────────┘      │
│┌──────────────────────┐      │
││  Shared File System  │      │
│└──────────────────────┘      │
│             VPC              │
└──────────────────────────────┘
┌────────┐┌────────┐┌──────────┐
│Registry││KV Store││Blob Store│
└────────┘└────────┘└──────────┘
```