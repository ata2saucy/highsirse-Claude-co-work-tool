# High-Rise Rental Comp & Square-Footage Tool

A browser-driven workflow (Claude in Chrome) that turns a subject building + address into a defensible recommended rent: it finds comparable rental buildings, verifies each unit's exact interior square footage from floor plans and listings, colour-codes confidence, and builds an institutional comp workbook.

## Quick start

New operator? Read **`HANDOFF.md`** — prerequisites (Cowork + Claude in Chrome + signed-in **condos.ca and vipcondostoronto.net** accounts) and setup (clone this repo into a local folder, select it in Cowork). The workflow: **give Claude the subject's address → BEFORE it looks for any comps (before the area search, the shortlist, and any pull) it asks three quick questions about the subject — a required gate (development type — condo vs rental apartment · suite mix, incl. the 1+den split · pre-construction vs resale) → it then searches the area and presents a ranked shortlist of comp buildings (each with a brief description, location, and a one-line *why it does or doesn't compare* — judgment in prose, **not a numeric score**) → you pick → it verifies every unit and builds the workbook.** Kickoff: `comps for {address}` (new subject) or `fix the {building} comps` (existing workbook). The process runs from the local folder via `CLAUDE.md`; the GitHub link alone does nothing at runtime.

**Arkfield `_AI` batch mode** (`run the Arkfield comps`): with the **Microsoft 365 connector** connected, Claude reads the subject work list from Arkfield's SharePoint project index (`Arkfield Capital/_AI/AI Pipeline/code/arkfield_projects.json`), runs the per-subject workflow (shortlist gate intact), and deposits each finished workbook into `Arkfield Capital/_AI/Rent Comps Output/` via Claude in Chrome (the connector is read-only). SharePoint supplies the work list and receives the output — **never a comp source.** See `CLAUDE.md` → "Kickoff — Arkfield _AI batch."

## Contents

- `HANDOFF.md` - operator quickstart (prereqs, setup, run, outputs)
- `Arkfield_Comp_Tool_Handoff_SOP.pdf` - branded one-page handoff SOP (printable)
- `CLAUDE.md` - operating contract (rules, workflow, output shape) — **wins on any conflict**
- `condo_sqft_verification_method_1.md` - full methodology
- `v2 hickory mock comp.xlsx` - **canonical workbook-format skeleton (v3)** — the six-sheet standard; deliverables match it cell-for-cell
- `10 Lower Spadina Rental Comps _vACTIVE.xlsx` - **v3 worked example** (downtown-waterfront, 9 condo comps) — clean six-sheet output
- `Hickory Rental Comps _vACTIVE.xlsx` - earlier worked example (Hickory Tree Tower, Weston) — predates the v3 cleanup (single `Raw Data` sheet); kept for reference
- `tools/qa_workbook.py` - QA gate — recalcs a workbook and checks the v3 acceptance checklist (run before delivery)
- `Hickory_Tree_Tower_Comps_Verification.md` - per-comp SF verification
- `Hickory_Rent_Reconciliation.md` - reconciliation to prior valuation
- `Olive_Residences_SqFt_Verification.md` - second worked example (per-unit SF)
- `Rental_Comp_Tool_SOP.pdf` - one-page SOP (10 steps)
- `building_memory/` - cross-session building facts (map, not proof — see its README)

## Conventions

- **Condos run on two websites only; apartments add authorized rental sources (see next bullet).** For condos: condos.ca = comp data (leased history, per-unit SF) · vipcondostoronto.net = floor plans / key-plates / identity. Other portals are Route A plan-hunt fallbacks, never condo comp sources.
- **Apartments vs condos are tracked separately.** The tool finds both, but purpose-built rental apartments get their **own Raw Data sheet and Output view** (identical structure), and their rent/listing data may come from **Apartments.com + reputable Canadian rental sites + building/property-manager pages** (apartment rows only — never a condo comp, never an interior-SF figure). Apartment SF still comes from a verified plan and clears the same strict exact-or-blank bar; asking (listed) vs achieved (leased) rent is kept explicit ("selling as vs sold for"), and **both** Output views surface that spread. See CLAUDE.md → "Apartment vs condo handling".
- Exact interior SF only; never a range. Every number names a source opened that session; "cannot verify" is a valid outcome.
- Comp-building selection is gated: shortlist + rejects are presented and **the user picks** before any per-unit pull.
- Workbook formatting follows CLAUDE.md's v2 spec: **blue font = hard-coded input · black = formula/label · yellow fill = tunable lever · green/cream/orange confidence fills** on both Raw Data sheets (green = leased in-window + SF verified per-unit; cream = active/older/caveat/apartment asking-only; orange = excluded partials).
- Parking adjustment is OLS-derived from the comps (live LINEST), not a copied figure.
- **No bare constants:** every hard-coded (blue) cell shows its origin — a live derivation or an explicit source. The subject unit-mix weights (Data_Summary H2:H4) are derived live from the Floor Plans `(SUBJECT)` rows when the subject has its own plans, else entered as the subject's planned mix with an in-cell source.
- Everything is read in the browser — no downloads, no new logins, no paid records.
- **Workbook is six sheets (v3):** Output · Building Summary · Data_Summary · `RD Condos` · `RD Apartments` · Floor Plans. There is **no `Subject & Conclusion` sheet** (its recommendation summary is folded into Output) and **no comp-quality `/10` score table** anywhere — comp quality is prose with qualitative role labels (Primary/Secondary/Supporting/Excluded) only. The final workbook must recalc with **no `#REF!`/`#VALUE!`/`#DIV/0!`/`#N/A`** — run `tools/qa_workbook.py` to verify.
