INTELLIGENCEOS AFRICA — LIVE PRODUCT
========================================
v1.0 · Ghana Edition
Live at: https://fadl462.github.io/intelligence-os/

WHAT THIS IS
------------
A single self-contained HTML file (index.html) implementing the
IntelligenceOS Africa frontend: the AI Command Centre and four core
modules, on the locked brand system (Navy #082B5A / Teal #00BFA6 /
Plus Jakarta Sans / compass motif). Open it directly in any browser
or push it to GitHub Pages — no install, no build step, no server.

WHAT'S BUILT
------------
1. AI Command Centre — KPI cards, live AI insight feed, alerts panel,
   quick actions, pinned dashboard previews
2. Africa Data Cloud — dataset source browser (GSS, GHS, World Bank,
   WHO, EPA, OSM, FAO, GMet) with live search filtering
3. AI Data Explorer — natural-language query box with working canned
   AI responses (narrative + chart + table)
4. GIS Intelligence — live Leaflet map of Ghana's 16 regions, 3
   togglable data layers, clickable region detail panel
5. Dashboard Studio — widget canvas; toolbar buttons add real
   Chart.js widgets to the canvas; publish flow with confirmation
6. Survey Intelligence & Tender Intelligence — Phase 2 module previews
7. Sidebar roadmap — GovOS / HealthOS / AgroOS / EduOS / ClimateOS,
   each opens a waitlist modal
8. Full dark/light mode, responsive to mobile, ⌘K search shortcut

INTERACTIVE SYSTEMS (v1.0 update)
-------------------------------------
This pass turned every static element into something clickable:
- Workspace switcher (dropdown, Ghana active + 3 upcoming countries)
- Notification bell dropdown with mark-all-read
- User menu dropdown (profile / preferences / docs / sign out)
- KPI cards deep-link into the relevant module
- AI insight cards and alerts open detail modals with contextual CTAs
- "View all" opens a full intelligence feed modal
- Data Cloud cards open dataset preview modals; search filters live
- GIS region rows fly the map to that region + open a metrics modal
- Dashboard Studio toolbar actually adds live-charted widgets;
  Publish gives real confirmation
- Global toast notification system backs every action
- Global modal system with keyboard (Esc) and click-outside dismiss

BRAND / LOGO AUDIT (this update)
-------------------------------------
Every logo instance in the file now uses the OFFICIAL brand hex
values from IntelligenceOS_Brand_Font_and_Color_Standards.pdf —
Navy #082B5A, Teal #00BFA6, Grey #6B7280 — not the slightly-off
values sampled from the original PNG exports. Specifically:
- Sidebar logo, favicon, and apple-touch-icon all use the SAME
  official-hex compass icon (embedded as base64 — no external file
  dependency, no risk of a broken image link)
- Browser tab now shows the real IntelligenceOS mark instead of a
  generic blank icon, with theme-color set to brand navy
- Added a proper social-share image (og-image.png, 1200x630) built
  from the official-hex horizontal logo — this is what shows up
  when the link is shared on LinkedIn, X, WhatsApp, Slack, etc.
- All in-app CSS color variables (--navy, --teal, --grey) were
  already at the exact official hex values, confirmed unchanged.

IMPORTANT — DEPLOYMENT STEP FOR THE SOCIAL IMAGE
-------------------------------------------------------
og-image.png must be uploaded to the SAME folder as index.html in
your repo (i.e. sit alongside it at the repo root) for the social
share preview to work — the HTML references it as a relative path
("og-image.png") so platforms can fetch it once the page is live at
https://fadl462.github.io/intelligence-os/. The favicon does NOT
need this step — it's embedded directly in the HTML.

All data shown (KPIs, alerts, regions, tenders, datasets) is
illustrative — written to feel real, not yet live. Wiring it to real
sources is the next phase (see below). Every mocked action (waitlist
signup, report generation, sign out, etc.) gives honest, clearly-demo
feedback via toast rather than pretending to be a real backend call.

TECHNICAL NOTES
----------------
- Zero build step: plain HTML/CSS/JS in one file
- Chart.js and Leaflet load from cdnjs.cloudflare.com; Google Fonts
  loads Plus Jakarta Sans — all three need an internet connection.
  Degrades gracefully if blocked (system font fallback, map shows a
  friendly empty state, tables/lists still render).
- Theme preference persists via localStorage.
- Icon embedded as base64 (official brand hex values) — no external
  image dependency.
- Tested across desktop (1440px), mobile (390px), light and dark
  mode, with zero console errors.

HOW TO USE IT
-------------
- Click through it yourself at the live URL above.
- Hand it to a developer as the interaction/visual reference for the
  real frontend build (Next.js/React per the original stack).
- Use it in a stakeholder or investor walkthrough — every screen is
  live and clickable, not a static mockup.

REALISTIC SCOPE — WHAT'S STILL AHEAD
----------------------------------------
This file is the frontend/interaction layer, built to production
polish. It is NOT yet backed by a real database, real datasets, a
real AI model, real auth, or real user accounts — everything you see
is convincing demo data and mocked actions. That's the honest state
of the build.

SUGGESTED NEXT PHASES
-----------------------
Phase 1 (done):    Interactive frontend, all core screens clickable
Phase 2:           Real backend (FastAPI/Node + Postgres), auth, and
                    2-3 real data connectors (start with GSS + World
                    Bank APIs)
Phase 3:           Replace canned AI Explorer responses with a real
                    LLM-backed query engine (RAG over connected data)
Phase 4:           GIS layer backed by real district-level data
Phase 5:           Survey Intelligence & Tender Intelligence built
                    out from preview to full module
Phase 6:           Mobile app, multi-tenancy, deployment infra

Recommended: pick ONE flagship use case — maternal health monitoring
for Ghana Health Service, or tender matching for your own consultancy
pipeline — and take it end-to-end with real data before building out
the other 17 modules. A platform that does one thing brilliantly with
real data is worth more than eighteen modules that are all still demos.
