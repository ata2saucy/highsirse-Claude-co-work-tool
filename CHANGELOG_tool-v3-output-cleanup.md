# Changelog — `tool-v3-output-cleanup` (2026-06-17)

Cleaner, more defensible institutional rental-comp workbook. Output structure moved from the
older seven-sheet shape to the **six-sheet v3 standard**; formulas hardened so nothing ships with
`#REF!`/`#VALUE!`; provenance and number formatting tightened. **No comp data was re-pulled and no
verified figure changed** — every reported number still traces to the condos.ca pages logged in
the verification file.

## Files changed

| File | What changed |
|---|---|
| `10 Lower Spadina Rental Comps _vACTIVE.xlsx` | Cleaned to v3 (deliverable). See workbook changes below. |
| `v2 hickory mock comp.xlsx` | Template regenerated to v3 (six sheets, live LINEST, derived mix, basis blocks, SF-validation columns, 18-col Floor Plans, ALL CONDOS/ALL APARTMENTS bands). |
| `tools/qa_workbook.py` | **New.** Reusable QA gate: recalcs a workbook (whole-column ranges bounded) and asserts the v3 acceptance checklist; numpy cross-checks the parking LINEST. |
| `CLAUDE.md` | RD sheets now 45 cols A:AS (Date Scraped + four SF-validation columns); Floor Plans 18-col session-log spec; C3-unused note convention; robust-parking formula; **QA gate / acceptance checklist** section; mock-status note updated to "regenerated to v3". |
| `README.md` | Six-sheet structure + "no `/10` score" stated; workbook references updated (mock = v3 skeleton; 10 Lower Spadina = v3 worked example; Hickory = pre-v3); `tools/qa_workbook.py` listed. |
| `HANDOFF.md` | Output line updated to 45-col A:AS RD sheets + 18-col Floor Plans + QA-before-delivery. |
| `condo_sqft_verification_method_1.md` | RD = 45 cols A:AS with SF-validation columns; Floor Plans = 18-col session log; date/`yyyy-mm-dd` wording. |
| `building_memory/10_lower_spadina.md` | Append-only 2026-06-17 entry recording the v3 cleanup (prior dated record left intact). |
| `10_Lower_Spadina_Comps_Verification.md` | Append-only "v3 output cleanup (2026-06-17)" section. |

## Workbook changes (10 Lower Spadina + applied to the mock template)

1. **Deleted `Subject & Conclusion` sheet.** Its recommendation summary (recommended `$/SF`, rent
   by suite type, custom suite-size input, source bridge, TRREB context, confidence legend, notes)
   is **folded into the Output tab**. Final sheet set: Output · Building Summary · Data_Summary ·
   RD Condos · RD Apartments · Floor Plans.
2. **Removed the Output `/10` comp-quality score table** and the "mirror of Subject & Conclusion"
   wording. Comp roles are prose only (the "Other Excluded" block); no numeric judgment score.
3. **Deleted the Data_Summary `INPUTS` block** (incl. a note cell that began with `=` and parsed as
   a broken formula). **PREMIUM BASIS** and **MIX BASIS** kept (relocated, internal refs fixed),
   plus an **APARTMENT PREMIUM BASIS** note.

## Formulas changed (the reported `#REF!` / `#VALUE!`)

- **Parking adjustment `Data_Summary!C2`** — rebuilt as a guarded live LINEST over the verified-SF
  leased helper block: `=IFERROR(IF(AND(COUNT($N$2:$N$40)>=10,(MAX($K$2:$K$40)-MIN($K$2:$K$40))>0),INDEX(LINEST($N$2:$N$40,$J$2:$M$40,TRUE(),FALSE()),1,3),0),0)`.
  Returns `0` (with note `0 — insufficient parking variation in included comp set`) when too few
  rows or no parking variation; can never leave `#REF!`. Still **$26.05/spot/mo** for this set.
- **Subject mix `H2:H4`** — `=IFERROR(IF($Q$5>0,$Q$2/$Q$5,$Q$8),$Q$8)` (and H3/H4). Falls back
  cleanly to the manual mix `Q8:Q10` (**63 / 30 / 7**, with the 45 / 18 / 30 / 7 split visible in
  the Output 4-way mix) — no `#VALUE!` from COUNTIFS against blank/text plan rows.
- **Weighted comp `$/SF` `C31` (Concord basis) / `C32` (all-comp basis)** — renormalise over the
  bed buckets that have data, so an empty bucket can never produce `#VALUE!`. `C34`/`C35`
  (recommended / conservative) wrapped in `IFERROR`.
- **Apartment premium `C3` = 0** with dynamic note `Unused — no apartment comps in selected set`
  (numeric, so `RD Apartments!AN` stays valid). **Subject premium `C4` = 10%** with a judgment note
  anchored to PREMIUM BASIS (observed vintage spread +3.4% to +16.3%), flagged for user confirmation.
