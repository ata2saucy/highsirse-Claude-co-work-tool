# 10 Lower Spadina Condos — Rental Comp Set & SF Verification

**Subject:** 10 Lower Spadina Condos · 10 Lower Spadina Ave, Toronto (Waterfront / **TRREB C01**)
**Developer:** Arkfield · A1 Development — **49 storeys / 511 suites** (vipcondos Step 0)
**Status:** Planning Phase / pre-construction (expected delivery ~2029-30). No floor plans or suite
areas published (vipcondos: "No floor plans currently available") — so "comps" = comparable nearby
condos; the subject unit mix is **estimated** (Data_Summary Q8:Q10 / T3:T6) pending the developer
suite schedule.
**Deliverable:** `10 Lower Spadina Rental Comps _vACTIVE.xlsx` (v2 format, 7 sheets).
**Comp set (user-confirmed 2026-06-16 — all 9 shortlisted picked):** Concord Canada House (2025,
PRIMARY) · Nobu Residences (2024) · The Well (2024) · Ten York (2019) · Forward Condos (2018) ·
Quartz/Spectra (2015) · Library District (2014) · N1 | N2 – CityPlace (2008) · Aqua (2003).

---

## ⚠️ Status of this log — AUDIT & STRUCTURAL FIX (2026-06-16)

This entry documents an **audit-and-structural-fix pass** on the workbook, run in a coding session
**without a signed-in condos.ca / vipcondos browser**. Consequences, stated plainly:

- **No number was changed.** All 39 verified-SF comps + 10 SF-ceiling context rows were carried
  over from the prior run (workbook dated 2026-06-16). Row provenance was reworded from
  "verified this session" to **"verified on condos.ca per-unit registered area (the 2026-06-16
  pull); re-confirm on live page next run"** — honest about when the read happened.
- **The structure was brought to full v2 spec** (see "What changed" below).
- **The live-browser work remains to be run** (see "Browser worklist" at the end): deepen all 9
  comps, recover Quartz/Spectra SF via Route A, and re-confirm every SF on the live page.

All math was re-verified by independent numpy recomputation (matches every block) and static
formula-reference validation (1,195 formulas, 0 errors); `fullCalcOnLoad` is set so Excel
recomputes on open.

---

## Round 2 revisions (2026-06-16, same day — additive)

User review of the run output drove a second pass. **No comp lease/SF number changed**; the only
modelling change is that the subject premium is now *derived*, which intentionally moves the
recommendation. Changes:

1. **Premiums now derived, not guesses.**
   - **C4 (subject rental premium)** is now the live formula **`=C58/C59-1`** = newest comp (Concord
     2025) avg $/SF ÷ all-comp blend − 1 = the **observed vintage premium ≈ +3.4%** (was a typed
     "proposed 10%"). To use a different premium, edit this one cell.
   - **C3 (apartment premium)** set to **0** with a note to derive it (condo $/SF ÷ comparable-age
     apartment $/SF − 1) only when apartment comps are added. No apartment comps here.
   - **Consequence:** recommended subject $/SF moves **$4.98 → $4.68** (Concord basis, C34) and
     **$4.83 → $4.54** (all-comp basis, C35); Output's Subject Site / Subject Property Rent rows
     drop in step. This is the data-derived (conservative) read the user requested.
2. **Subject & Conclusion sheet deleted** — its content was a pure presentation layer (all formulas
   pulled from Data_Summary); the recommendation still lives in Data_Summary (C34) and Output's
   native Subject-Site / Subject-Property-Rent rows. Workbook now **6 sheets**.
3. **Output decluttered** — removed the round-1 bolt-ons (recommendation mirror, comp-quality /10
   scores) **and** the "Other Excluded / Evaluated & excluded" block. The excluded-buildings log is
   preserved here and in building memory, so nothing is lost.
4. **Formatting** — square footage and dollar rents now display **0 decimal places** (e.g. 799 sq ft,
   $3,040); $/SF rates keep 2 dp; premiums/mix show %.
5. **Date Scraped (AO)** now stored as clean text `2026-06-16`, consistent with the Lease Date column.
6. **Deferred to a browser-enabled run:** Floor Plans population from vipcondos (match the Hickory
   mock format) and Route-A validation of the bracket-only SF (Quartz/Spectra, The Well small suites).

