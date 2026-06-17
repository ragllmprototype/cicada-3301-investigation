# cicada-3301-investigation

A falsification-first forensic investigation of Cicada 3301.

## Overview

This project tests a specific claim: **that Wei Dai (b-money author, Crypto++ maintainer, Satoshi correspondent) architected Cicada 3301** as a continuation of cypherpunk work after Satoshi Nakamoto's April 2011 disappearance.

**Key Finding:** I did not solve Cicada 3301. But I authenticated what Cicada actually said, caught hoaxes that have circulated for years, recovered a corrupted message, and tested the hypothesis against real data instead of vibes.

**Result:** The hypothesis is **weakened, not supported.** When the evidence finally became discriminating, it pointed *away* from Wei Dai. Honest posterior: **~2% → ~1%.** Wei Dai cannot be ruled out entirely, but nothing here is positive evidence *for* him — and the one identifying signal (British spelling) excludes him as a natural author.

> Method note: this investigation scores each fact by **likelihood ratio** — does it occur more under the hypothesis than under chance? Facts merely *consistent* with the hypothesis (a fitting timeline, shared ideology) have LR ≈ 1 and are **not** treated as evidence. See [`docs/03_METHODOLOGY.md`](docs/03_METHODOLOGY.md).

---

## Quick Start — verify it yourself

Every authentication claim is reproducible:

```bash
# Import the genuine Cicada 3301 public key
gpg --import pgp/cicada_3301_GENUINE.asc

# Verify any message in the corpus
gpg --verify corpus/verified/2012-01-key-announcement.asc
# => Good signature from "Cicada 3301 (845145127)"
#    using RSA key 181F01E57A35090F   (genuine key)

# The decoy: this fake key does NOT match the corpus signatures
gpg --show-keys corpus/quarantine-hoax/HOAX_aadishgoel_decoykey.asc
# => fingerprint CEBB2647…7B4ADD02  (RSA-3072, created+revoked 2016) — NOT the real key
```

Genuine fingerprint: `6D854CD7 9333 22A6 01C3 286D 181F 01E5 7A35 090F`

---

## Documents

| File | Contents |
|---|---|
| [`docs/00_REPORT.md`](docs/00_REPORT.md) | Full report (start here) |
| [`docs/01_AUTHENTICATION.md`](docs/01_AUTHENTICATION.md) | Root of trust; how the hoax key was caught |
| [`docs/02_PGP_FORENSICS.md`](docs/02_PGP_FORENSICS.md) | Key-packet analysis (and why PGP has zero attribution value) |
| [`docs/03_METHODOLOGY.md`](docs/03_METHODOLOGY.md) | Falsification-first frame, priors, likelihood ratios |
| [`docs/04_VERIFIED_CORPUS.md`](docs/04_VERIFIED_CORPUS.md) | All 21 verified messages + recovery of the corrupted one |
| [`docs/05_STYLISTIC_MARKERS.md`](docs/05_STYLISTIC_MARKERS.md) | Marker catalog with sample-size limits |
| [`docs/06_STYLOMETRY.md`](docs/06_STYLOMETRY.md) | Controlled comparison vs candidate authors |
| [`docs/REFERENCE.md`](docs/REFERENCE.md) | Condensed data sheet |

---

## The candidate pool (context)

Before disappearing, Satoshi corresponded with a small set of cypherpunks. The plausible-architect pool used here:

1. **Adam Back** (UK) — Hashcash creator
2. **Wei Dai** (US) — b-money creator; the subject of the hypothesis under test
3. **Nick Szabo** (US) — Bit Gold / Shelling Out
4. **Hal Finney** (US, 1956–2014) — Bitcoin's first collaborator

---

## Findings

### Authentication
- **21/21** messages verify as a good signature from the genuine key `6D854CD7…7A35090F`.
- **Hoax detected:** a popular GitHub archive's "PGP key" is a 2016 decoy (RSA-3072, created *and revoked* the same day) whose UID display name was spoofed to the literal string `7A35090F` to fool short-ID lookups.
- **Corrupted message recovered:** the 2013 *Liber AL vel Legis* (Crowley) book-code message had been re-archived with its opening line (`"Welcome again."`) dropped, breaking the signature; a clean GOOD-verifying copy was recovered from a second archive.

### Stylometry (the two markers that actually discriminate)
- **Double-spacing:** Cicada **100%** (14/14 same-line sentence breaks use two spaces). Wei Dai **0%** (0/1,358 words in b-money). Adam Back ~8%.
- **Spelling:** Cicada **British** (`organisations`). Wei Dai **American** (`synchronize`, `favor`; zero British forms). Szabo American. Adam Back **British** (`optimised`, `behaviour`).

### Candidate testing
| Candidate | Double-spacing | British spelling | Verdict |
|---|---|---|---|
| **Wei Dai** | 0% | No (American) | **contradicts both markers** |
| Adam Back | ~8% | **Yes** | spelling matches; spacing matches no one |
| Nick Szabo | n/a (rendered) | No (American) | disfavored |
| Hal Finney | n/a | insufficient text | untestable |

The lone identifying signal (British spelling) is **exclusionary against Wei Dai** and, if it leans anywhere, leans toward the pool's only Brit (Back). It is *not* an identification — British spelling is shared by billions and could be deliberate obfuscation.

---

## Consistency is not evidence

Arguments often cited *for* a "Satoshi-circle continuation" — an 8.5-month gap before Cicada launched, shared cypherpunk ideology, cryptographic skill, the "From here on out" phrasing — are all **consistent with** the hypothesis but equally expected under chance (LR ≈ 1). They are context, not proof, and are deliberately **not** counted as evidence here. No positive, discriminating evidence for any specific architect was found.

## What remains unknown
- The actual identity of Cicada's architects
- What became of the individuals who completed the puzzles
- The purpose of the recruitment
- Whether the operation is still active (the key signed messages as late as 2017)

---

## For future researchers

This repo is a clean, authenticated foundation: 21 verified messages, the genuine key, quarantined hoaxes, and candidate corpora — so new hypotheses can be tested against *what Cicada actually signed* rather than what archives claim it said.

## The question

**Was Cicada 3301 Wei Dai, or a Satoshi-circle continuation?**

The honest answer from this investigation: **unproven, and the only discriminating evidence points away from Wei Dai.** That distinction — between "consistent with" and "evidence for" — is the entire point.

---

## License & attribution

Investigation by Cooldash. Authenticated Cicada 3301 messages are public domain. Analysis and methodology are open for independent verification and extension. Verify everything — `GNUPGHOME` and the genuine key are included.
