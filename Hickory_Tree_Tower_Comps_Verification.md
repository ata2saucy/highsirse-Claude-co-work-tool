# Hickory Tree Tower — Rental Comp Set & SF Verification

**Subject:** Hickory Tree Tower Condos · 1736–1746 Weston Road, Toronto (Weston)
**Developer:** Arkfield · A1 Development · A1 Capital — Architect: DIALOG — 38 storeys / 446 suites
**Status:** Planning Phase / pre-construction. No floor plans or suite areas published (vipcondos re-checked this session: "No floor plans are currently available", SIZE RANGE N/A) — so "comps" = comparable nearby rental condos.
**Deliverable:** `Hickory Rental Comps _vACTIVE.xlsx` — v5 (REDO): full re-run of the method — fresh area shortlist (gate honoured), user re-selected Humber-only, every row re-verified against pages opened this session, 2 new actives added, 3 v4 cell slips fixed.
**Session date:** 2026-06-11 · **Method:** read in-browser via Claude in Chrome (condos.ca signed-in; vipcondos; TRREB Q1-2026 PDF read in-browser). No downloads.

---

## Shortlist gate (run 2026-06-11) — fresh area search, user pick

Candidates presented (vipcondos Nearby Market + condos.ca Weston & Mount Dennis building directories, each building page opened):

| Building | Address | Built | Product | Depth (≥2025-05) | SF quality | Outcome |
|---|---|---|---|---|---|---|
| **The Humber** | 10 Wilby Cres | 2023 | Condo 22fl/232u | ~22 leases + 5 actives | Exact per-unit (TSCC-2982) | **SELECTED — SOLE COMP** |
| River Ridge ⭐new find | 1–3 Hickory Tree Rd | 1991 | Condo 19fl/413u (Rockport, MTCC-983) | 12 recent rentals ($2.77/SF site stat); leases seen: 2005 $2,300 May-26 · 809 $2,050 Apr-26 · 1701 $2,900 Apr-26 | Exact per-unit visible | Offered secondary — **not selected** |
| River Hill | 2088 Lawrence Ave W | 2006 | Condo 135u | thin (3 leases, 0 active) | Exact per-unit (TSCC-1752) | Re-offered — not selected |
| Weston On The Humber | 2464 Weston Rd | 2007 | Condo 10fl/162u micro-suites 343–957sf | ~5 leases $1,400–1,850 | Brackets on history | Offered supporting — not selected |
| The Winston House | 75 Emmett Ave | 1976 | Condo 349u | 2 leases | Approx only | Re-offered — not selected |
| Emmett House | 85 Emmett Ave | 1974 | Condo 275u | 4 leases | Approx only | Re-offered — not selected |
| West22 / WestonHub | 22 John St | 2020 | **Apartment (PBR)** 30fl/377u (Rockport) | 0 MLS records — off-MLS leasing | n/a | Offered as labelled asking-rent option — not selected |

**Evaluated & excluded (logged in Output → Other Excluded):** The Charlton Residences — 1695-1705 Weston Rd (precon condo, Old Stonehenge, 25fl/240u, 0 rentals; future comp once leasing) · Weston Gate — 2130 Weston Rd (1978, 75u; only 2 leases in window: 1004 $2,300 Apr-26, 404 $1,900 Nov-25; bracket SF) · Eglinton Park Place — 3559 Eglinton W (1988, 170u, ~2.3 km; 2 leases: 1601 $2,550 May-26, 903 $2,450 Jun-25; River Ridge dominates) · Lexington on The Green — 36-38 Gibson/9-11 Pine (2008 low-rise towns, TSCC-1930 — product mismatch) · Sidney Belsey 50–74 / W Towns / Riverboat Landing / Pioneer & Charlton Settlement (stacked towns — product) · RioCan Hall 126 John (precon) · Humberview Heights (0 rentals, standing reject) · 2255/2275 Weston Rd, 1530 Weston Rd, 38 Gibson (non-condo / partial-basement units) · 89 Church St entries in Weston feed (downtown C-district mis-bucket).

**Comp set per user pick 2026-06-11: THE HUMBER ONLY.** Date filter kept at 2025-05-01 (user choice). Workbook overwritten in place (user choice).

## What changed vs v4 (2026-06-09)

- **All 26 leased rows + 2 room rentals re-verified on unit pages opened this session — zero SF/rent/date deltas.** All 5 actives re-verified (building page cards show exact SF signed-in).
- **2 new actives added:** 1102 · 2/2 · 0pk · **694 sf** · $2,400 · 6 DOM (listed 2026-06-05) · W13243038 — and 1004 · 1+1/1 · 0pk · **588 sf** · $2,200 · listed 2026-06-11 · W13430024. Raw Data now 33 rows (22 in-window + 4 older + 5 actives + 2 excluded rooms).
- **v4 slips fixed:** (1) 1801-P row carried 1907's description and a 600-699 bracket — restored to room-rental description, bracket 700-799 per this session's unit-page read; (2) 1907's bracket caveat ("600-699 vs calc 715") was missing from its own row — reinstated (bracket per 2026-06-09 read, labelled; signed-in pages no longer display brackets); (3) 405's MLS bracket cell read 700-799 — corrected to **800-899** per this session's history read (caveat: calc 788 sits below bracket).
- **Output Low/High array ranges extended** $2:$32 → $2:$34 for the two added rows.
- **Format aligned cell-for-cell to the canonical `v2 hickory mock comp.xlsx` (2026-06-11):** added Output row 37 **Weighted Avg. Building Total (Comps)** (pre-premium comps basis = mix-weighted row-31 rents × 446 → **$997,764/mo** vs subject totals ~$1.13M — the premium uplift in dollars); K36 → "Weighted Avg.", K45 → "Subject Property Rent", G2 → "Unit Mix Adjusted1"; B2 banner removed (not in mock); Building Summary J5 → `=SUM(J4:J4)`; S&C A8 label matched. 665 formulas, 0 errors; L37 ties to manual recomputation.
- **Levers untouched:** filter 2025-05-01 · premium +13.3% (Data_Summary!C4) · apartment adj 0 · weights 46/45/9 & 30/16/45/9.

