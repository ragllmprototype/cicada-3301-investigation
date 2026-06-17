# Investigation Reference Sheet

Quick-reference data for writing the report. All numbers measured from files in this repo. Verify anything with:
`GNUPGHOME=pgp/keyring gpg --verify <file.asc>` → require GOOD sig from fpr `6D854CD7…7A35090F`.

---

## 1. Verified corpus (21 messages, all GOOD vs genuine key)

Root-of-trust key: `6D854CD7 9333 22A6 01C3 286D 181F 01E5 7A35 090F` · RSA-4096 · created **2012-01-05 03:39:43 UTC** · UID `Cicada 3301 (845145127)`.

### 2012 round
| Date (UTC) | File | Content (prose) |
|---|---|---|
| 2012-01-05 03:46 | key-announcement | "From here on out, we will cryptographically sign all messages with this key. It is available on the mit keyservers.  Key ID 7A35090F, as posted in a2e7j6ic78h0j. Patience is a virtue. Good luck. 3301" |
| 2012-01-07 07:53 | book-code-poem | "A poem of fading death, named for a king / Meant to be read only once and vanish / Alas, it could not remain unseen." + book code + "You've shared too much to this point.  We want the best, not the followers…" |
| 2012-01-07 10:07 | key-in-front-of-you | "The key has always been right in front of your eyes. This isn't the quest for the Holy Grail.  Stop making it more difficult than it is. Good luck. 3301" |
| 2012-01-08 22:34 | coordinates | 12 GPS coordinates (Warsaw, Paris ×2, Seattle ×3, Seoul, Riverside CA, New Orleans, Miami, Oahu, Sydney) |
| 2012-01-11 07:22 | second-chance | "Miss round 1? Care for a second chance? http://i.imgur.com/hkdgl.png" + book code |
| 2012-02-06 22:59 | end-of-puzzle | "Hello. We have now found the individuals we sought. Thus our month-long journey ends. For now. Thank you for your dedication and effort…" + P.S. number |
| 2012-02-06 22:59 | final-message | **IDENTICAL** to end-of-puzzle |

