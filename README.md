# 🔐 T‑26 Cipher  
A lightweight, client‑side text encryption tool implemented in **pure HTML + JavaScript**.  
The algorithm is based on a **custom 26‑character wheel** and a **key‑driven shifting rule**, providing a simple but effective substitution cipher.

---

## ✨ Features

- **100% client‑side** — no backend, no data transmission  
- **Pure HTML + JavaScript** — zero dependencies  
- **Custom cipher algorithm** (T‑26)  
- **Works offline** — open `index.html` and use immediately  
- **Simple UI** — encrypt/decrypt with one click  
- **Safe for casual use** — no key storage, no logs  

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/CH3COOOH/T26Cipher.git
cd T26Cipher
```

### 2. Open the webpage

Just open the file in any browser:

```
index.html
```

No build steps, no server required.

---

## 🔧 How the T‑26 Cipher Works

### 1. Character Set

The cipher uses a fixed 26‑character wheel:

```
0A1B2C3D4E5F6G7H8I9JKLMNOPQRSTUVWXYZ
```

This acts as the lookup table for all substitutions.

---

### 2. Key → Rule Conversion

When the user enters a **KEY**, the program:

1. Converts it to uppercase  
2. For each character, finds its index in the charset  
3. Produces a numeric sequence called **rule**

Example:

```
KEY = "AB3"
rule = [1, 3, 6]   // indices in charset
```

This rule is then **cycled** during encryption/decryption.

---

### 3. Encryption (encode26)

For each character in the plaintext:

- If it exists in the charset → shift forward by rule[i]
- If not → keep original
- Rule index loops automatically

Formula:

\[
cipher[i] = charset[(index(plain[i]) + rule[i]) \bmod 26]
\]

---

### 4. Decryption (decode26)

Reverse the shift:

\[
plain[i] = charset[(index(cipher[i]) - rule[i] + 26) \bmod 26]
\]

Characters not in the charset remain unchanged.

---

## 📁 Project Structure

```
.
├── index.html      # Main UI + encryption logic
└── README.md       # Project documentation
```

> Note: All logic is embedded directly in `index.html` for portability.

---

## 🖥️ UI Overview

- **Top textarea** → output (read‑only)  
- **Bottom textarea** → input text  
- **KEY field** → encryption key  
- **ENC** → encrypt  
- **DEC** → decrypt  

The page is intentionally minimal to keep usage straightforward.

---

## 🛡️ Security Notes

- This cipher is suitable for **lightweight or educational use**.  
- It is **not** intended to replace modern cryptographic algorithms.  
- For strong security, consider using **Web Crypto API** or established libraries.  
- Keys are never stored or transmitted.

---

## 📜 License

MIT License.

## 🔗 Relationship to the Vigenère Cipher

T‑26 Cipher is conceptually similar to the classic **Vigenère cipher**, but with a few important differences:

- **Both** use a *key‑driven sequence of shifts* to transform each character.
- **Both** apply the shifts cyclically across the plaintext.
- **Both** are reversible, symmetric substitution ciphers.

However, T‑26 replaces the traditional A–Z alphabet with a **custom 26‑character wheel**, and the shift values are derived from the **index of each key character within this wheel**, rather than from alphabetical positions.  
This makes T‑26 effectively a **“custom‑alphabet variant of the Vigenère cipher”**, preserving the same conceptual structure while allowing more flexible character mapping.
