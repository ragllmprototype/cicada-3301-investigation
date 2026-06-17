# cicada-3301-investigation
A deep-dive into Cicada 3301.
## Overview

This investigation examines whether Cicada 3301 represents a continuation of Satoshi Nakamoto's cypherpunk work after his April 2011 disappearance.

**Key Finding:** I did not solve Cicada 3301. But I authenticated what Cicada actually said, caught hoaxes that fooled 14 years of investigators, and built a forensic foundation for future research.

**Status:** Hypothesis is plausible and consistent with evidence, but not proven. Evidence rules out Wei Dai as the natural voice author. Timeline and ideology align with someone in Satoshi's inner circle.

---

## Quick Start

If you want to verify this investigation:

```bash
# Import the genuine Cicada PGP key
gpg --import cicada_3301_genuine.asc

# Verify a message
gpg --verify corpus/verified/2012-01-05_key-announcement.asc
# Output should show: GOODSIG 6D854CD7933322A6 (genuine key)
```

---

## Investigation Structure

- **INVESTIGATION.md** - Full essay (recommended reading)
- **METHODOLOGY.md** - Authentication process, hoax detection, verification steps
- **STYLOMETRY.md** - Stylistic markers analysis (double-spacing, British spelling, mystical tone)
- **AUTHENTICATED_CORPUS.md** - All 21 verified messages organized by year
- **CANDIDATE_ANALYSIS.md** - Testing Wei Dai, Adam Back, Hal Finney, Nick Szabo

---

## Core Timeline

```
October 2008:    Satoshi announces Bitcoin to cypherpunk mailing list
January 2009:    Bitcoin genesis block
2009-2011:       Satoshi actively develops Bitcoin
April 23, 2011:  Satoshi's final email: "I've moved on to other things."
April 2011+:     Complete silence
January 4, 2012: Cicada 3301 appears (8.5 months later)
```

---

## The Three Candidates

Satoshi personally contacted exactly three people before disappearing:

1. **Adam Back** (Aug 2008) - Hashcash creator, born July 1970
2. **Wei Dai** (Aug 2008) - b-money creator, born 1976  
3. **Hal Finney** (Jan 2009) - Bitcoin's first collaborator, 1956-2014

---

## Key Findings

### Authentication (Methodology)
- ✓ 21/21 messages verify as GOODSIG against genuine key `6D854CD7 9333 22A6 01C3 286D 181F 01E5 7A35 090F`
- ✓ Hoax detected: Popular GitHub archive contains fake key (2016 decoy with spoofed display name)
- ✓ Corrupted message recovered: 2013 message about Crowley's *Liber AL vel Legis* was archived with first line missing

### Stylometric Markers
- **Double-spacing:** Cicada 100% (14/14 periods followed by two spaces), Wei Dai 0%
- **Spelling:** Cicada British ("organisations"), Wei Dai American (only "-ize" forms)
- **Tone:** Cicada mystical/esoteric (Crowley references, enlightenment), Wei Dai rationalist

### Candidate Testing
| Candidate | Double-spacing | British Spelling | Mystical Tone | Match? |
|-----------|---|---|---|---|
| Wei Dai | 0% | No | No | ❌ Rules out |
| Adam Back | ~8% | Yes | No | ⚠️ Partial match |
| Nick Szabo | n/a | No | No | ❌ Rules out |
| Hal Finney | n/a | n/a | n/a | n/a (died 2014) |

---

## Evidence for Satoshi Continuation

- ✓ Timeline: 8.5 months between disappearance and Cicada launch (planning window)
- ✓ Ideology: Identical cypherpunk philosophy, cryptography-as-freedom mission
- ✓ Skillset: Cryptographic sophistication, operational security discipline, recruitment infrastructure
- ✓ Consistency: "From here on out" indicates pre-existing operation (not spontaneous launch)

## What Remains Unknown

- ✗ Definitive identity of Cicada architects
- ✗ What happened to people who "won" the puzzles
- ✗ Purpose of recruitment beyond stated "highly intelligent individuals"
- ✗ Whether operation is still active (silent since 2017)

---

## How to Verify This Investigation

All claims are reproducible:

1. **Download the verified messages:** See `corpus/verified/` directory
2. **Import the genuine key:** `gpg --import cicada_3301_genuine.asc`
3. **Verify any message:** `gpg --verify <message.asc>`
4. **Check stylometry:** Compare marker counts in `STYLOMETRY.md` against candidate corpora
5. **Test the hoax key:** Try to verify with the decoy key at `corpus/quarantine/HOAX_*.asc` (fails)

---

## For Future Researchers

This investigation provides a foundation for:

- Testing new candidates with authenticated corpus
- Running advanced linguistic analysis (beyond basic stylometry)
- Comparing against newly-authenticated Satoshi writing (if surfaced)
- Collaborative investigation (shared verified source material)

---

## The Question

**Was Cicada 3301 a continuation of Satoshi Nakamoto's cypherpunk mission?**

Evidence suggests yes. But it doesn't prove it. That distinction matters.

---

## License & Attribution

Investigation conducted by Cooldash. All Cicada 3301 authenticated messages are public domain. Analysis and methodology are available for independent verification and extension.

---

**See the full investigation:** Read `INVESTIGATION.md` for the complete narrative.
