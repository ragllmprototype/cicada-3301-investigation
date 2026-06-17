# Phase 6 — Controlled Stylometry (Markers vs Candidates)

**Date:** 2026-06-12
**Test:** do Cicada's two discriminating markers (M1 double-spacing, M2 British spelling) appear in Wei Dai's writing or in control candidates' writing?
**Controls:** Adam Back (British), Nick Szabo (American), Hal Finney (American) — all cypherpunk-pool members of comparable plausibility.
**Sources:** Wei Dai b-money (raw plaintext, weidai.com); Adam Back hashcash announce (raw, hashcash.org) + hashcash paper; Szabo Shelling Out + Bit Gold; Finney RPOW (Nakamoto Institute). Raw plaintext sources allow M1; HTML sources allow only M2 (rendering destroys double-spaces).

## Data

| Author | words | `. X` single | `.  X` double | British spell | American spell | verdict |
|---|---|---|---|---|---|---|
| **CICADA (ref)** | 450 | **0** | **13** | `organisations` (1) | 0 | British + double-spaced |
| Wei Dai (b-money, RAW) | 1358 | **51** | **0** | 0 | `-ize` (1) | **American + single-spaced** |
| Adam Back (announce, RAW) | 1156 | 12 | 1 | `optimised` (1) | 0 | **British** + mostly single |
| Nick Szabo (Shelling Out) | 13489 | n/a | n/a | ~0 real | `-ize` (50) | American |
| Nick Szabo (Bit Gold) | 1047 | n/a | n/a | 0 | `-ize` (1) | American |
| Hal Finney (RPOW) | 449 | n/a | n/a | 0 | 0 | insufficient |

(Szabo's `-ise` hits — *appraising, surprising, raising* — are false positives, not British `-ise` verbs.)

## Findings

### M2 (British spelling) — points AWAY from Wei Dai, mildly TOWARD Back
- Cicada uses British spelling. Wei Dai writes **American** (`-ize`, zero British across 1,358 words). Szabo and Finney also American.
- The **only** candidate matching Cicada's British spelling is **Adam Back**, the only UK-born member of the pool.

### M1 (double-spacing) — directly contradicts Wei Dai
- Cicada: 13/13 double-spaced (100%). Wei Dai: **0/1358 opportunities double-spaced**. A clean contradiction.
- Back is also mostly single-spaced (12:1), so M1 matches *no* candidate cleanly — the double-spacing may be a Cicada-specific operational style. But it is unambiguous that it is **not** Wei Dai's habit.

## Honest weighting (do not overclaim)

The markers are real but **thin**, and several caveats cap their force:

1. **n is tiny.** Cicada offers exactly **one** British-vs-American opportunity and 13 spacing instances; the b-money sample is from **1998** (14 years before Cicada — habits drift, though spelling-nationality rarely flips).
2. **British spelling ≠ Adam Back specifically.** It excludes US-native natural writers (Wei Dai, Szabo, Finney) but is shared by ~2 billion Commonwealth-English writers. It could also be **deliberate obfuscation** by anyone, including a US author. So it is *exclusionary* evidence against Wei Dai, **not** positive identification of Back.
3. **M1 contradicts everyone**, so it functions only as a (weak) strike against Wei Dai, not as attribution.

### Likelihood ratios (conservative)
- L(British spelling | Wei Dai) ≈ low (he writes American; requires deliberate disguise) vs L(British spelling | not-Wei-Dai pool) ≈ moderate. Conservative **LR ≈ 0.3–0.5** against H1.
- M1 contradiction: a further soft factor **≈ 0.5–0.7** against H1.
- Combined: roughly a **2–4× reduction** in the odds for the Wei Dai hypothesis.

## Net effect on the hypothesis

| | before Phase 6 | after Phase 6 |
|---|---|---|
| P(Wei Dai is a 3301 architect) | ~2% (prior; no discriminating evidence) | **~1%** (first discriminating evidence is mildly *disconfirming*) |

**Conclusion:** The investigation's first genuinely discriminating evidence does not support Wei Dai — it **weakens** the hypothesis. Cicada's verified prose is British-spelled and double-spaced; Wei Dai's authenticated prose is American-spelled and single-spaced. If the thin signal points anywhere in the pool, it points at the British member (Back), but the honest reading is *exclusionary*, not an identification. This is exactly the outcome a falsification-first method is supposed to surface: a beloved hypothesis, tested against real data, going **down** rather than up.
