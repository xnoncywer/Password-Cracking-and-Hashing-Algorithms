# Password Security Study — Internship Project

**Short description**
A concise, theory-only project that explains password hashing, salting, common password‑hashing algorithms, attack techniques, and defensive best practices. This repository is intended for educational use and internship submission.

**Important:** This repo contains only theory and safe educational materials. It does **not** include tools or instructions for unauthorized password cracking. Do not use these materials to attack systems or accounts.

---

## Contents

* `report.md` — Short theory report on password hashing and defenses.
* `safe_demos/` — Optional folder for local educational demos (hashing & verification) — use only on your own test systems.
* `slides/` — Presentation slides (optional).
* `references.md` — Authoritative sources and further reading.

---

## Key recommendations (short)

* Use a memory‑hard, tunable KDF such as **Argon2id** (preferred), **bcrypt**, or **scrypt** for storing passwords.
* Always use a **unique random salt** per password.
* Allow **long passphrases** and avoid overly strict composition rules that reduce usability.
* Add **multi‑factor authentication (MFA)** and rate limiting to protect accounts.
* Only test cracking methods in authorized lab environments with explicit permission.

---

## How to use this repo

1. Read `report.md` for a short, simple theory overview suitable for upload.
2. Add any slides or diagrams you need in `slides/` for presentation.
3. If you include `safe_demos/`, keep demos local and explicitly label them educational-only.

---

## License

Choose a license for your repo (e.g., MIT). This project contains non-sensitive educational material.

---

## Contact / Responsible use

If you discover security issues while learning, follow responsible disclosure practices and do not exploit any third-party systems. Use this repository only for learning and authorized testing.
