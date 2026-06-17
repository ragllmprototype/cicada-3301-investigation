# Phase 5 — Stylistic Marker Catalog (Verified Corpus)

**Date:** 2026-06-12
**Input:** the 20 cryptographically verified messages (`corpus/verified_plaintext/`), prose-only (numeric coordinates, SHA hashes, hex image dumps, `.onion`, and `@timestamp` lines stripped before counting).
**Purpose:** convert the qualitative read into quantified, falsifiable markers — and state the sample-size limits plainly so nothing here is over-weighted later.

## SAMPLE-SIZE REALITY (read this first)

- **Total prose tokens: 450 words.**
- Heavy duplication: `end-of-puzzle` == `final-message`; the three 2014 onion messages are identical; the two `cicada-os` messages identical; the two 2017 messages identical. **Unique prose content ≈ 300 words.**
- Several "messages" contain **zero** prose (coordinates, the runic table, the hash block, the hex JPEG).
- Mean sentence length **6.8 words** (max 25, min 1) — the author writes in very short declaratives, which further limits per-sentence signal.

**Implication:** This is far below the ~1,000–10,000-word floor where quantitative authorship attribution (Burrows's Delta, etc.) becomes even weakly reliable. Everything below is **descriptive marker evidence**, not classification. Each marker's evidential weight is capped by its opportunity count (n).

## Markers

### M1 — Double-spacing after sentence period (STRONG, robust)
- **13 of 13** sentence boundaries use `.  X` (two spaces); **0** use single space.
- 100% consistent across 2012, 2014, 2015 (every multi-sentence message).
- Old typewriter / manual-style convention; a stable, low-conscious typographic habit → good individuating potential.
- **Caveat for comparison:** HTML/markdown rendering collapses double spaces. If a candidate's known writing only survives as rendered web text, this marker is **undetectable** in them and the comparison is impossible (not negative). Must use raw/plaintext sources to test M1.

### M2 — British/Commonwealth spelling (REAL signal, but n=1)
- `organisations` appears (2015 message); `organiz-` count = 0.
- Only **one** British-vs-American opportunity exists in the entire corpus, and it resolved British.
- `-our`/`-ise`/other probes: no opportunities arose (n=0), so they neither support nor refute.
- **Weight:** one data point. Suggestive, not decisive. But it is genuinely *discriminating* (unlike anything in the original hypothesis doc) and it points **away from a US-native author writing naturally.**

### M3 — Fixed formulae / house style (MODERATE)
- `Hello.` openings: 5 messages.
- `Good luck` closings: 12.
- `3301` sign-off: 18.
- Consistent ritual framing 2012→2017 → either single author or an enforced style guide. Does not individuate a person, but shows continuity of control.

### M4 — Terse declarative register (WEAK/contextual)
- Mean 6.8 words/sentence; almost no subordinate clauses; calm, instructive tone.
- Common to the whole "cryptic puzzle" genre → low discriminating value (LR ≈ 1).

### M5 — Grammatical slip (WEAK, n=1)
- 2015: *"nor do condone their use"* (elided subject "we").
- Single instance; could be haste or non-native construction. Too thin to weigh, logged for completeness.

## Marker → evidential value summary

| Marker | Robust to web rendering? | Opportunities (n) | Discriminating? | Use in stylometry |
|---|---|---|---|---|
| M1 double-space | **No** (needs raw text) | 13 | potentially yes | test only vs plaintext sources |
| M2 British spelling | **Yes** (survives rendering) | 1 | **yes** | primary cross-candidate test |
| M3 formulae | Yes | many | weak (continuity only) | context |
| M4 terse register | Yes | — | no (genre-wide) | ignore |
| M5 grammar slip | Yes | 1 | unclear | note only |

## Bottom line
The corpus yields exactly **two** markers with real discriminating potential — **M1 (double-spacing)** and **M2 (British spelling)**. M2 is the only one that survives the way most candidate writing is archived (rendered HTML), so it will carry the controlled-stylometry test. Both are thin (n=13 typographic, n=1 spelling). They can *nudge* the posterior; they cannot settle it. Phase 6 tests them against Wei Dai + controls.
