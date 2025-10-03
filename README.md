# Password Security Study — Internship Project

**Objective:**
Analyze password security concepts including hashing, salting, and key derivation functions (KDFs), and understand common attacks and defenses. This project is strictly theory-focused and educational.

**Important:** This repository contains only theory and safe educational explanations. It does **not** include instructions or tools for illegal password cracking. Use these materials only for authorized learning.

---

## 1. Overview

Passwords are the primary authentication method in most systems. Storing them safely is critical to prevent unauthorized access in case of database leaks. This project covers:

* Hashing concepts
* Salting and optional peppering
* Common password KDFs
* Attack techniques
* Defensive strategies
* Responsible lab practices

---

## 2. Key Concepts

### Hash

A hash is a one-way function converting input (password) into a fixed-length string.

* **Deterministic:** Same input → same hash
* **One-way:** Cannot reverse to original input
* **Collision-resistant:** Different inputs rarely produce same hash

### Why Not Store Plaintext Passwords

Storing plaintext allows attackers immediate access if the database is compromised. Hashing forces them to guess and verify passwords, slowing attacks.

### Fast Hashes Are Unsafe

SHA-256, MD5, and similar are fast by design. Fast = easier brute-force attacks with GPUs. Password storage requires **slow and computationally expensive functions**.

### Salt

A salt is a unique, random value added to each password before hashing.

* Prevents precomputed attacks (rainbow tables)
* Ensures identical passwords have different hashes

### Pepper (optional)

A pepper is a global secret added to passwords and stored separately. It provides extra protection if the database leaks but the pepper remains secret.

---

## 3. Key Derivation Functions (KDFs)

KDFs are designed for password storage. They are tunable, often memory-hard, and slow by design:

* **Argon2id:** Modern, memory-hard, recommended for new systems
* **bcrypt:** Mature, adjustable work factor
* **scrypt:** Memory-hard, GPU-resistant
* **PBKDF2:** CPU-bound, widely supported, FIPS-approved

Avoid using MD5, SHA-1, SHA-256 alone for passwords.

---

## 4. How Attackers Crack Passwords

* **Brute-force:** Try all possible passwords
* **Dictionary attacks:** Try common passwords and variations
* **Rainbow tables:** Precomputed hash tables (defeated by unique salts)
* **Offline attacks:** Attacker has the hash file and tries guesses locally

---

## 5. Defensive Best Practices

* Use a **strong KDF** (Argon2id preferred) with a unique salt per password
* Tune cost parameters to slow attackers but allow normal login speed
* Encourage **long passphrases** over short, complex passwords
* Implement **rate-limiting** and lockouts for online attacks
* Require **multi-factor authentication (MFA)**
* Protect global secrets (pepper) securely and with least privilege

---

## 6. Responsible Practice

* Test password-cracking concepts only in lab environments you own or where you have explicit written permission
* Do not use real leaked datasets or attack third-party systems
* Follow responsible disclosure if a vulnerability is discovered

---

## 7. Short Takeaway

Use memory-hard, tunable password hashing with unique salts, allow long passphrases, and implement MFA to protect users from offline attacks.

---

## 8. References

* OWASP: Password Storage Cheat Sheet
* NIST SP 800-63B: Digital Identity Guidelines
* RFC 9106: Argon2 Memory-Hard Function for Password Hashing
* Argon2 reference (PHC winner)
* Responsible disclosure frameworks (HackerOne, government guidance)

---

*This README serves as a complete educational project overview suitable for internship submission and GitHub upload.*
