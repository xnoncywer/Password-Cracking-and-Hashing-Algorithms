# Password Security Report

**Objective:** Provide a short, easy-to-read explanation of password hashing, salting, common password‑hashing algorithms, attack techniques, and defensive best practices. This is a theory-only report suitable for uploading to GitHub as part of an internship submission.

---

## 1. Executive summary
Store passwords using a slow, adaptive, memory-aware key derivation function (KDF) and a unique random salt per password. Allow long passphrases and add multi-factor authentication (MFA). These practices make offline cracking expensive and protect user accounts.

---

## 2. Key concepts

### What is a hash?
A hash is a one-way function that turns input (like a password) into a fixed-length string. Hashes are deterministic (same input → same hash) and infeasible to reverse.

### Why not store plaintext passwords?
Plaintext passwords give attackers immediate access if a database is breached. Hashes force attackers to guess passwords and compare hashes, which slows them down.

### Why fast hashes (SHA-256, MD5) are bad for passwords
Fast cryptographic hashes are designed for speed. Speed is bad for password storage because attackers can try many guesses per second using GPUs. For passwords we want functions that are deliberately slow and costly.

### Salt
A salt is a unique, random value added to each password before hashing. Salts prevent precomputed attacks (rainbow tables) and ensure identical passwords produce different hashes.

### Pepper
A pepper is an optional global secret added to passwords (stored outside the database). It provides extra protection if the database leaks but the pepper remains secret.

---

## 3. Password-specific functions (KDFs)
These functions are designed for password storage and can be tuned to increase cost:
- **Argon2id** — modern, memory-hard, recommended for new systems.
- **bcrypt** — mature and widely used; adjustable work factor.
- **scrypt** — memory-hard design to resist GPU acceleration.
- **PBKDF2** — older, widely supported, CPU-bound; sometimes required in regulated contexts.

Do not use general-purpose fast hashes (MD5, SHA-1, SHA-256) alone for password storage.

---

## 4. How attackers crack hashes (brief)
- **Brute-force:** try every possible password.
- **Dictionary attacks:** try common passwords and variations.
- **Rainbow tables:** precomputed hash tables (defeated by unique salts).
- **Offline attacks:** attacker has the hash file and tries guesses locally (most damaging).

---

## 5. Defensive best practices
- Use a **strong KDF** (Argon2id preferred) with a unique random salt per password.
- Tune the KDF cost parameters (time and memory) to slow attackers while keeping login latency acceptable.
- Encourage **long passphrases** over complex but short rules.
- Implement **rate limiting** and account lockouts for online attempts.
- Require **multi-factor authentication (MFA)** to protect accounts even if passwords leak.
- Store and protect any global secrets (pepper) separately and with least privilege.

---

## 6. Responsible practice (theory)
Only perform password‑cracking experiments in authorized lab environments on systems you own or where you have explicit written permission. Do not use real leaked datasets or attempt to attack third‑party systems without consent. If you discover a vulnerability, follow a responsible disclosure process.

---

## 7. Short takeaway
Use memory‑hard, tunable password hashing with unique salts, allow long passphrases, and add MFA — these simple steps greatly increase user security against offline attacks.

---

*End of report.*

