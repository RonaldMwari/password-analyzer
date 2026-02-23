# 🔐 PassGuard — Password Strength Analyzer & Breach Checker

A browser-based password security tool that analyzes strength in real-time and checks against the HaveIBeenPwned breach database — without ever sending your password over the internet.

---

## Features

- **Real-time strength analysis** — Score updates instantly as you type
- **Entropy calculation** — Measures true password randomness in bits
- **8-point criteria checklist** — Length, character variety, common patterns, sequences, repeats
- **HaveIBeenPwned integration** — Checks if password appeared in known data breaches
- **k-Anonymity privacy model** — Only the first 5 chars of a SHA-1 hash are sent; your password never leaves your browser
- **Actionable recommendations** — Explains exactly how to improve each password
- **Zero dependencies** — Pure HTML/CSS/JS, no build tools or installs needed

---

## How To Use

Just open `passguard.html` in any modern web browser. No server, no install, no dependencies.

```bash
# Option 1: Double-click the file in your file explorer

# Option 2: Open via terminal
open passguard.html          # macOS
start passguard.html         # Windows
xdg-open passguard.html      # Linux
```

---

## How the Breach Check Works

PassGuard uses the **HaveIBeenPwned Pwned Passwords API** with a k-anonymity model:

1. Your password is hashed locally using SHA-1 (via the Web Crypto API)
2. Only the **first 5 characters** of the hash are sent to the API
3. The API returns all hashes that start with those 5 characters (~500 results)
4. Your browser checks locally if your full hash appears in the list
5. **Your actual password — and even the full hash — never leave your device**

This is the same privacy model used by major browsers and password managers.

---

## Scoring System

| Score | Strength | Meaning |
|-------|----------|---------|
| 0–24 | CRITICAL | Easily cracked, likely common |
| 25–44 | WEAK | Vulnerable to dictionary/brute force |
| 45–64 | FAIR | Decent but improvable |
| 65–79 | STRONG | Good for most purposes |
| 80–100 | EXCELLENT | Highly resistant to attacks |

### Score Factors

- **Length** — Up to 30 points (3 pts per character)
- **Uppercase letters** — +10 points
- **Lowercase letters** — +10 points
- **Numbers** — +10 points
- **Special characters** — +15 points
- **Not a common password** — +10 points (capped at 10 if common)
- **No repeated characters** — +8 points
- **No keyboard sequences** — +7 points

### Entropy

Entropy is calculated as: `log2(pool_size) × length`

Where pool size is the number of distinct character types used (lowercase=26, uppercase=26, digits=10, symbols=32).

---

## Concepts Demonstrated

- SHA-1 hashing with the **Web Crypto API** (no libraries needed)
- **k-Anonymity** privacy model for secure API integration
- Real-time DOM manipulation and event handling
- Password security best practices (OWASP guidelines)
- Entropy and information theory applied to security

---

## Possible Extensions

- [ ] Passphrase generator using wordlists
- [ ] Password history tracker (session only)
- [ ] Export strength report as PDF
- [ ] Browser extension version
- [ ] Dark/light theme toggle
- [ ] Bulk password audit mode (paste a list)
