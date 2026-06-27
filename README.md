# TOTP

> *A minimalist, local-first authenticator. Clean design, absolute privacy.*

TOTP is a streamlined two-factor authentication companion. It turns Base32 secret keys into secure, rolling 6-digit verification codes. Everything stays inside your browser window. No telemetry, no external scripts, no servers.

---

## Why

Most modern authenticators require user accounts, mobile apps, or cloud syncing. That's unnecessary surface area for tools meant to secure your life.

This project distills the Time-Based One-Time Password algorithm down to its essential form. It provides a highly scannable, quiet layout that lives entirely in your local ecosystem, cutting out the noise of traditional security managers.

---

## Features

* **Local-first persistence** — Secrets are committed to `localStorage` locally. No networks, no cloud storage, no external API handshakes.
* **Native Web Crypto** — Computes cryptographic tokens efficiently via standard browser-native algorithms (`crypto.subtle.importKey` and `HMAC-SHA-1`).
* **Clean geometric grid** — Built entirely inside a sharp responsive split-screen pane, scaling from desktop workstations down to mobile screens natively.
* **Copy on click** — Tap any generated token to instantly copy it to your clipboard with clean visual confirmation.
* **Zero dependencies** — Hand-crafted purely within a single, lightweight HTML file under 6 KB. No frameworks, no bundlers, no npm packages.

---

## Structure

```
totp/
└── index.html         — Unified self-contained codebase (DOM structure, tokens, crypto engine)

```

---

## Technical notes

### Native Base32 decoding

Since standard browser environments don't include a built-in Base32 parser, the internal `decode32()` method parses secret keys manually into a `Uint8Array`. It masks, shifts bitwise values safely, and trims trailing padding characters (`=`) cleanly during user entry.

### Cached CryptoKeys

To protect system memory and processing bandwidth, the application skips redundant secret imports. Imported keys are safely cached inside an active `Map` block (`keyCache`), keeping code updates completely fluid at every 30-second epoch step.

### Contrast ratios (background `#faf7f2`)

| Token | Hex | Ratio | Level |
| --- | --- | --- | --- |
| Main typography / Accent backgrounds | `#262626` | 13.1:1 | AAA |
| Secondary text / Headers | `#7c7975` | 4.3:1 | AA (Large Text) |
| Form borders / Muted text | `#a39f98` | 2.5:1 | placeholder |
| Input baselines / Grid outlines | `#ede9e2` | 1.3:1 | structural |

---

## License

MIT
