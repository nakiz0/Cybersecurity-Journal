# SHA (Secure Hash Algorithm)

## Introduction

SHA (Secure Hash Algorithm) is a family of cryptographic hash functions used to generate a unique fixed-length output called a hash or digest.

Unlike encryption:

```text
Encryption = Reversible

Hashing = One-Way
```

Hash functions cannot be decrypted back into their original form.

SHA is primarily used for:

- Data Integrity
- Digital Signatures
- Password Verification
- Certificates
- Blockchain
- Malware Analysis
- Digital Forensics

---

# What is Hashing?

Hashing converts data of any size into a fixed-size output.

## Example

```text
Input:

Hello World

↓

SHA-256

↓

a591a6d40bf420404a011733cfb7b190...
```

Regardless of input size:

```text
1 Byte
1 KB
1 GB
1 TB
```

SHA always produces the same output size for a given algorithm.

---

# Properties of Secure Hash Functions

## Deterministic

The same input always produces the same hash.

### Example

```text
Hello

↓

SHA-256

↓

Same Hash Every Time
```

---

## One-Way Function

The original input cannot be recovered from the hash.

### Example

```text
Password

↓

SHA-256

↓

Hash
```

Cannot reverse the process.

---

## Avalanche Effect

A tiny change produces a completely different hash.

### Example

```text
Hello
```

and

```text
hello
```

generate completely different outputs.

---

## Collision Resistance

It should be extremely difficult to find:

```text
Input A ≠ Input B

but

Hash A = Hash B
```

---

## Fast Computation

Hashes should be generated quickly.

---

# SHA Family Overview

## SHA-0

Released:

```text
1993
```

Status:

```text
Deprecated
```

---

## SHA-1

Released:

```text
1995
```

Status:

```text
Broken
```

---

## SHA-2 Family

Released:

```text
2001
```

Includes:

- SHA-224
- SHA-256
- SHA-384
- SHA-512

Status:

```text
Industry Standard
```

---

## SHA-3 Family

Released:

```text
2015
```

Includes:

- SHA3-224
- SHA3-256
- SHA3-384
- SHA3-512

Status:

```text
Modern Alternative
```

---

# SHA-0

## Overview

SHA-0 was the first member of the SHA family.

Developed by:

```text
NSA
```

---

## Output Size

```text
160 Bits
```

---

## Problems

Cryptographic weaknesses were discovered shortly after release.

---

## Current Status

```text
Obsolete
```

Not used today.

---

# SHA-1

## Overview

SHA-1 was designed as an improved version of SHA-0.

---

## Output Size

```text
160 Bits
```

---

## Internal Structure

Uses:

```text
512-bit Blocks
```

and

```text
80 Processing Rounds
```

---

# SHA-1 Workflow

```text
Message
     ↓
Padding
     ↓
Message Blocks
     ↓
80 Rounds
     ↓
160-bit Hash
```

---

# Uses of SHA-1

Historically used in:

- SSL Certificates
- HTTPS
- Git
- Software Verification
- Digital Signatures

---

# Why SHA-1 Failed

## Collision Attacks

Researchers generated:

```text
Different Files

↓

Same Hash
```

This breaks one of the most important properties of secure hashing.

---

## Risks

- Fake Documents
- Certificate Forgery
- Integrity Bypass

---

## Current Status

```text
Deprecated
```

Not recommended.

---

# SHA-2 Family

## Introduction

SHA-2 was designed to replace SHA-1.

Released:

```text
2001
```

Designed by:

```text
NSA
```

---

# SHA-224

## Output Size

```text
224 Bits
```

---

## Uses

- Embedded Systems
- Resource-Constrained Devices

---

## Security

Stronger than SHA-1.

---

# SHA-256

## Output Size

```text
256 Bits
```

---

## Most Popular SHA Algorithm

SHA-256 is currently the most widely used hash function.

---

## Internal Structure

Uses:

```text
512-bit Blocks
```

and

```text
64 Rounds
```

---

# SHA-256 Workflow

```text
Input Data
      ↓
Padding
      ↓
Message Blocks
      ↓
Compression Function
      ↓
64 Rounds
      ↓
256-bit Hash
```

---

# Uses of SHA-256

