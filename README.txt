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
7. Survey Intelligence — FULL MODULE: 6 tracked surveys, live
   progress bars, an enumerator leaderboard, AI data-quality checks,
   and a per-survey detail modal with a submissions trend chart
8. GovOS — FULL MODULE: budget allocation simulator with live sliders
   (drag to reallocate a mock FY26 budget across 5 sectors, watch the
   donut chart and projected-impact text update in real time),
   ministry dashboard list with performance scores, citizen service
   response-time tracker
9. HealthOS — FULL MODULE: disease surveillance feed, ranked facility
   performance list, medicine inventory stock-level alerts
10. AgroOS — FULL MODULE: regional yield chart, live market price
    ticker, pest & disease alert feed
11. EduOS — FULL MODULE: school performance list ranked by pass rate
    with dropout-risk badges, teacher distribution chart
12. ClimateOS — FULL MODULE: regional climate resilience ranking,
    live climate alert feed
13. Full dark/light mode, responsive to mobile, ⌘K search shortcut

EVERY MODULE IN THE SIDEBAR IS NOW FULLY FUNCTIONAL
---------------------------------------------------------
As of this update, all 12 modules — not just the original 5, not
just Tender and Survey Intelligence, but all five Domain OS modules
too — are real, interactive, data-driven pages. Nothing in the
sidebar is a "coming soon" placeholder anymore. Every KPI is computed
from underlying data, every list is real and sorted/filterable where
it makes sense, and the GovOS budget simulator is a genuinely live
interactive tool, not just a static mockup.

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

3. NAVY-COLORED ICONS INVISIBLE IN DARK MODE — FIXED
   While building the new Domain OS modules, the same "navy-on-navy"
   contrast bug from an earlier round turned up again in more places
   than previously caught — including the ORIGINAL Command Centre KPI
   icons, which had been invisible in dark mode this whole time. Any
   icon styled with navy on a navy-tinted background is unreadable
   once the background itself goes dark. Fixed by switching every
   instance to the theme-aware --navy-ink variable (dark navy in
   light mode, light blue in dark mode) — 11 occurrences across the
   Command Centre, Survey Intelligence, Tender Intelligence, all 5
   Domain OS pages, and the AI Explorer's decorative icon. Confirmed
   visually across every affected page in dark mode.

4. LOGO STILL DISTORTED — ROOT CAUSE FOUND AND FIXED
   You were right that the logo was still wrong. Re-processing from
   your freshly uploaded original logo files surfaced two real bugs
   in how I'd been cropping the artwork:
   - The sidebar/wordmark logo crop was cutting off the top and
     bottom points of the compass star, because the compass icon is
     genuinely taller than the "Intelligence OS / AFRICA" text block
     next to it — my crop was using the text's row bounds instead of
     the icon's true (taller) bounds. Fixed by surgically erasing
     only the tagline pixels rather than cutting by row, so the full
     compass is preserved.
   - The favicon/icon-only crop was clipping the rightmost circuit
     nodes, because I'd restricted the pixel search itself to the
     same column boundary used for the crop, so pixels just past
     that boundary could never be found. Fixed by first finding the
     true icon/wordmark gap independent of any assumption, then
     cropping from that.
   Both are rebuilt from your original source file, verified via
   direct side-by-side pixel comparison against the previous
   (flawed) versions, and confirmed rendering correctly in both light
   and dark mode in the live app.

NEW: MARKETING LANDING PAGE (landing.html)
---------------------------------------------
A public-facing front door for the platform — since index.html drops
straight into the logged-in app with no way to explain what this is
to someone who isn't already a user. Includes:
- Hero section with live stat bar (12 modules, 16 regions, 1.2M
  farmers, 3,847 facilities — pulled from the same numbers as the app)
- A 9-card module showcase covering all 12 live modules
- A dark "product preview" panel with mock KPI cards
- A roadmap section (Nigeria/Kenya/Rwanda workspaces, real backend,
  LLM-backed AI Explorer, mobile app)
- Full dark/light mode, fully responsive, built from the exact same
  design tokens and corrected logo as the main app
- Every CTA links to index.html ("Enter the Platform")

FILE STRUCTURE — TWO OPTIONS FOR HOW TO WIRE THIS TOGETHER
------------------------------------------------------------------
landing.html is a SEPARATE file from index.html (the app). Right now
your live URL (https://fadl462.github.io/intelligence-os/) opens
index.html directly — the app, not the landing page. You have two
options once you push landing.html to the repo:

OPTION A — Keep the app as the homepage (no changes needed)
  Leave index.html as-is. landing.html becomes an extra page at
  https://fadl462.github.io/intelligence-os/landing.html that you
  can link to from elsewhere (e.g. a Freelancer.com profile, a
  LinkedIn post) as a polished pitch page, while the main URL keeps
  opening straight into the app for anyone who already knows what
  this is.

OPTION B — Make the landing page the homepage (swap the files)
  Rename index.html to app.html, then rename landing.html to
  index.html. Now https://fadl462.github.io/intelligence-os/ shows
  the landing page first, and every "Enter the Platform" button
  correctly opens app.html — but you'll need to do a find-and-replace
  in landing.html changing href="index.html" to href="app.html"
  (5 occurrences) BEFORE renaming, or the buttons will 404.

Recommended: Option B if you want this to read as a real product to
someone landing on the URL cold (e.g. sharing it with a client or
investor). Option A if the URL is mainly shared with people who
already know to expect the app.

5. CURSOR NOT CHANGING TO POINTER ON HOVER — FIXED
   Root cause: browsers only apply the automatic pointer cursor to
   <a> elements that have a real href attribute, or to native form
   controls. Throughout the app, many clickable elements are <a> or
   <div> tags driven by onclick/JS instead of href (sidebar nav
   items, quick actions, dropdown menu items, "add widget", widget
   remove buttons) — so they fell back to the default text/arrow
   cursor instead of signaling they're clickable. Audited every
   interactive element across all 12 modules plus every dropdown and
   modal, found 6 element types missing the fix (sidebar nav, quick
   action cards, dropdown menu items, "View all"-style links, add
   widget, widget remove buttons), and added explicit cursor:pointer
   to each. Verified programmatically — not just by eye — by reading
   the actual computed CSS cursor value for all 22 interactive
   element types across every view, confirming every one now reports
   "pointer". landing.html was also audited the same way and had no
   issues, since every link there uses a real href.

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
