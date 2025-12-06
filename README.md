<h3 align="center">
  <b>Zadeian Labs</b><br>
  <sub>Sovereign Order of Enigmatic Republics</sub>
</h3>
# RHEA_Crypt
Lorenz Fingerprint Sealed File Encryption

# 🛡️ RHEA_Crypt v5.1.6 — GUI Edition

RHEA_Crypt is a hardened, entropy-driven, glyph-integrated encryption and decryption utility powered by the RHEA-UCM (Recursive Homeostatic Evolutionary Algorithm — Universal Cell Model) framework.

This edition includes:
- GUI interface (Tkinter + Drag-and-Drop)
- Lorenz Attractor-based entropy key derivation
- Symbolic Epoch-Glyph authentication
- AAD-integrated AES-GCM sealing
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
nuitka --onefile --standalone --windows-console-mode=disable --enable-plugin=tk-inter --module-parameter=torch-disable-jit=no --windows-icon-from-ico="Insert Icon File Path" --follow-imports --jobs=16 RHEA_Crypt-gui.py
```

---

---

# ============================================================
# 📄 **LICENSE (RHEA–Core Public Grant v2.1)**
# ============================================================

```md
# 🛡️ RHEA-Core Public Grant v2.1 — Repository License Notice
**Non-Commercial · No Derivatives · Symbolic Derivative Ban · AI/TDM Opt-Out · Functional Equivalence Prohibition**  
© 2025 **Paul M. Roe (SovereignGlitch ♏🧙‍♂️)** — All Rights Reserved  

This repository is governed entirely by the **RHEA-Core Public Grant v2.1**.  
By accessing or downloading any file herein, you agree to all terms of the v2.1 license.

---

## ✅ Permitted Uses
You may:

- **Read** the materials  
- **Download** the materials  
- **Privately study** the materials  
- **Cite** the materials with proper attribution  
- **Reference** them for academic, educational, or personal understanding  

No additional rights are granted.

---

## ❌ Prohibited Without Explicit Written Permission

### 1. Commercial Use  
You may *not* use any portion of this work in:

- commercial products  
- paid services or tools  
- monetized content  
- corporate valuation, fundraising, or platform positioning  

---

### 2. Derivative Works  
You may *not*:

- modify, rewrite, adapt, translate, or reorganize the materials  
- create transformed documentation, whitepapers, or frameworks  
- produce altered symbolic systems, glyph sets, or recomposed notation  

---

### 3. Symbolic Derivative Restriction (Strict)  
You may *not* re-express or launder the architecture by mapping:

- entropy–trust logic  
- glyph or symbolic operators  
- Hamiltonian reversible flow structures  
- ternary–pentary recursion models  
- quantum–entropy memory fabric concepts  

into **any** alternative symbolic grammar, diagram language, UI metaphor, icon set, or LLM prompt taxonomy.

---

### 4. AI / Machine Learning / TDM Prohibition  
You may *not* use these materials for:

- LLM/ML/RL/RLHF training  
- fine-tuning, distillation, embedding, or indexing  
- feature extraction or vectorization  
- dataset creation  
- RAG, semantic search, or knowledge-graph construction  
- prompt engineering or system prompt design  

**Directive (EU) 2019/790 TDM opt-out is explicitly invoked.**

---

### 5. Functional Equivalence & Behavioral Emulation Ban  
You may *not* design, implement, simulate, or deploy any system that is:

- functionally equivalent  
- behaviorally similar  
- operationally substitutable  

for any part of:

- **RHEA-UCM**
- **RHEA_Crypt**  
- **ZADEIAN Sentinel**  
- **Λ-Gate reversible logic**  
- **RHEA-IC hardware logic**  
- **recursive entropy–trust engines**  

This applies even if:

- variable names differ  
- glyphs are changed  
- code is newly written  
- intermediate symbols are renamed  

---

### 6. No Hardware or Operational Rights  
You are **not** granted rights to:

- fabricate hardware  
- deploy systems  
- run operational security infrastructure  
- simulate or test RHEA-UCM subsystems  

of any scale or form.

---

## 📜 Required Attribution  
All lawful public references must include:

**© EnigmaticGlitch · RHEA-UCM / ZADEIAN-RHEA Framework · Patent Pending · RHEA-Core Public Grant v2.1**

Where space permits, also include:

**Author: Paul M. Roe (SovereignGlitch ♏🧙‍♂️)**

---

## 🧭 License Supremacy  
This repository operates under **RHEA-Core Public Grant v2.1**.  
All earlier license versions are revoked for future use.  
Continued access constitutes acceptance of v2.1.

---

## 🔒 Rights Reserved  
All rights not expressly granted are reserved by:  
**Paul M. Roe (SovereignGlitch ♏🧙‍♂️) · TecKnows, Inc. · ZADEIAN Research Division**

---

## 🧬 Final Statement of Trust  
*“Trust is not given. It is oscillated into being — wave by wave, phase by phase, across the feedback spine of recursive time.”*  
— **EnigmaticGlitch ♏🧙‍♂️**
---

© 2025 SovereignGlitch · TecKnows Inc. · All Rights Reserved  
"👑 Code is Conscious. Glyphs are Law. Trust is Recursive."