## Per-unit detail — The Humber (all opened 2026-06-11; "sqft\*" = condos.ca calculated registered area)

**In-window leases (22, all CONFIRMED per-unit):**
1602 · 2/2 · 1pk · **694** · $2,450 · 2026-04-24 (W12954480) — 409 · 1+1/1 · 0pk · **694** · $2,000 · 2026-04-22 (W12873004) — 1807 · 2/2 · 1pk · **715** · $2,350 · 2026-04-21 (W12930642) — 204 · 1/1 · 1pk · **617** · $1,999 · 2026-04-13 (W12984894) — 202 · 1+1/2 · 0pk · **751** · $2,100 · 2026-04-01 (W12841906) — 1409 · 2/2 · 1pk · **816** · $2,575 · 2026-03-28 (W12898704) — 1005 · 1+1/1 · 1pk · **583** · $2,200 · 2026-03-24 (W12848862) — 1206 · 3/2 · 0pk · **988** · $2,550 · 2026-03-03 (W12473063) — 308 · 1+1/1 · 1pk · **694** · $2,199 · 2026-01-22 (W12686952) — 2004 · 1+1/1 · 0pk · **588** · $2,100 · 2026-01-21 (W12460996) — 101 · 3/2 · 1pk · **1,135** · $3,000 · 2025-12-19 (W12506510, grade-level 2-storey) — 2102 · 2/2 · 1pk · **694** · $2,400 · 2025-12-18 (W12573868) — 405 · 2/2 · 1pk · **788** · $2,600 · 2025-10-29 (W12432828, calc below 800-899 bracket — caveat) — 2106 · 3/2 · 1pk · **988** · $3,000 · 2025-10-03 (W12390989) — 615 · 1/1 · 1pk · **556** · $2,200 · 2025-10-02 (W12339385) — 2006 · 3/2 · 1pk · **988** · $3,000 · 2025-09-23 (W12324893) — 407 · 1+1/1 · 1pk · **663** · $2,300 · 2025-09-05 (W12317619) — 1204 · 1+1/1 · 0pk · **588** · $2,000 · 2025-08-18 (W12272427) — 906 · 3/2 · 1pk · **988** · $3,200 · 2025-07-24 (W12276329) — 901 · 2/2 · 1pk · **797** · $2,500 · 2025-07-03 (W12216889) — 9 · 2/2 · 0pk · **816** · $2,400 · 2025-06-26 (W12049546) — 204 · 1/1 · 1pk · **617** · $2,100 · 2025-05-14 (W12051218).

**Pre-filter leases (4, Include 0):** 502 · **751** · $2,500 · 2025-04-23 (W12042837) — 2202 · **694** · $2,400 · 2025-04-22 (W12018074) — 1407 · **715** · $2,600 · 2025-04-16 (W12013340) — 309 · **694** · $2,150 · 2025-04-11 (W12051780).

**Actives (5, asking):** 1102 · **694** · $2,400 (W13243038) — 1004 · **588** · $2,200 (W13430024) — 907 · **715** · $2,400 (W13150160) — 1407 · **715** · $2,500 (W13159224) — 1907 · **715** · $2,500 **leased conditional**, 99 DOM (W12841668).

**Excluded rooms (2, orange):** 1801-P · $1,560 · 2026-04-06 (W12905894) — 1801-S · $1,280 · 2025-07-22 (W12194033). Room-by-room rentals of one 2-bed; never in PSF.

**Exposure note:** condos.ca unit pages no longer display an Exposure field (re-confirmed this session). Exposure values in Raw Data col Y are carried from the 2026-06-03/09 session reads, labelled. New actives 1102/1004: exposure blank (not observed).

## Coverage & conclusion (computed in the workbook, re-verified independently 2026-06-11)

- **664 formulas, 0 recalc errors**; every block ties to an independent numpy/manual recomputation (exact match).
- **Parking adjustment (Data_Summary!C2, LIVE LINEST over 26 leased helper rows): $132.33/spot/mo** — numpy OLS cross-check identical.
- **Data_Summary:** 22 included · raw **$3.23/SF** · mix-weighted Humber $/SF (46/45/9) **$3.28** → +13.3% → **RECOMMENDED subject $/SF $3.71** → ~$2,598/mo @ 700 sf. Residual vs prior $3.90: **−4.8%** (market timing).
- **Output (untrended, net of parking, Humber sole comp):** 22 txns · 762 avg sf · $2,323/mo · $3.10/SF → ×1.133 → **Subject Site (Untrended) $2,632/mo · $3.51/SF**.
- **TRREB Q1-2026 re-read this session (report PDF p.1 + p.3):** W04 **$2,084 / $2,569 / $3,043** (1B/2B/3B, 51/38/8 leased) · City of Toronto **$2,292 / $3,091 / $3,866** · GTA YoY **−4.1% / −3.2% / −2.7%** — unchanged; Q1-2026 still the latest release (2026-05-21).

## Data ceiling / definitive source

condos.ca per-unit figures are calculated registered areas (precise for The Humber TSCC-2982). Leased history is login-gated (signed-in session used). MLS size brackets are no longer displayed on signed-in unit pages — bracket reads are from the leased-history list. Definitive areas: registered declaration TSCC-2982 / MPAC. Hickory's own suite areas verifiable only once the developer publishes plans or the suite-area schedule / declaration.