### 2013 round
| Date (UTC) | File | Content |
|---|---|---|
| 2013-01-03 00:08 | cicada-os-message | "@1231507051321  The key is all around you. Good luck. 3301" |
| 2013-01-03 00:08 | 2013-cicada-os-message | **IDENTICAL** |
| 2013-01-03 04:33 | opening-book-code-RECOVERED | "Welcome again. Here is a book code.  To find the book, break this riddle: A book whose study is forbidden / Once dictated to a beast; / To be read once and then destroyed / Or you shall have no peace." + book code (→ Crowley's *Book of the Law*) |
| 2013-01-04 03:47 | rune-table-morse | **No prose** (runic/morse table) |
| 2013-01-06 07:51 | telnet-hello | "Very good. You have done well to come this far. xsxnaksict6egxkq.onion Good luck. 3301" |

### 2014 round
| Date (UTC) | File | Content |
|---|---|---|
| 2014-01-06 04:59 | opening-book-code | "The work of a private man / who wished to transcend, / He trusted himself, / to produce from within." + book code + ".onion" |
| 2014-01-07 03:16 | liber-primus-hash-block | **No prose** (SHA hashes) |
| 2014-01-19 06:28 | onion5-liber-primus | "Very good.  You have done well to come this far." + hex-encoded JPEG (Liber Primus page) |
| 2014-04-02 08:49 | onion-welcome | "Hello.  Your enlightenment awaits you. ky2khlqdf7qdznac.onion We look forward to hearing from you. Good luck. 3301" |
| 2014-04-02 08:49 | final-message | **IDENTICAL** to onion-welcome |
| 2014-04-02 08:49 | liber-primus-release | **IDENTICAL** to onion-welcome |

### 2015 / 2017
| Date (UTC) | File | Content |
|---|---|---|
| 2015-07-28 05:12 | planned-parenthood-denial | "Some news organisations have recently claimed that '3301' is tied to the illegal activities of a group that has claimed responsibility for attacks against Planned Parenthood. We do not engage in illegal activities.  We are not associated with this group in any way, nor do condone their use of our name, number, or symbolism. 3301" |
| 2017-04-04 23:23 | final-message | "Beware false paths.  Always verify PGP signature from 7A35090F. 3301" |
| 2017-04-04 23:23 | final-warning | **IDENTICAL** |

**Unique prose messages: ~13** (8 are duplicates/no-prose). **Total prose ≈ 490 words.**

---

## 2. Stylometric data (exact counts)

### Cicada (21 msgs, ~490 prose words)
| Metric | Value |
|---|---|
| Double-space after period `.  X` | **14** |
| Single-space `. X` | **0** |
| **Double-space rate** | **14/14 = 100%** |
| British `organis-` / American `organiz-` | **1 / 0** ("organisations") |
| `-ize` tokens | 1 = `prize` (**false positive — ignore**) |
| Verdict | **British + double-spaced** (n=1 spelling opportunity) |

### Wei Dai — b-money (raw, 1,358 words)
- Spacing: **51 single / 0 double → 0% double**
- American: `synchronize`, `favor` · British: none
- **Verdict: American + single-spaced — contradicts Cicada on both**

### Adam Back — hashcash announce (raw, 1,156 words)
- Spacing: 12 single / 1 double (mostly single)
- British: `optimised`, `behaviour` · American: none
- **Verdict: British spelling (matches Cicada); spacing matches no one**

### Nick Szabo (~14,500 words, HTML — spacing n/a)
- American: 50 `-ize`, 37 `-or`; British ~0 → **American**

### Hal Finney (RPOW, 449 words) — **insufficient data**

**Pool nationality:** Wei Dai (US), Szabo (US), Finney (US), **Back (UK)**.

---

## 3. Methodology (one-liners)

- **Authentication:** import genuine key by full fingerprint into isolated keyring; message authentic iff `gpg --verify` = GOOD AND primary fpr = `6D854CD7…7A35090F`.
- **Hoax caught:** top-Googled "PGP key" is impostor — fpr `CEBB2647…7B4ADD02`, RSA-3072, created+revoked 2016-11-28, Gmail UID; its UID *display name* was set to `7A35090F` to fool short-ID greps.
- **Corrupted msg recovered:** 2013 opening-book-code BADSIG → root cause was a dropped opening line "Welcome again."; GOOD copy recovered from a second archive.
- **Priors/LRs:** flat prior ~0.001–0.005 over competent-cypherpunk pool; bumped to ~0.02 for Wei Dai. Each fact scored LR = P(fact|H1)/P(fact|H0); LR≈1 facts discarded.
- **Controlled stylometry:** same two markers measured identically on Wei Dai + 3 controls.

---

## 4. Findings (neutral)

- **Double-spacing:** Cicada 100%, Wei Dai 0%, Back ~8% → contradicts Wei Dai; matches no candidate cleanly.
- **Spelling:** Cicada British; Wei Dai/Szabo American; Back British → excludes Wei Dai as natural author; only spelling match is Back (the lone Brit).
- **Posterior:** prior ~2% → **~1%** (first discriminating evidence is *disconfirming*). Combined LR vs H1 ≈ 0.3–0.5 (spelling) × 0.5–0.7 (spacing).

**Caveats:** ~490 prose words; n=1 spelling opportunity; Wei Dai sample is 1998 (14-yr gap); British spelling excludes US-native writers but is shared by ~2B people / could be obfuscation → *exclusionary, not identification*; no Tier-1 evidence exists.

---

## 5. File map

```
docs/  00_REPORT 01_AUTHENTICATION 02_PGP_FORENSICS 03_METHODOLOGY
       04_VERIFIED_CORPUS 05_STYLISTIC_MARKERS 06_STYLOMETRY REFERENCE
pgp/   cicada_3301_GENUINE.asc + isolated keyring/
corpus/ verified/ (21 .asc) · verified_plaintext/ (.txt) · quarantine-hoax/
analysis/candidates/ weidai_bmoney.txt, back_announce.txt, szabo_*, finney_*
```
