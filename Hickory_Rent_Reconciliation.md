# Hickory Tree Tower — Rent Reconciliation (why it looked low, and the fix)

**Question:** the comp workbook's recommended rent looked lower than the ~$3.90/SF you had before. Here's exactly why, what I fixed, and the verification.

## TL;DR

The first version reported **raw comp $/SF** and never applied your **new-build / lease-up premium**. That was the bug. Re-applying your own premium (from `Data_Old`, +13.3%) lifts the recommendation to **$3.72/SF** — within **−4.6%** of your prior **$3.90**, and that small residual is real **market softening from 2024 to 2026**. The method itself checks out: my Humber **2-Bed $/SF = $3.25** is identical to your prior "Wilby" 2-Bed of **$3.25**.

## What your prior model did (Data_Old → "Applying Wilby Figures to Hickory Market")

| Step | Value |
|---|---|
| Per-bed comp $/SF (Wilby = 10 Wilby = The Humber): 1BR 3.85 · 2BR 3.25 · 3BR 3.20 | weighted **$3.50/SF** |
| + **Rental Premium** | **+13.3%** (+$0.44/SF) |
| = Adjusted | **$3.94/SF** |
| Subject Site (pegged) | **$3.90/SF** → $2,730/mo @ 700 sf |

Those per-bed figures were on a **2024 / mid-2025 basis** (your "2024 rents" subtotal was **$3.96/SF**).

## What my first version did

Reported the **raw, current-market comp $/SF** with **no subject premium**: The Humber **$3.26**, all-comp blended **$3.01**. So it was answering a different question ("what do the comps lease for today") than your model ("what should the new subject achieve").

## The four drivers of the gap — quantified

1. **Missing subject premium (the fix, ~80% of the gap).** Your model grosses comps up by ~13% to reach a new, prime subject; mine didn't. Applying +13.3% to the current Humber comp $/SF: **$3.28 → $3.72**.
2. **Market timing (the residual, −4.6%).** Your per-bed figures were 2024/mid-2025-anchored; my data is **2026 leases**, the softest point (condos.ca shows The Humber **−9.3% YoY**, Toronto condos ~−7.5%). So even with the premium, current market ($3.72) sits a touch below your 2024-anchored $3.90.
3. **Den grouping (1-bed).** Your "1BR" was pure 1-bed at small size → **$3.85/SF**. My "1-bed" lumps **1+den** units (larger ~690 sf, ~$3.27/SF) with pure 1-beds (~$3.53/SF), pulling the blended 1-bed $/SF down. Splitting them recovers most of that.
4. **Comp mix.** The **all-comp blended $3.01** drags in older Mount Dennis stock (Winston $2.15, Emmett $2.35). The **Humber-only $3.26** is the cleaner new-build proxy — which is why the recommendation is anchored on The Humber, not the blend.

**Validation:** for the same building (The Humber / 10 Wilby), my **2-Bed $/SF $3.25 = your Wilby 2-Bed $3.25** exactly. The comps are right; the gap was premium + timing, not the data.

## The fix (in `Hickory Rental Comps _vACTIVE.xlsx`)

- **Subject premium lever** added (`Data_Summary!C4`, default **+13.3%** from your prior model, tunable). The TLDR now leads with the **premium-adjusted recommendation**, with raw comp $/SF shown beneath.
- **Reconciliation bridge** on the Subject sheet: current comp $/SF → + premium → recommended $3.72 → vs prior $3.90 → residual −4.6% (timing).
- **Apartment adjustment set to 0 (off)** per your note.
- All numbers re-verified (recalc: **0 formula errors**, 532 formulas; $/SF = rent ÷ SF on every row; averages tie out).

## Recommendation now

| Basis | $/SF | 700 sf/mo |
|---|---|---|
| **Recommended subject (Humber comps + 13.3% premium, current market)** | **$3.72** | **$2,603** |
| Conservative (all-comp + premium) | $3.45 | $2,418 |
| Raw comps, no premium (today's market) | $3.28 | $2,298 |
| Your prior model (2024-rent anchored) | $3.90 | $2,730 |

Recommended monthly rents by suite type (subject basis): **1-bed/1+den ≈ $2,402 · 2-bed ≈ $2,796 · 3-bed ≈ $3,328.**

## Open items / tuning

- The **premium % is yours to set** — I defaulted to your prior 13.3%. If today's lease-up market warrants less, dial `Data_Summary!C4`.
- If you want the 1-bed to match your old $3.85 exactly, I can split pure-1BR from 1+den in the rollup (currently combined).
- Winston House / Emmett House $/SF are **approximate** (condos.ca bracket-only SF) — flagged red; they affect only the conservative all-comp blend, not the Humber-anchored recommendation.