## HTTPS

Certificate Verification.

---

## Blockchain

Used by:

```text
Bitcoin
```

for mining and transaction verification.

---

## Digital Signatures

Verifies document integrity.

---

## File Integrity Checking

Used to verify downloads.

---

## Security Applications

Used throughout cybersecurity.

---

# Advantages

- Strong Security
- No Practical Collisions
- Industry Standard

---

# SHA-384

## Output Size

```text
384 Bits
```

---

## Uses

- Government Systems
- Enterprise Applications

---

## Security

Higher security margin than SHA-256.

---

# SHA-512

## Output Size

```text
512 Bits
```

---

## Internal Structure

Uses:

```text
1024-bit Blocks
```

and

```text
80 Rounds
```

---

# Uses

- Military Systems
- Government Infrastructure
- High-Security Environments

---

# Advantages

- Extremely Strong Security
- Larger Hash Space

---

# SHA-224 vs SHA-256 vs SHA-384 vs SHA-512

| Algorithm | Output Length |
|------------|------------|
| SHA-224 | 224 Bits |
| SHA-256 | 256 Bits |
| SHA-384 | 384 Bits |
| SHA-512 | 512 Bits |

---

# SHA-3

## Introduction

SHA-3 is the newest SHA family.

Released:

```text
2015
```

---

# Why SHA-3 Was Created

SHA-2 was not broken.

SHA-3 was created as:

```text
Backup Cryptographic Standard
```

in case SHA-2 is ever compromised.

---

# SHA-3 Architecture

SHA-2 uses:

```text
Merkle-Damgård Construction
```

SHA-3 uses:

```text
Sponge Construction
```

---

# Sponge Construction

```text
Input Data
      ↓
Absorb Phase
      ↓
Internal State
      ↓
Squeeze Phase
      ↓
Hash Output
```

---

# SHA-3 Variants

## SHA3-224

```text
224-bit Output
```

---

## SHA3-256

```text
256-bit Output
```

---

## SHA3-384

```text
384-bit Output
```

---

## SHA3-512

```text
512-bit Output
```

---

# Advantages of SHA-3

## Different Architecture

Provides diversity from SHA-2.

---

## Strong Security

No known practical attacks.

---

## Future-Proof Design

Designed for long-term cryptographic security.

---

# SHA in Password Storage

## Common Mistake

Many beginners think:

```text
Password
↓
SHA-256
↓
Database
```

is secure.

It is not.

---

# Why?

Attackers can use:

- Rainbow Tables
- GPU Cracking
- Dictionary Attacks

---

# Recommended Password Hashing Algorithms

## bcrypt

Purpose-built for password storage.

---

## Argon2

Winner of the Password Hashing Competition.

Modern recommendation.

---

## PBKDF2

Widely used in enterprise environments.

---

# Real-World Uses of SHA

## HTTPS

Certificate Integrity.

---

## Digital Signatures

Document Verification.

---

## Blockchain

Transaction Validation.

---

## Software Downloads

File Integrity Verification.

---

## Malware Analysis

File Hash Identification.

---

## Digital Forensics

Evidence Verification.

---

# MD5 vs SHA-1 vs SHA-256

| Feature | MD5 | SHA-1 | SHA-256 |
|----------|----------|----------|
| Output Length | 128 Bits | 160 Bits | 256 Bits |
| Security | Broken | Broken | Secure |
| Collision Resistance | Weak | Weak | Strong |
| Recommended | No | No | Yes |

---

# SHA-2 vs SHA-3

| Feature | SHA-2 | SHA-3 |
|----------|----------|----------|
| Release Year | 2001 | 2015 |
| Architecture | Merkle-Damgård | Sponge |
| Security | Strong | Strong |
| Adoption | Very High | Growing |
| Recommended | Yes | Yes |

---

# Key Takeaway

The SHA family forms the backbone of modern cybersecurity. SHA-1 is deprecated due to collision attacks, while SHA-2 (especially SHA-256 and SHA-512) remains the industry standard for integrity verification, digital signatures, certificates, blockchain technologies, malware analysis, and digital forensics. SHA-3 introduces a completely different sponge-based design that provides additional security diversity for future cryptographic systems.