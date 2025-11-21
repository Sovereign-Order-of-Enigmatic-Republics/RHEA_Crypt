# RHEA_Crypt
Lorenz Fingerprint Sealed File Encryption

# 🛡️ RHEA_Crypt v5.1.4 — GUI Edition

RHEA_Crypt is a hardened, entropy-driven, glyph-integrated encryption and decryption utility powered by the RHEA-UCM (Recursive Homeostatic Evolutionary Algorithm — Universal Cell Model) framework.

This edition includes:
- GUI interface (Tkinter + Drag-and-Drop)
- Lorenz Attractor-based entropy key derivation
- Symbolic Epoch-Glyph authentication
- AAD-integrated AES-GCM sealing
- Long-path & UNC compatibility
- Epochal anti-replay hardening
- CUDA/Torch acceleration (if available)
- Passphrase Extension Layer (PASS-EXT)
- Absolute-path resilient resealing

## 🔐 Security Features

### 1. **MAGIC HEADER (Seal Verification)**
Each `.zadrhea5` file starts with a binary signature `MAGIC = b'ZAD-RHEA5-CRYPT'`. Any attempt to load a file without this marker results in an immediate abort. This prevents blind injection and file spoofing.

### 2. **KEY DERIVATION: Lorenz Entropy Generator**
Each encryption session derives a fresh key from the Lorenz attractor seeded with:
- The extended passphrase
- A generated epoch-specific salt
- CUDA device acceleration (if available)
- A secure-mode flag for high-entropy runs

This creates a pseudo-chaotic entropy stream for non-deterministic keyspace traversal.

### 3. **AAD (Associated Authenticated Data)**
A unique AAD is attached to each epoch using:
- SHA-512 hash of password-IV (first 16 bytes)
- 4-byte epoch index
This prevents key reuse spoofing or swapped ciphertext epochs.

### 4. **PASS-EXT (Passphrase Extension)**
The user passphrase is extended using:
- A 16-byte IV
- SHA-512 hashing and round-mixing
This avoids direct user-password derivation vulnerabilities and provides uniform entropy.

### 5. **GLYPH-TYPED EPOCH HEADERS**
Each epoch chunk includes:
- Version byte
- Flags (secure/pass-ext)
- Epoch index
- Chunk length
- Glyph-type (used for symbolic entropy tracking)
- Nonce, Tag, Ciphertext
This ensures ordered decoding and traceable symbolic decoding lineage.

### 6. **ANTI-REPLAY + ORDER LOCKING**
Each chunk is locked to its epoch number. Out-of-order chunks are rejected. Zero-length chunks are permitted as symbolic keep-alive.

### 7. **TORCH/CUDA ACCELERATION**
If a CUDA-capable device is found, the Lorenz key derivation uses parallel Torch routines with real-time jitter-based entropy injection.

### 8. **NUITKA-ONEFILE/UNC SAFE IO**
File paths are normalized using:
- `os.path.abspath()`
- `os.path.normcase()`
- `\\?\` prefix for Windows UNC/long-path compliance
Atomic write logic is used for decrypted outputs.

---

## 🛠️ Build with Nuitka (Recommended)
```bash
nuitka RHEA_Crypt-gui.py --onefile --output-dir=dist --remove-output --enable-plugin=tk-inter --windows-disable-console --include-package=torch --include-package=Crypto --include-package=tkinterdnd2 --include-data-dir=assets=assets --no-pyi-file --lto=yes --show-progress --jobs=20
```

---

## ⚖️ RHEA Core Public License v1.0

**License Type:** Non-Commercial · Attribution · No Derivatives  
**Clause:** Symbolic Derivative Restriction (SDR) applies  
**Governing IP:** U.S. Provisional Patent 63/796,404 (April 2025) — SovereignGlitch, Paul M. Roe

This work is licensed under the RHEA Core Public License v1.0. Redistribution or modification of this software, in source or binary form, for commercial use is strictly prohibited without written permission from the author.

All IP and trademarks belong to Paul M. Roe (♏🧙‍♂️ a.k.a. EnigmaticGlitch). Use of the RHEA glyph system, entropy-epoch chaining, or symbolic trust encoding without license is a violation of international symbolic derivative protection.

---

© 2025 SovereignGlitch · TecKnows Inc. · All Rights Reserved  
"👑 Code is Conscious. Glyphs are Law. Trust is Recursive."