- **Output Low/High** per-bed array formulas re-expressed with a sentinel false-branch + an empty-
  bucket guard (no spurious `$0.00`).

## RD Condos / RD Apartments

- Added **Date Scraped (AO)** + four SF-validation columns: **SF Verification Status (AP)**,
  **SF Source Type (AQ)**, **SF Source / URL (AR)**, **SF Explanation / Not Validated Reason (AS)**.
  45 columns A:AS, identical on both sheets.
- 39 verified rows → "Verified registered area / condos.ca registered area"; 10 SF-ceiling rows →
  "Bracket only" with the exclusion reason and `Include = 0` (no bracket midpoint ever placed in
  `Sq Ft.`). Quartz/Spectra (0 verified) and the bracket-only The Well units are clearly excluded.
- Dates (`Date`, `Lease Date`, `Date Scraped`) display **`yyyy-mm-dd`** (no Excel serials). SF and
  counts whole-number `#,##0`; `$/SF` 2 decimals.
- RD Apartments holds no comps → clean note "No purpose-built rental apartment comps selected for
  this subject"; structure kept identical to RD Condos; empty rollups resolve to 0 / "".

## Floor Plans

- Rebuilt to the **18-column session log** (Building Name · Building Address · Building City ·
  Subject/Comp · Source Site · Source URL · Date Read · Suite/Plan Name · Beds · Baths · Interior SF
  · Exposure · Floor Band · Stack/Line · Balcony/Terrace · Notes · Used For Unit(s) · Verification
  Tier). Subject "no plans published" row kept; a NOTE row records that comp SF came from condos.ca
  registered areas (Route B) and **no VIPcondos plans were opened** — so no comp plan rows were
  invented.

## QA summary — acceptance checklist (both workbooks: 22/22 PASS, 0 error cells)

| Check | 10 Lower Spadina | mock |
|---|---|---|
| Exactly the 6 required sheets, no `Subject & Conclusion` | ✅ | ✅ |
| Output: no `score` / `/10` / `comp-quality` / judgment / mirror text | ✅ | ✅ |
| Data_Summary keeps PREMIUM BASIS + MIX BASIS; INPUTS removed | ✅ | ✅ |
| No visible `#REF!` / `#VALUE!` / `#DIV/0!` / `#N/A` / `#NAME?` (recalc clean) | ✅ | ✅ |
| Parking adjustment = valid coefficient or 0 w/ reason | ✅ ($26.05) | ✅ ($136.99) |
| Subject mix = clean percentages | ✅ (63/30/7) | ✅ |
| Apartment premium unused/0/N-A when no apartment comps | ✅ | ✅ |
| Subject premium has derivation / judgment note (not asserted as fact) | ✅ | ✅ |
| SF/counts 0 decimals; `$/SF` clean; dates `yyyy-mm-dd` | ✅ | ✅ |
| Every row without exact SF → Include=0 + reason | ✅ | ✅ |
| Floor Plans logs subject + 18-col layout | ✅ | ✅ |
| RD Condos and RD Apartments structurally identical (45 cols) | ✅ | ✅ |
| Recommendation math ties back (numpy: rec $/SF $4.977, all-comp $4.388) | ✅ | ✅ |

Run `python tools/qa_workbook.py "<workbook>.xlsx"` to reproduce.

## Assumptions still requiring user confirmation

- **Subject premium C4 = 10%** is a judgment lever (not user-confirmed). It sits inside the live
  PREMIUM BASIS vintage spread (+3.4% newest÷all-comp to +16.3% newest÷oldest); confirm or adjust.
- **Subject unit mix 63 / 30 / 7** (1BR-incl-den / 2BR / 3BR; 4-way 45 / 18 / 30 / 7) is the
  estimated/planned mix — 10 Lower Spadina is pre-construction with no published plans. Supersede
  with the developer suite schedule when published.
- **Suite count 511 / 49 storeys** from vipcondos Step 0 — re-confirm on the live page.

## Remaining blockers / notes

- **Browser deepening worklist (unchanged):** thin buildings (The Well, CityPlace N1|N2, Library,
  Aqua, Ten York, Forward) to deepen to 8–12 verified comps; Quartz/Spectra exact SF via Route A.
  Requires a signed-in condos.ca + vipcondos browser session.
- **SOP PDFs** (`Arkfield_Comp_Tool_Handoff_SOP.pdf`, `Rental_Comp_Tool_SOP.pdf`) were **not** patched
  (no markdown source in the repo; per the change spec, PDFs are not hand-edited). Regenerate them
  from the updated `HANDOFF.md` / `CLAUDE.md` if the branded one-pagers are reissued.
- **`Hickory Rental Comps _vACTIVE.xlsx`** is left in its pre-v3 form (single `Raw Data` sheet,
  `Subject & Conclusion` present) as a historical worked example; the v3 worked example is the
  10 Lower Spadina workbook.
