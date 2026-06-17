# Verified Corpus Inventory

**Date:** 2026-06-12
**Method:** every candidate message verified with `gpg --verify` against the pinned genuine key `6D854CD7933322A601C3286D181F01E57A35090F`. A file is `VERIFIED` only if the signature is GOOD **and** the primary signing key fingerprint equals the genuine fingerprint.
**Source archive:** `krisyotam/cicada3301` `pgp/messages/` (21 files pulled individually; no repo clone).

## Result: 20 verified / 1 failed

All 20 verified messages were signed by the genuine key. Signature dates form a coherent operational record:

| File | Signed (UTC date) | Round |
|---|---|---|
| 2012-01-key-announcement | 2012-01-05 | 2012 |
| 2012-01-key-in-front-of-you | 2012-01-07 | 2012 |
| 2012-01-book-code-poem | 2012-01-07 | 2012 |
| 2012-01-coordinates | 2012-01-08 | 2012 |
| 2012-01-second-chance | 2012-01-11 | 2012 |
| 2012-01-end-of-puzzle | 2012-02-06 | 2012 |
| 2012-01-final-message | 2012-02-06 | 2012 |
| 2013-cicada-os-message | 2013-01-03 | 2013 |
| 2013-01-cicada-os-message | 2013-01-03 | 2013 |
| 2013-01-rune-table-morse | 2013-01-04 | 2013 |
| 2013-01-telnet-hello | 2013-01-06 | 2013 |
| 2014-01-opening-book-code | 2014-01-06 | 2014 |
| 2014-01-liber-primus-hash-block | 2014-01-07 | 2014 |
| 2014-01-onion5-liber-primus | 2014-01-19 | 2014 |
| 2014-01-onion-welcome | 2014-04-02 | 2014 |
| 2014-01-final-message | 2014-04-02 | 2014 |
| 2014-05-liber-primus-release | 2014-04-02 | 2014 |
| 2015-07-planned-parenthood-denial | 2015-07-28 | 2015 |
| 2017-04-final-message | 2017-04-04 | 2017 |
| 2017-04-final-warning | 2017-04-04 | 2017 |

Stored in `corpus/verified/`; canonical signed plaintext extracted to `corpus/verified_plaintext/`.

> Note: the `2015-07` "Planned Parenthood denial" and the `2017-04` pair are validly signed by the SAME genuine key, i.e. whoever held the key was still active/holding it in 2015 and 2017. Relevant later — the key's custody is not confined to 2012–2014.

## FAILED — quarantined

**`2013-01-opening-book-code.asc` → `quarantine-hoax/CORRUPT-BODY_...`** *(later RECOVERED — see below)*
- Signature is **genuine** (real key, signed 2013-01-02 23:33 EST) but verification = **BADSIG**.
- Cause is **not** line endings: normalizing CRLF→LF still fails. The *body text in this archive copy was altered* from what Cicada actually signed.
- **Root cause identified:** the archive copy **dropped the opening line `"Welcome again."`**, which changed the signed bytes and broke the hash.

### RECOVERY (Phase 3)
A GOOD-verifying copy was recovered from the `cicada-solvers/The-Complete-Cicada3301-Archive` (`book code pastebin.txt` / `C5G2fNPR.txt`), confirmed against the genuine key (signed **2013-01-03 04:33 UTC**). Stored as `corpus/verified/2013-01-opening-book-code-RECOVERED.asc` (plaintext alongside). **Verified corpus is now 21 messages.** The recovered prose adds another double-space instance (M1), consistent with the corpus.

Also in quarantine: `HOAX_aadishgoel_decoykey.asc` (the 2016 revoked decoy key from Phase 4).

## Corpus statistics (reality check for stylometry)

- Verified English-prose total: **~982 words across 20 messages.**
- Much of that is numeric (coordinates, SHA hashes, the big P.S. number strings) → genuine natural-language content is **materially less than 982 words**, and split across 5 years and likely multiple authors/voices.
- **Consequence:** this is a *very small* sample for authorship attribution. Stylometry here can at best be suggestive, never conclusive, and any result needs a control set + explicit uncertainty. This constraint must be stated in the methodology before running it (consistent with `03_METHODOLOGY.md` §4).

## Status

- [x] 20 genuine messages authenticated and isolated
- [x] 1 corrupted message caught and quarantined (signature genuine, text untrustworthy)
- [x] Clean plaintext corpus extracted
- [ ] Next: controlled stylometry — but see the small-sample caveat above
