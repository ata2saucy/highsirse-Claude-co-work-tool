# Hickory Tree Tower — building memory (stable facts only; NO reportable SF)

> SUBJECT site (your Arkfield development), not a comp. Pre-construction.

## Identity
- Marketing name: Hickory Tree Tower Condos
- Developer: Arkfield · A1 Development · A1 Capital — Architect: DIALOG
- Address(es): 1736–1746 Weston Road, Toronto — Weston (Walk 71 / Transit 80)
- Storeys / total units: 38 storeys / 446 suites
- Status: Planning Phase / Pre-Construction (as of 2026-06)
- Unit mix: planned 30/16/45/9 (1B/1+Den/2B/3B) → Data_Summary H2:H4 3-way = 46/45/9 (den folded into 1BR). **Sourced input, not derived** — subject has no published plans (none on vipcondos as of 2026-06), so it cannot derive from Floor Plans (which holds only the comp, The Humber). Lives as the manual sourced mix in the workbook's Subject Unit-Mix Derivation block (Q8:Q10, source noted in Q7). **Confirm 30/16/45/9 against the developer suite schedule** — origin of these shares not yet primary-sourced.

## Working sources
- vipcondostoronto.net: /toronto/hickory-tree-tower-condos-4180 — building stats + "Nearby Market" comp list. **No floor plans published yet** ("No floor plans are currently available"); SIZE RANGE = N/A. Re-confirmed 2026-06-09.
- condos.ca: subject not yet a building page with rentals (unbuilt).

## PROCESS (updated 2026-06-09): shortlist gate
"Find comps" for this subject = **shortlist → user picks → only then pull comps** (see CLAUDE.md "Comp-building selection" step 3). Do not pull per-unit comps for an unconfirmed set.

## Comp shortlist (standing) — present these for selection
- **The Humber** — 10 Wilby Cres (2023, 232u, ~250 m) — PRIMARY new-build benchmark. condos.ca slug `the-humber-10-wilby-crescent-10-wilby-cres`, buildingId 6502. SF verifiable per-unit. See `the_humber.md`.
- **River Ridge** — 1–3 Hickory Tree Rd (1991, 19fl/413u, Rockport, MTCC-983, ~450 m) — slug `river-ridge-1-hickory-tree-rd-3-hickory-tree-rd`. Best secondary: ~12 recent rentals, exact per-unit SF visible. Found 2026-06-11; offered, not yet selected.
- **River Hill** — 2088 Lawrence Ave W (2006, 135u) — slug `river-hill-2088-lawrence-ave-w`. SF verifiable per-unit; thin leased volume.
- **Weston On The Humber** — 2464 Weston Rd (2007, 10fl/162u, Arten) — slug `weston-on-the-humber-2464-weston-rd`. Micro-suites 343–957sf, ~5 leases $1,400–1,850 — different segment; brackets on history.
- **The Winston House** — 75 Emmett Ave (1976, 349u) — slug `the-winston-house-75-emmett-ave`. SF condos.ca **bracket-only → approx**.
- **Emmett House** — 85 Emmett Ave (1974, 275u) — slug `emmett-house-85-emmett-ave`. SF condos.ca **estimate → approx**.
- **West22 / WestonHub** — 22 John St (2020, 30fl/377u, Rockport) — slug `west22-22-john-st`. **Purpose-built rental, 0 MLS records** (off-MLS leasing); closest vintage to subject; only usable as labelled asking-rent evidence + PBR premium. (condos.ca page SEO text wrongly says King West — it IS the Weston building.)
- STANDING REJECTS: Humberview Heights (40 Richview, Etobicoke — 0 rentals) · Sidney Belsey 50–74 / W Towns / Riverboat Landing / Pioneer & Charlton Settlement (stacked towns — wrong product) · Weston Park (no single condo building) · The Charlton Residences — 1695-1705 Weston Rd (precon, Old Stonehenge, 25fl/240u — 0 rentals; **future comp once leasing**) · Weston Gate — 2130 Weston Rd (1978, 75u, ~2 leases/yr, bracket SF) · Eglinton Park Place — 3559 Eglinton W (1988, ~2.3 km, thin — River Ridge dominates) · Lexington on The Green (2008 low-rise towns) · RioCan Hall 126 John (precon) · 2255/2275 Weston, 1530 Weston, 38 Gibson (non-condo/partial units) · "89 Church St" rows in Weston feeds (downtown mis-bucket — C-prefix MLS).

## Workbook format (LOCKED 2026-06-09, v3)
Deliverables use the user's **v3 reference layout** (4-building grouped Output): six sheets — Output (grouped: "Lawrence & Jane St" primary = Humber + River Hill; "Other Excluded" = Winston + Emmett; count-weighted SUMPRODUCT averages; PBR premium rows = Data_Summary!C4; unit-mix table 1B Q="1" / 1+Den Q="1+1" / 2B H="2" / 3B H="3"; building totals = mix 30/16/45/9 × 446) · Subject & Conclusion · Building Summary · Data_Summary (**C2 = LIVE LINEST** over J:N helper block — extend block + range when leased rows change) · Raw Data (40 cols A:AN) · Floor Plans. Full spec in `CLAUDE.md` → "Output format". Gotchas: recalc toolchain has **no MINIFS/MAXIFS/AGGREGATE** — Output Low/High use `SUMPRODUCT(MIN/MAX(IF(...)))`; TRREB district for this subject = **W04**; date filter lever currently 2025-05-01 (user's choice).

