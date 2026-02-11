# UISL Architecture Overview

## Deterministic Validation Architecture

UISL enforces a layered, mandatory validation pipeline:

1. Structural Parsing  
2. Field Order Enforcement  
3. Canonical Byte Construction  
4. SHA-256 Hash Verification  
5. ED25519 Signature Verification  
6. Chain Continuity Verification  
7. Custody Recording (CMD)

Failure at any stage results in invalidation.

Validation is fail-closed.

---

## Core Components

### 1. Grammar Layer
Strict required fields. No unknown keys. No duplicates.

### 2. Canonicalization Layer
Deterministic byte construction from ordered fields.

### 3. Cryptographic Layer
SHA-256 for integrity.  
ED25519 for authority.

### 4. Continuity Layer
Append-only chain referencing prior artifact hash.

### 5. Custody Layer (CMD)
Append-only ledger preserving validation state and continuity history.

---

## Design Principles

- Deterministic
- Reproducible
- Append-only
- Fail-closed
- Drift-resistant
- Platform-agnostic

UISL does not depend on external enforcement.  
Validity is derived from deterministic structure and cryptographic proof.
