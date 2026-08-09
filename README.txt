INTELLIGENCEOS AFRICA — INTERACTIVE PROTOTYPE
================================================
v1.0 · Ghana Edition · Prototype for developer handoff

WHAT THIS IS
------------
A single self-contained HTML file (IntelligenceOS_Africa_Prototype.html)
implementing the flagship experience described in the Master Prompt:
the AI Command Centre and four core modules, fully wired to the locked
brand system (Navy #082B5A / Teal #00BFA6 / Plus Jakarta Sans / compass
motif). Open it directly in any browser — no install, no server needed.

WHAT'S BUILT
------------
1. AI Command Centre — KPI cards with sparklines, live AI insight feed,
   alerts panel, quick actions, pinned dashboard previews
2. Africa Data Cloud — dataset source browser (GSS, GHS, World Bank,
   WHO, EPA, OSM, FAO, GMet) with sync status
3. AI Data Explorer — natural-language query box; 4 example prompts
   return working canned AI responses (narrative + chart + table)
4. GIS Intelligence — live Leaflet map of Ghana's 16 regions, 3
   togglable data layers (health / agriculture / education), ranked
   region panel, legend
5. Dashboard Studio — widget canvas with live Chart.js charts (line,
   bar, donut, KPI card), toolbar, "add widget" placeholder
6. Survey Intelligence & Tender Intelligence — Phase 2 teaser panels
7. Sidebar roadmap — GovOS / HealthOS / AgroOS / EduOS / ClimateOS
   listed as upcoming domain modules
8. Full dark/light mode toggle (persisted), responsive down to mobile,
   compass-motif branding throughout

All data shown (KPIs, alerts, regions, tenders) is illustrative demo
data written to feel real — it is NOT live. Wiring it to real sources
is the next engineering phase (see below).

TECHNICAL NOTES
----------------
- Zero build step: plain HTML/CSS/JS in one file
- Chart.js and Leaflet load from cdnjs.cloudflare.com; Google Fonts
  loads Plus Jakarta Sans — all three need an internet connection.
  If they're blocked, the page degrades gracefully (system font
  fallback, map shows a friendly empty state, tables still render).
- Theme preference is saved in localStorage.
- Icon is embedded as base64 (official brand hex values) — no
  external image dependency.

HOW TO USE IT
-------------
- Open the file in a browser to click through the prototype yourself.
- Hand it to a developer as a visual/interaction reference for
  building the real frontend (Next.js/React per the original stack).
- Use it in an investor or stakeholder walkthrough — every screen is
  live and clickable, not static mockups.

REALISTIC SCOPE — WHAT THIS IS NOT
------------------------------------
The Master Prompt describes a 35-deliverable, Palantir/Bloomberg-scale
platform: production backend, mobile/tablet/desktop native apps,
multi-tenant database architecture, Kubernetes deployment, a live AI
copilot, real data pipelines from World Bank/WHO/GSS/etc., security
and accessibility audits, and a full design-system/Figma handoff.
None of that exists yet. This file is the front-of-house prototype —
deliverable #35 on that list ("interactive prototype ready for
developer handoff") — not the finished product.

SUGGESTED NEXT PHASES
-----------------------
Phase 1 (this file):        Interactive frontend prototype ✓
Phase 2:                    Real backend (FastAPI/Node + Postgres),
                             auth, and 2-3 real data connectors
                             (start with GSS + World Bank APIs)
Phase 3:                    Replace canned AI Explorer responses with
                             a real LLM-backed query engine (RAG over
                             the connected datasets)
Phase 4:                    GIS layer backed by real district-level
                             data instead of the current demo values
Phase 5:                    Survey Intelligence & Tender Intelligence
                             modules built out from teaser to full
Phase 6:                    Mobile app, multi-tenancy, deployment
                             infrastructure

Recommended: pick ONE flagship use case (e.g. maternal health
monitoring for Ghana Health Service, or tender matching for your own
consultancy pipeline) and take it end-to-end with real data before
building out the other 17 modules. A platform that does one thing
brilliantly with real data is worth more than eighteen modules that
are all still demos.