Re-verified: **1,160 formulas, 0 errors** (static scan), numpy tie-out matches (new C4 = 3.4%,
C34 = $4.68); 0 leading-operator labels; no dangling reference to the deleted sheet.

---

## What changed in this pass (structural / format — no data changes)

1. **`Date Scraped` column added at AO** on both `RD Condos` and `RD Apartments`; populated
   `2026-06-16` for every existing row (append-only plumbing for future re-runs).
2. **AutoFilter set** on both RD header rows (`A1:AO50` / `A1:AO3`); freeze row 1 retained.
3. **Gridlines hidden** on all 7 sheets (v2 convention).
4. **Confidence fills applied** on `RD Condos` cols B & E: green `E2EFDA` = verified in-window
   (39 rows); orange `FCE4D6` = SF bracket-only / excluded (10 rows).
5. **Three live Data_Summary blocks added** (appended below row 40 — no cross-sheet reference
   shifts):
   - **INPUTS** (A42) — every hard-coded cell + its origin, incl. the LINEST/helper
     verified-rows-contiguous convention (A54).
   - **PREMIUM BASIS** (A56, live) — Newest (Concord) **$4.53/SF** · All-comp **$4.38/SF** ·
     Oldest (Aqua) **$3.90/SF**; observed vintage premiums **+3.4%** (newest÷all) and **+16.3%**
     (newest÷oldest). The proposed subject premium **C4 = 10%** sits inside this range (anchored,
     not asserted).
   - **MIX BASIS** (A65, live) — comp-set bed split **1-Bed 51.3% / 2-Bed 41.0% / 3-Bed 7.7%**
     (1+Den 23.1%) vs the estimated subject mix 63/30/7 (1+Den 18%). Comp set skews more 2-Bed;
     authoritative subject mix = developer suite schedule once published.
6. **Output additions:** a **recommendation mirror** (B30) of the Subject & Conclusion conclusion;
   and a **comp-quality /10 score table** (B43, labelled *Claude judgment*) for the 9 selected
   comps **and** the evaluated-and-excluded buildings.
7. **Output Low/High array ranges** future-proofed `$2:$40 → $2:$120` (safe; MIN/MAX ignore the
   blank/excluded rows). LINEST helper `J:N` and `C2` left at rows 2–40 — they already cover all
   39 verified-SF rows; extending them into blank-SF rows would error (LINEST is blank-intolerant).
8. **Leading-operator labels reworded** (`Output!B34`, `Subject & Conclusion!A20`:
   "+ New-build…" → "Plus — new-build…") so no label parses as a formula.

---

## Coverage table — examined vs verified per building (HONEST; thin buildings flagged)

| Building | Built | condos.ca depth | Examined (this set) | Verified-SF (Include=1) | Status |
|---|---|---|---|---|---|
| Concord Canada House | 2025 | deep (lease-up, very active) | 11 | **10** | ✅ PRIMARY, good depth |
| Nobu Residences | 2024 | moderate | 6 | **6** | ✅ adequate |
| The Well | 2024 | deep (~100+ rentals) | 7 | **3** | ⚠️ THIN — small suites bracket-only (Route A) |
| Ten York | 2019 | deep | 5 | **5** | ⚠️ under 8–12 target |
| Forward Condos | 2018 | deep | 5 | **5** | ⚠️ under 8–12 target |
| Quartz/Spectra | 2015 | deep | 5 | **0** | ⛔ SF bracket-only — 0 verified (Route A pending) |
| Library District | 2014 | moderate | 3 | **3** | ⚠️ thin |
| N1 \| N2 – CityPlace | 2008 | deep | 3 | **3** | ⚠️ under 8–12 target |
| Aqua | 2003 | deep | 4 | **4** | ⚠️ under 8–12 target; sets oldest-vintage floor |
| **TOTAL** | | | **49** | **39** | |

**Date filter (Data_Summary!C1):** 2025-01-01. All 39 verified comps are 2026 leases (well inside).
**The-Well failure mode is present** (deep building, only 3 verified) — flagged for the deepening run.

---

## Per-unit detail (carried from the 2026-06-16 pull; "SF" = condos.ca per-unit registered area)

Format: `unit · beds/baths · parking · SF · leased $ · listed $ · lease date · MLS#`