## Run log
- **2026-06-11 (v5 REDO): full method re-run.** Fresh area shortlist (Weston + Mount Dennis swept; River Ridge + West22 newly evaluated and offered); **user re-selected THE HUMBER ONLY**; filter kept 2025-05-01; vACTIVE overwritten in place. All 26 leased + 2 rooms re-opened per-unit (zero deltas); 2 new actives added (1102 $2,400 W13243038 · 1004 $2,200 W13430024 — Raw Data now 33 rows); Output Low/High ranges extended to $34. **v4 slips fixed:** 1801-P had 1907's description+bracket (restored; rooms bracket 700-799); 1907 caveat (600-699 vs calc 715) reinstated on its own row; 405 bracket corrected 700-799 → **800-899**. TRREB Q1-2026 re-read (still latest): W04/City/YoY unchanged. 664 formulas, 0 errors; LINEST C2 $132.33 = numpy; rec $3.71/SF, residual −4.8%.
- 2026-06-03: full 4-building set (34 leased + 3 active) → first `Hickory Rental Comps _vACTIVE.xlsx`.
- **2026-06-09 (REDO): shortlist presented per new gate; user selected The Humber ONLY, trailing-12-month window.** 21 leased included + 5 older + 4 active; workbook rebuilt. New comp found: Humber unit 101 (3B, leased 2025-12-19). River Hill / Winston / Emmett offered, not selected — not pulled.
- **2026-06-09 (FORMAT v2): rebuilt the workbook 100% in the user's v2 mock format** (adds Output page w/ PBR-premium framing, unit-mix weighted subject rent, regression block, TRREB Q1-2026 table). Recommended subject $/SF $3.71 (mix-weighted Humber $3.27 × 1.133).
- **2026-06-09 (v4 FINAL): user instruction — comp set = THE HUMBER ONLY.** RH/Winston/Emmett rows removed everywhere (logged as REMOVED in Output → Other Excluded); 31 Raw Data rows, 22 included; C2 live LINEST = **$132/spot** (26 Humber leases); raw $3.23/SF, rec subject $3.71/SF, Subject Site untrended $2,632 · $3.51.
- **2026-06-09 (v3): user's reference file reinstated the 4-building set + grouped Output; deep re-verify of all 41 rows.** Fixed 8 stale MLS/URLs (incl. RH 908 → W12587434), 6 listed rents, 7 MLS brackets; added missed Humber lease **101** (1,135 sf, $3,000, 2025-12-19); restored confidence fills; swapped minifs/maxifs → SUMPRODUCT(MIN/MAX(IF)); filled TRREB W04/City/YoY; C2 live LINEST = **$143/spot** (n=35). 31 included · Humber $3.23/SF · rec subject $3.71/SF. New actives NOT added per user row set: Humber 1102 ($2,400, 694sf), Winston 1801 (W13154924).

## condos.ca leased-history route (reuse this)
Building page → click "Price History" → toggle **Rented** → "View full listing history" **opens a NEW TAB** at `pricehistory?offer=Rent&buildingId=<ID>`; "Load 15 more" paginates (2 clicks ≈ 14 months for The Humber). Per-unit exact SF ("NNN sqft*") on each unit page; signed-in, the building page's For Sale/For Rent cards also show exact SF. PARSING GOTCHA: 1,000+ sqft brackets contain commas — allow `[\d,\-]+`. Unit-page URL pattern: `<building-slug>/unit-<unit>-<MLS#>` (harvest hrefs from the history list; don't guess).
- 2026-06-11: direct nav to bare `condos.ca/pricehistory?offer=Rent&buildingId=6502&bedTypeNum=-1` works (the building-slug-prefixed version redirects to the building page). History rows render duplicated (desktop+mobile) — dedupe by href+text.
- **Signed-in unit pages no longer show the MLS size bracket** (exact sqft* replaces it) — read brackets from the leased-history list rows instead. Exposure field also gone (carry from prior session reads, labelled).

## Dead-ends (don't re-try)
- No developer floor plans / suite areas online yet — Hickory's own SF unverifiable until plans or the suite-area schedule/declaration publish.

## Gotchas
- "find me comps" for this building = comparable nearby rentals (it has none of its own). It is the SUBJECT, not a comp row.
- Prior-model premium lives in old workbook's Data_Old ("Applying Wilby Figures to Hickory Market"): +13.3% → carried as the tunable lever (Data_Summary!C4).

## Last touched
- 2026-06-11 — v5 REDO: fresh shortlist (River Ridge/West22 new), user kept Humber-only; all rows re-verified; 2 new actives; 3 v4 slips fixed; workbook + verification MD rebuilt.
