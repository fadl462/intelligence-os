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
6. Tender Intelligence — FULL MODULE: 14 tracked opportunities, live
   search/sector/min-fit filters, sort by fit/deadline/budget, and a
   working pipeline board (Identified → In Progress → Submitted →
   Won) you can actually advance opportunities through
7. Survey Intelligence — FULL MODULE: 6 tracked surveys (GFD baseline,
   GTVP tracer study, Jaman North feasibility survey, ESSA teacher
   workforce, KOFIH pretest, cocoa farmer registry) with live
   progress bars, an enumerator leaderboard, AI data-quality checks,
   and a per-survey detail modal with a submissions trend chart
8. Roadmap · Domain OS — GovOS, HealthOS, AgroOS, EduOS, ClimateOS
   are no longer dead sidebar links. Each is now a real page: hero,
   6-feature grid, a blurred "coming soon" dashboard preview, and a
   working email waitlist form with validation
9. Full dark/light mode, responsive to mobile, ⌘K search shortcut

EVERY SIDEBAR ITEM NOW LEADS SOMEWHERE REAL
------------------------------------------------
As of this update, there are no more dead links or bare modals
anywhere in the sidebar. Every single nav item — from Command Centre
down to ClimateOS — routes to an actual page with real content.
Two tiers are honestly distinguished:
- FULL MODULES (Command Centre, Data Cloud, AI Explorer, GIS,
  Dashboard Studio, Tender Intelligence, Survey Intelligence): fully
  interactive, backed by structured demo data, everything clickable
- ROADMAP PREVIEWS (GovOS, HealthOS, AgroOS, EduOS, ClimateOS):
  honestly labeled "Coming Soon," with a real feature description,
  a locked dashboard preview, and a working waitlist signup — not
  pretending to be functional, but not a dead end either

TENDER INTELLIGENCE — WHY THIS MODULE FIRST
------------------------------------------------
Per the recommendation in the previous version of this README ("pick
ONE flagship use case and take it end-to-end"), Tender Intelligence
was chosen because it maps directly onto real work you already do —
tender monitoring for JMK Consulting and your own freelance pipeline.
The 14 opportunities include realistic entries tied to your actual
context (JMK, Inscend, the Jaman North political survey, CRI/Mondelez)
alongside donor-realistic ones (EU, World Bank, UNICEF, GIZ, USAID,
AfDB, WHO). Every number on the KPI strip (open count, average fit,
closing-soon count) is computed live from the underlying data rather
than hardcoded, so advancing a tender through the pipeline updates
everything downstream — this is the pattern to repeat when the other
modules get built out for real.

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

BUGFIXES (this update)
-------------------------
1. KPI CARDS GROWING ABNORMALLY TALL — FIXED
   Cause: the sparkline charts on the Command Centre KPI cards sat
   directly inside flex-column containers with no positioned wrapper.
   This triggers a known Chart.js issue where the canvas's resize
   observer enters a feedback loop and the chart grows taller on
   every frame, pushing surrounding content down the page. Fixed by
   wrapping every chart canvas (KPI sparklines, Dashboard Studio
   widgets, AI Explorer chart, Survey Intelligence modal chart) in a
   fixed-height, position:relative container with the canvas
   absolutely positioned inside it — the standard fix for this
   Chart.js behavior. Verified by loading Chart.js locally (the
   sandbox used to build this normally has the CDN blocked, which is
   why the bug wasn't caught in earlier testing) and confirming every
   chart now renders at its correct, stable size.

2. LOGO WAS A CSS APPROXIMATION, NOT THE REAL ARTWORK — FIXED
   The sidebar was displaying "IntelligenceOS" as styled text rather
   than your actual logo image, which meant it was missing the
   analytics-chart-inside-the-O detail from your real logo — a direct
   miss against your own brand rule ("never redesign or reinterpret
   the approved logo"). Fixed by embedding your actual logo artwork
   (cropped from the official-hex horizontal lockup, tagline excluded
   since it's illegible at sidebar size) as the sidebar logo, with a
   light-background and dark-background version that swap
   automatically with the theme toggle. Verified pixel-by-pixel that
   the dark-mode swap actually fires and the correct variant renders.

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
Phase 1 (done):    Interactive frontend, every sidebar item routes
                    to real content. Tender Intelligence and Survey
                    Intelligence built out as full end-to-end modules
Phase 2:           Real backend (FastAPI/Node + Postgres), auth, and
                    2-3 real data connectors (start with GSS + World
                    Bank APIs) — Tender Intelligence and Survey
                    Intelligence are both ready to connect first,
                    since their interaction models are already built
                    and tested
Phase 3:           Replace canned AI Explorer responses with a real
                    LLM-backed query engine (RAG over connected data)
Phase 4:           GIS layer backed by real district-level data
Phase 5:           Pick ONE Domain OS (GovOS/HealthOS/AgroOS/EduOS/
                    ClimateOS) and build it out the same way Tender
                    and Survey Intelligence were — full module, not
                    a preview page
Phase 6:           Mobile app, multi-tenancy, deployment infra

Recommended: Tender Intelligence and Survey Intelligence are now the
strongest candidates to connect to real data first — both have their
full interaction model (filtering, scoring, progress tracking, detail
views) already built and tested. They just need real records flowing
in instead of demo data.
