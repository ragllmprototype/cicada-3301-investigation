# cicada-3301-investigation

A forensic investigation of Cicada 3301 — built on *what Cicada actually signed*, not what archives claim it said.

## The question

**Was Cicada 3301 a continuation of Satoshi Nakamoto's cypherpunk mission after his April 2011 disappearance?**

Eight and a half months after Satoshi went silent ("I've moved on to other things"), Cicada 3301 appeared — same ideology, same obsession with cryptography, recruiting "highly intelligent individuals." This project asks whether that's continuation, or a vacuum filled by someone who understood Satoshi's mission perfectly.

**Honest answer:** the evidence **suggests yes, but does not prove it.** What this investigation *does* deliver is the thing 14 years of speculation never built — a clean, authenticated, falsifiable foundation.

**What I did not do:** solve the puzzle, crack the Liber Primus, or name the architects. **What I did:** authenticate 21 messages cryptographically (with Claude Code's help), catch a hoax that fooled thousands of researchers, recover a corrupted message, and measure stylistic markers against real candidate data. The single firmest result: **the stylometry rules out Wei Dai writing naturally.**

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

# The decoy: the fake key from the popular archive does NOT match
gpg --show-keys corpus/quarantine-hoax/HOAX_aadishgoel_decoykey.asc
# => fingerprint CEBB2647…7B4ADD02  (RSA-3072, created+revoked 2016) — NOT the real key
```

Genuine fingerprint: `6D854CD7 9333 22A6 01C3 286D 181F 01E5 7A35 090F`

---

## Documents

| File | Contents |
|---|---|
| [`docs/00_REPORT.md`](docs/00_REPORT.md) | Full report |
| [`docs/01_AUTHENTICATION.md`](docs/01_AUTHENTICATION.md) | Root of trust; how the hoax key was caught |
| [`docs/02_PGP_FORENSICS.md`](docs/02_PGP_FORENSICS.md) | Key-packet analysis (why PGP authenticates but doesn't attribute) |
| [`docs/03_METHODOLOGY.md`](docs/03_METHODOLOGY.md) | Authentication process, priors, how evidence is weighed |
| [`docs/04_VERIFIED_CORPUS.md`](docs/04_VERIFIED_CORPUS.md) | All 21 verified messages + recovery of the corrupted one |
| [`docs/05_STYLISTIC_MARKERS.md`](docs/05_STYLISTIC_MARKERS.md) | Marker catalog with sample-size limits |
| [`docs/06_STYLOMETRY.md`](docs/06_STYLOMETRY.md) | Controlled comparison vs candidate authors |
| [`docs/REFERENCE.md`](docs/REFERENCE.md) | Condensed data sheet |

---

## Timeline

```
Oct 2008      Satoshi announces Bitcoin to the cypherpunk mailing list
Jan 2009      Genesis block; Hal Finney receives the first transaction
2009–2011     Satoshi actively develops Bitcoin
Apr 23, 2011  Satoshi's final email: "I've moved on to other things."
Apr 2011+     Complete silence
Jan 4, 2012   Cicada 3301 appears — 8.5 months later
```

Before vanishing, Satoshi personally contacted three people:
- **Adam Back** (UK, b. 1970) — Hashcash creator
- **Wei Dai** (US, b. 1976) — b-money creator
- **Hal Finney** (US, 1956–2014) — Bitcoin's first collaborator

(Nick Szabo, Bit Gold, is included as an additional control.)

---

## Findings

### Authentication
- **21/21** messages verify as a good signature from the genuine key `6D854CD7…7A35090F` (20 verified directly; 1 recovered — see below).
- **Hoax caught:** the most-cloned Cicada archive on GitHub embeds a **fake key** — a 2016 decoy (RSA-3072, created *and revoked* the same day) whose UID display name was spoofed to the real key's short ID `7A35090F` to fool anyone matching on the short ID. Reading the *full* fingerprint exposed it. Quarantined.
- **Corrupted message recovered:** the 2013 message pointing to Crowley's *Liber AL vel Legis* had a **genuine signature but a missing first line** (`"Welcome again."`) → BADSIG. A clean GOOD-verifying copy was recovered from a second archive.

### Stylometry — reading all 21 together
- **Not one author.** The messages don't read as a single voice — yet the *style* is rigidly consistent across five years, suggesting an enforced operational standard rather than one person.
- **Double-spacing:** every sentence is followed by two spaces — Cicada **100%** (14/14). A typewriter-era habit, deliberately used in 2012–2017 long after it died. A fingerprint, whether ingrained habit or enforced discipline.
- **British spelling:** in the one off-script moment (the 2015 denial) they wrote "**organisations**" — British. Faking a national spelling to hide identity would be odd, which makes it notable either way.
- **Esoteric tone:** Crowley, "enlightenment," "transcendence," "a private man who wished to transcend." Occult/Western-mystical, not the language of someone optimizing for cryptographic efficiency.

### Candidate testing
| Candidate | Double-spacing | Spelling | Tone | Verdict |
|---|---|---|---|---|
| **Wei Dai** | 0% | American only | rationalist | **ruled out** (natural author) |
| Adam Back | ~8% (one slip) | **British** | technical | **possible** — spelling matches, rest doesn't |
| Nick Szabo | n/a | American | — | ruled out |
| Hal Finney | n/a | insufficient | — | untestable (d. 2014) |

**The writer is: NOT Wei Dai · MIGHT be Adam Back · NOT Szabo · or someone outside the documented circle entirely.** Double-spacing + esoteric tone point to a cypherpunk insider, but probably not one of the headline names — which leaves: an undocumented collaborator, one person adapting two styles to hide, or a group with one style-enforcer.

---

## Consistent with continuation — but not proof

For the broad question (Satoshi-circle continuation vs. an unrelated group), several things line up:
- **Timeline:** 8.5-month gap reads as a planning window.
- **Ideology:** identical cypherpunk philosophy.
- **Skillset:** cryptographic sophistication + operational-security discipline.
- **Deliberate obfuscation:** British spelling, double-spacing, mystical tone all look like chosen masks.

These are **consistent with** continuation and tilt the odds toward an insider rather than random outsiders — but they are not proof, and none of them name a person. The firm, falsifiable result remains the *negative* one: **it was not Wei Dai writing naturally.**

## What remains unknown
- The actual identity of Cicada's architects
- What became of the people who completed the puzzles
- The real purpose of the recruitment
- Whether the operation is still active (the key signed messages as late as 2017)

---

## For future researchers

A clean, authenticated foundation: 21 verified messages, the genuine key, quarantined hoaxes, and candidate corpora — so new hypotheses can be tested against *what Cicada actually signed*, candidates compared, and work shared instead of theorized in isolation.

**Was 3301 a continuation of Satoshi's cypherpunk mission?** The evidence suggests yes; it doesn't prove it. Maybe that's what a 14-year-old mystery deserves — not a confident answer, but a cleaner way to ask the question.

---

## License & attribution

Investigation by Cooldash, with cryptographic verification assisted by Claude Code. Authenticated Cicada 3301 messages are public domain. Analysis and methodology are open for independent verification and extension.
