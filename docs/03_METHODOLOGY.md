# Methodology (Falsification-First) — Wei Dai / Cicada 3301

**Replaces** the confirmation-structured original. The job is not to *build the case for* Wei Dai; it is to *try to break* the hypothesis and report whether it survives.

## 0. The claim, stated falsifiably

> **H1:** Wei Dai is a principal architect of Cicada 3301.
> **H0 (null):** Wei Dai is not; 3301 was run by some other individual/group.

A hypothesis that cannot specify what evidence would *kill* it is not an investigation. So, up front:

**H1 is falsified / strongly weakened if any of these hold:**
- A genuine (genuine-key-signed) 3301 message exists during a window when Wei Dai is documented elsewhere in a way incompatible with running the op — and we never check. (We must check.)
- Stylometry on verified 3301 prose diverges significantly from Wei Dai's known corpus.
- A different, better-supported author emerges (someone with equal/greater trust, skill, opportunity, and *positive* trace evidence).
- The only "evidence" for H1 turns out to be non-discriminating (true of thousands of people). ← **this is currently the case; see §3.**

## 1. Bayesian frame (so confidence numbers mean something)

Posterior odds = prior odds × Π(likelihood ratios).

**Prior.** Before any evidence, how many people could plausibly be a 3301 architect? The candidate pool — competent cryptographers with cypherpunk alignment and the opportunity/anonymity discipline, c. 2011 — is conservatively **hundreds to low thousands**. So a flat prior P(H1) ≈ 0.001–0.005. Wei Dai is a *distinguished* member of that pool, so bump it generously: **prior P(H1) ≈ 0.01–0.03**. That is the honest starting point — not 50%.

**The only thing that raises the posterior is a likelihood ratio > 1** — evidence *more expected if Wei Dai did it than if he didn't*. Evidence equally expected under H0 has LR ≈ 1 and **must not** move our confidence, however thematically satisfying.

## 2. Evidence ledger (with likelihood ratios, not vibes)

| Claimed evidence | More expected under H1 than H0? | LR | Verdict |
|---|---|---|---|
| Cypherpunk ideology of 3301 (May/Hughes language) | True of the whole candidate pool | ~1 | non-discriminating |
| Wei Dai has crypto expertise (b-money, Crypto++) | True of the whole pool by construction | ~1 | non-discriminating |
| Wei Dai contacted by Satoshi pre-2008 | Real, but shared with Back, Finney, & others; doesn't bear on 3301 | ~1–1.2 | weak at best |
| "Employment gap / ghost period" 2010–2011 | **Base-rate trap**: private engineers default to no public footprint. Most of the pool also has gaps. | ~1 | **non-evidence** |
| 3301 launched 8.5 months after Satoshi's exit | Post-hoc window; many people fit any 8-month window | ~1 | **non-evidence** |
| PGP key is RSA-4096 / AES-256 / GnuPG defaults | Stock GnuPG output; millions identical (see 02_PGP_FORENSICS) | ~1 | **non-evidence** |
| "Mac as opsec platform" | Speculative; no artifact supports it; also true of millions | ~1 | **non-evidence** |

**Result:** after auditing, essentially **every** item in the original document is LR ≈ 1. Multiplying a prior of ~0.02 by a string of 1's leaves the posterior at **~0.02**. The original's "Timeline coherence 95% / Expertise 95%" figures confused *consistency* (H1 doesn't contradict the facts) with *evidence* (the facts are more likely under H1). Consistency is necessary but worth almost nothing — H0 is equally consistent with all of it.

## 3. Why "consistency" felt like proof (the core error to avoid)

Every fact in the original is of the form *"Wei Dai could have done this."* None is of the form *"this is something we'd see if Wei Dai did it but not otherwise."* A narrative built entirely from could-haves will fit any sufficiently skilled candidate. That is confirmation by availability, not inference. The fix is mechanical: **for each new fact, ask "what's the probability of seeing this if H0 is true?" If it's about the same as under H1, discard it as evidence.**

## 4. What WOULD be real evidence (LR meaningfully ≠ 1)

Ranked by attainability:
1. **Stylometry**: verified 3301 English prose vs. Wei Dai's LessWrong corpus, with a *control set* of other candidate authors. A strong, control-beating match would be LR > 1; a mismatch would be LR < 1 (falsifying). **This is the single most testable lever and should be the next analytic phase.**
2. **Cross-source opportunity check**: documented Wei Dai activity timestamped *against* genuine 3301 release moments — looking specifically for *conflicts* (alibi-style falsification), not confirmations.
3. **Infrastructure traces**: registration/hosting/OPSEC metadata in *authenticated* 3301 artifacts that points to or away from any individual. (Note: none found so far; the only "stack" evidence examined was non-discriminating.)
4. **Tier-1** (direct testimony, leaked logs): not available; do not pretend otherwise.

## 5. Procedural rules for the rest of the investigation

1. **Authenticate before analyze.** Only genuine-key-signed material enters analysis. (Phase 4 already caught one decoy posing as the key itself.)
2. **State the LR for every fact** before it's allowed to change confidence.
3. **Run a control set.** Any test applied to Wei Dai is applied identically to ≥2 other candidates (e.g., Back, plus a "generic skilled cypherpunk" baseline). A test that "confirms" everyone confirms no one.
4. **Report falsification attempts, including failed ones.** A surviving hypothesis is only meaningful if we genuinely tried to kill it.
5. **No real-person assertion beyond the evidence.** This concerns a living, private individual. Output language stays at "hypothesis, currently unsupported by discriminating evidence," never "likely" or "architect," absent LR>1 findings.

## 6. Current honest confidence

| Quantity | Original doc | Audited |
|---|---|---|
| P(Wei Dai is a 3301 architect) | ~30–95% (mixed) | **~2% (≈ prior; no discriminating evidence yet)** |
| Quality of evidence gathered | "strong, coherent" | consistent but non-discriminating (LR≈1 across the board) |
| Most promising next test | code/Crypto++ matching | **stylometry with controls** (code-matching premise refuted) |

**Bottom line:** The hypothesis is *not yet supported* — not refuted either, just unsupported by anything that distinguishes Wei Dai from the field. The path forward is evidence with LR ≠ 1, starting with controlled stylometry on the authenticated corpus.