**Concord Canada House — 23 Spadina Ave (CityPlace/Waterfront; Concord Adex; 72 fl / 1,394 u) — 10 verified**
2505 · 3/2 · 1pk · 908 · $4,300 · $4,300 · 2026-06-12 · C13234234 — 6201 · 2/3 · 1pk · 1,050 · $4,500 · $4,900 · 2026-06-12 · C12939248 — 5611 · 2/2 · 1pk · 718 · $3,500 · 2026-06-08 · C13238978 — 1705 · 2/2 · 1pk · 692 · $3,300 · 2026-06-05 · C13046560 — 312 · 2/2 · 0pk · 736 · $3,050 · 2026-06-09 · C13157296 — 2106 · 1+1/2 · 0pk · 650 · $2,750 · 2026-06-10 · C13217872 — 2608 · 1+1/1 · 0pk · 600 · $2,800 · 2026-06-09 · C12874476 — 1907 · 1/1 · 0pk · 578 · $2,500 · 2026-06-05 · C13219416 — 2212 · 1/1 · 0pk · 505 · $2,300 · 2026-06-04 · C13231928 — 1715 · 1/1 · 0pk · 485 · $2,300 · 2026-06-05 · C13186274.
*Excluded (no registered SF):* 50th row — sub-600 1-bed @ $4,000 listed/leased, flagged outlier (likely furnished/short-term) → Include=0.

**Nobu Residences — 15 Mercer St (King West; Madison Group; 45 fl / 657 u) — 6 verified**
818 · 2/2 · 0pk · 649 · $2,950 · 2026-06-13 · C13117738 — 3910 · 2/2 · 0pk · 799 · $3,395 · 2026-06-08 · C13222970 — 2316 · 2/2 · 0pk · 667 · $3,000 · 2026-05-30 · C13209116 — 1706 · 2+1/2 · 0pk · 799 · $3,300 · 2026-06-05 · C13106892 — 1103 · 1/1 · 0pk · 416 · $2,150 · 2026-06-07 · C13049560 — 1603 · 1/1 · 0pk · 427 · $2,200 · 2026-06-04 · C13110904.

**The Well — 470-480 Front St W (King West; Tridel; 18 fl / 356 u) — 3 verified**
PH-14 · 3/2 · 1pk · 1,069 · $5,500 · 2026-06-12 · C13099798 — 1909 · 1+1/1 · 0pk · 652 · $2,650 · 2026-05-23 · C13044578 — 1812 · 1/1 · 0pk · 558 · $2,500 · 2026-05-27 · C13088234.
*Excluded (bracket-only):* 4 more in-window leases ($2,750 / $2,700 / $2,900 / $5,800) carry MLS brackets, no registered area → Include=0. **Route A (vipcondos key-plates) to recover.**

**Ten York — 10 York St (Waterfront; Tridel; 66 fl / 694 u) — 5 verified**
3905 · 2/2 · 1pk · 830 · $3,695 · 2026-06-08 · C13247834 — 4003 · 2/2 · 1pk · 830 · $3,495 · 2026-06-07 · C13247746 — 5102 · 1+1/2 · 0pk · 710 · $2,900 · 2026-06-08 · C13207690 — 5001 · 1+1/2 · 0pk · 779 · $2,850 · 2026-06-06 · C13208742 — 4208 · 1/1 · 0pk · 575 · $2,750 · 2026-06-08 · C13235092.

**Forward Condos — 70-90 Queens Wharf Rd (CityPlace; Concord Adex; 30 fl / 625 u) — 5 verified**
906 · 3/2 · 1pk · 928 · $4,200 · 2026-06-15 · C13212972 — 1109 · 2/2 · 1pk · 802 · $3,600 · 2026-06-07 · C13220162 — 1501 · 1+1/1 · 1pk · 579 · $2,680 · 2026-06-09 · C13229088 — 2601 · 1+1/1 · 0pk · 579 · $2,400 · 2026-06-06 · C13221156 — 1801 · 1/1 · 0pk · 507 · $2,250 · 2026-06-05 · C13217472.

**Library District — 170 Fort York Blvd (CityPlace; 29 fl / 364 u) — 3 verified**
2112 · 1+1/1 · 0pk · 585 · $2,400 · 2026-06-10 · C13220980 — 1008 · 1/1 · 0pk · 492 · $2,200 · 2026-05-29 · C13177424 — 309 · 2/1 · 1pk · 686 · $2,795 · 2026-05-25 · C13159384.

