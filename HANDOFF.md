# Handoff — running this tool in Cowork

A browser-driven workflow that turns a subject building + address into a defensible recommended rent, with every square foot tied to a source opened that session. This page is the 5-minute setup for a new operator. The full rules live in `CLAUDE.md` (operating contract) and `condo_sqft_verification_method_1.md` (methodology) — read those before your first run.

## Prerequisites (hard requirements)

1. **Claude desktop app with Cowork mode.**
2. **Claude in Chrome** extension installed, Chrome running and connected.
3. **condos.ca AND vipcondostoronto.net accounts, both signed in** in that Chrome profile. condos.ca leased rental history is login-gated, and vipcondos serves floor plans/key-plates to logged-in sessions — without these the pull fails at step 1. (Do NOT log into HouseSigma/MPAC/GeoWarehouse or pay for records — see the do-not list in CLAUDE.md.)
4. **Access to this repo** (it is private — ask the owner for a collaborator invite).
5. *(Arkfield `_AI` batch mode only)* **Microsoft 365 connector connected** (read access to Arkfield SharePoint) and Claude in Chrome **signed in to SharePoint** for the output upload. Not needed for the address / existing-workbook modes.

## Setup

1. Get the repo onto your machine: `Code → Download ZIP` (or `git clone`), into a folder such as `~/Documents/Claude/Projects/hickory`.
2. In Cowork, **select that folder**. `CLAUDE.md` in the folder root is auto-loaded as the operating contract — this is what makes the process run; the GitHub link alone does nothing at runtime.
3. Sanity-check the folder contains: `CLAUDE.md` · `condo_sqft_verification_method_1.md` · the comps workbook (`.xlsx`) · `building_memory/` (with `README.md`, `INDEX.md`, `_TEMPLATE.md`).

## Run

**Two ways to start:**

1. **New subject — give an address.** Say e.g. *"comps for {address}"* or *"find comps for {building name}, {address}"*. Claude confirms the building, then — **before it goes looking for any comps (before the area search and shortlist)** — **asks three quick questions about the subject** so it understands what you're building and can pick fair comparables: (1) **type** — high-rise condos or a high-rise rental apartment (a rental-apartment subject changes how comps are premium-adjusted); (2) **suite mix** — share of 1-bed / 1+den / 2-bed / 3-bed (if you have it, that's used as the building's mix; if not, say "skip" and it estimates from the floor plans); (3) **pre-construction or resale** (a built/resale subject can use its own lease history as the primary evidence). Q1 and Q3 are usually self-evident from the building lookup, so Claude proposes the answer and you just confirm or correct it in a word. **Then it searches the area and stops and presents a ranked shortlist** — each candidate shown with a brief description of the development, location (address + distance), and **Claude's 0–10 comp-quality rating** (Claude's own judgment to guide you, not a measured figure — it never overrides your pick) — **plus every evaluated-and-excluded building with reasons. You pick the comp set; only then are units pulled.** This stop is required behaviour, not a stall. It may also ask once for other per-subject parameters (premium, prior-model peg) — questions arrive in plain language with a recommended default; answer or accept defaults, and they stay as yellow levers in the workbook.
2. **Existing workbook — refresh or fix it.** Say *"fix / redo the {building} comps"*. Claude takes intake from the workbook in the folder, re-offers the shortlist if the comp set is in question, and re-verifies everything against pages opened that session.
3. **Arkfield `_AI` batch — source subjects from SharePoint.** Say *"run the Arkfield comps"* / *"do the _AI pipeline comps"*. Claude reads the subject work list from Arkfield's `_AI` project index via the Microsoft 365 connector (intake only — never comp evidence), runs the per-subject workflow one at a time **with the shortlist gate intact**, then uploads each finished workbook to `Arkfield Capital/_AI/Rent Comps Output/` via Claude in Chrome (the connector is read-only) — **confirming each upload with you first.** See `CLAUDE.md` → "Kickoff — Arkfield _AI batch."

Then expect: per-unit verification in the browser (roughly 30–40 page reads for a Humber-sized building), the workbook build, a verification markdown, and a building-memory update. Everything is read in the browser — no downloads, ever. "Cannot verify" is a valid outcome; a blank beats a guess.

## Outputs

- `{Building} Rental Comps _vACTIVE.xlsx` — v2 format specified in CLAUDE.md: Output (with **two product-type views — condos-only and apartments-only**) · Subject & Conclusion · Building Summary · Data_Summary · **`RD Condos` and `RD Apartments`** (RD = Raw Data; two identical-structure sheets, A:AN) · Floor Plans; live formulas (incl. the LINEST parking regression), zero recalc errors. Condos and apartments are never blended; apartment rent/listing data may come from Apartments.com + Canadian rental sites (apartment rows only — those sources never supply an SF figure, and apartment interior SF clears the SAME strict exact-or-blank bar). Asking (listed) vs achieved (leased) rent is kept explicit, with the "selling as vs sold for" spread shown in each Output view.
- `{Building}_..._Verification.md` — per-unit sources: what was opened and what was seen.
- `building_memory/` — refreshed stable facts (never reportable SF).

## If documents disagree

`CLAUDE.md` wins. (Known example: the generic cell-colour note in the method doc/README describes the dark-blue/grey/green financial-model standard; comp workbooks follow CLAUDE.md's v2 convention exactly — blue font = hard-coded input, black = formula/label, yellow fill = tunable lever, green/cream/orange confidence fills on both Raw Data sheets.)

## Worked examples in this repo

- **Hickory Tree Tower** (1736 Weston Rd, Weston — pre-construction subject): current workbook is v5 (2026-06-11), Humber-only comp set per owner instruction; see `Hickory_Tree_Tower_Comps_Verification.md` and `Hickory_Rent_Reconciliation.md`.
- **Olive Residences** — per-unit SF verification example (`Olive_Residences_SqFt_Verification.md`).
