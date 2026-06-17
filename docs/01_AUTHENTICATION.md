# Phase 4 — Corpus Authentication

**Date:** 2026-06-12
**Goal:** Establish a cryptographic root of trust so that all downstream analysis runs only on authenticated 3301 material, not hoaxes/impersonators.

## Root of trust

Genuine Cicada 3301 communications (2012–2015) were signed with a single PGP key. That key is the anchor: a message is *authentic 3301* **iff** it carries a valid signature from this key. Everything else is `unverified` until proven, or `hoax` if affirmatively disproven.

### The genuine key (verified this session)

| Field | Value |
|---|---|
| Primary fingerprint | `6D85 4CD7 9333 22A6 01C3 286D 181F 01E5 7A35 090F` |
| Key ID | `0x181F01E57A35090F` (short `7A35090F`) |
| UID | `Cicada 3301 (845145127)` |
| Algo / size | RSA-4096, v4 |
| Created | **2012-01-05 03:39:43 UTC** |
| Encryption subkey | `4D390ECF671DDEB1` (RSA-4096, same creation instant) |
| Source | keyserver.ubuntu.com `--recv-keys` (fingerprint-pinned) |
| Local copies | `pgp/cicada_3301_GENUINE.asc`, `pgp/cicada_3301_GENUINE.gpg` |

Cross-checks: fingerprint matches independent references (Uncovering-Cicada wiki, cicada-solvers "Is It Cicada" verifier). UID comment number `845145127` is an unexplained identifier — flagged for later, **not** interpreted here.

## Authentication procedure (reproducible)

```bash
export GNUPGHOME=cicada-investigation/pgp/keyring
# verify any candidate signed message:
gpg --homedir "$GNUPGHOME" --verify message.asc
# PASS only if: "Good signature from 'Cicada 3301 (845145127)'"
#               AND primary key fpr == 6D854CD7933322A601C3286D181F01E57A35090F
```

A "Good signature" from *any other* key ID is NOT authentication — see the hoax below for exactly this trap.

## CONTAMINATION FOUND — first artifact was a decoy

The very first key file pulled (GitHub `aadishgoel/Cicada-3301/PGPKey.txt`, a top Google hit) is **NOT** the real key:

| Field | Hoax key | Genuine key |
|---|---|---|
| Fingerprint | `CEBB2647 6A68DB15 AFB08432 8EAF0197 7B4ADD02` | `6D854CD7...7A35090F` |
| UID | `7A35090F <leon.morgenthaler.4600@gmail.com>` | `Cicada 3301 (845145127)` |
| Algo | RSA-3072 | RSA-4096 |
| Created | 2016-11-28 | 2012-01-05 |
| Status | **revoked same day** | valid |

**The trick:** the impostor set its UID *display name* to the literal string `7A35090F` — the real key's short ID — so anyone searching/grepping for "7A35090F" finds it and is fooled into trusting a 2016 troll key. Quarantined at `corpus/quarantine-hoax/HOAX_aadishgoel_decoykey.asc`.

**Lesson:** short key IDs and display names are attacker-controlled. Only full-fingerprint matching authenticates. This is precisely why Phase 4 precedes everything.

## Corpus buckets

- `corpus/verified/` — carries a valid sig from the genuine key (none yet; next step is to verify the original signed messages)
- `corpus/unverified/` — plausibly 3301 but not yet signature-checked
- `corpus/quarantine-hoax/` — affirmatively disproven (currently: 1 decoy key)

## Status / next

- [x] Genuine key obtained, fingerprint-pinned, stored
- [x] One hoax caught and quarantined
- [ ] Pull original PGP-signed 3301 messages and verify each against the genuine key to populate `corpus/verified/`