**N1 | N2 – CityPlace — 15 Fort York Blvd (CityPlace; 42 fl / 568 u) — 3 verified**
1601 · 1+1/1 · 0pk · 587 · $2,600 · 2026-06-10 · C13207458 — 1910 · 2+1/2 · 1pk · 914 · $3,900 · 2026-06-09 · C13226098 — 919 · 1/1 · 1pk · 630 · $2,415 · 2026-06-05 · C13170188.

**Aqua — 410 Queens Quay W (Waterfront; 16 fl / 273 u) — 4 verified**
1103 · 2/2 · 1pk · 929 · $4,000 · 2026-06-08 · C13230806 — 509 · 2/1 · 2pk · 842 · $3,450 · 2026-05-19 · C13136720 — 1017 · 2/1 · 1pk · 840 · $3,000 · 2026-05-01 · C13032848 — 605 · 1/1 · 0pk · 562 · $2,030 · 2026-04-03 · C12929788.

**Quartz/Spectra — 75-85 Queens Wharf Rd (CityPlace; 41 fl / 943 u) — 0 verified (SF ceiling)**
5 in-window leases pulled (4606 $4,100 · 2512 $3,500 · 815 $3,200 · + 1+1 $2,700 · 1-bed $2,300), **all bracket-only on condos.ca** → SF blank, Include=0. **Route A (vipcondos key-plates) to recover exact interior SF.**

---

## Coverage & conclusion (re-verified independently 2026-06-16)

- **1,195 formulas, 0 errors** (static reference validation; numpy independent recomputation of
  every block matches exactly; `fullCalcOnLoad` set).
- **Parking adjustment (Data_Summary!C2, LIVE LINEST over 39 verified leased rows): $26.05/spot/mo**
  — numpy OLS cross-check identical. (Low for downtown — most verified comps lease without parking.)
- **Data_Summary:** 39 included · ALL CONDOS avg **696 SF · $3,039.87/mo · $4.38/SF** · mix-weighted
  Concord $/SF **$4.524** → +10% premium → **RECOMMENDED subject $/SF $4.977** (≈ $3,484/mo @ 700 SF).
  All-comp basis **$4.388** → +10% → $4.826 (conservative floor). No prior model (new subject).
- **Output (untrended, net of parking):** 39 txns · 696 avg SF · $3,028.52 adj rent · $4.369 net PSF
  → ×1.10 → **Subject Site (Untrended) $3,331.37/mo · $4.806/SF**.
- **TRREB Q1-2026 (read 2026-06-16):** Toronto **C01** 1BR $2,438 / 2BR $3,431 / 3BR $4,591 · City of
  Toronto 1BR $2,292 / 2BR $3,091 / 3BR $3,866 · GTA YoY −4.1% / −3.2% / −2.7%.

---

## Browser worklist (run in Claude in Chrome, signed in to condos.ca + vipcondos)

1. **Deepen all 9 comps to 8–12 verified-SF leased comps** across bed types, in-window (≥2025-01-01).
   Priority (currently thin): **The Well, CityPlace N1|N2, Library District, Aqua, Ten York, Forward.**
   condos.ca → building → Price History → **Rented** → "View full listing history" → "Load 15 more"
   past the filter with a buffer; dedupe by href+text; exclude `-P`/`-S` partials.
2. **Quartz/Spectra → Route A:** pull vipcondos developer key-plates to recover exact interior SF for
   its units; set Include=1. Same for The Well's bracket-only small suites.
3. **Re-confirm each carried SF on the live condos.ca unit page this session**; re-confirm subject
   identity on vipcondos (511 suites / 49 storeys / C01); re-read the latest TRREB Rental Market Report.
4. **Append-only:** new rows get today's `Date Scraped`; place verified-SF rows contiguously in the
   top block and extend the LINEST helper `J:N` + `C2` range to the new last verified row (never
   include blank-SF rows). Extend nothing else — Output Low/High already reach row 120.

## Data ceiling / definitive source
condos.ca per-unit figures are calculated registered areas (precise for modern TSCC corps; bracket
-only for some buildings — Quartz/Spectra, The Well small suites). Leased history is login-gated
(signed-in session required). Definitive subject areas: the developer suite-area schedule / registered
declaration once 10 Lower Spadina is published.
