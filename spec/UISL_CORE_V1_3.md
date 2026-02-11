# UISL Core Specification v1.3

## Purpose
Define deterministic grammar, canonical construction rules, validation sequence, and fail-closed enforcement for UISL artifacts.

## Required Fields
UISL2  
SPEC  
POLICY  
ID  
VER  
STATUS  
AUD  
ISSUER  
LICENSE  
KEY  
TS  
CAPS  
CMD  
CHAIN  
TSA  
HASH  
SIG  

Missing required field = INVALID_SCHEMA

## Canonicalization Rule
- Strict field order
- ASCII encoding only
- Newline = \n
- No leading/trailing whitespace
- No unknown fields
- No duplicate fields

Canonical string is constructed from SPEC through TSA only.

## Validation Sequence
1. Parse structure
2. Enforce field order
3. Build canonical byte string
4. Compute SHA-256 hash
5. Verify ED25519 signature
6. Verify CHAIN pointer
7. Record to CMD (append-only)

Fail at any step = invalid artifact.
