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

6. NO WAY TO GET HOME + LOGO TOO SMALL — FIXED
   Two related issues from your feedback:
   - There was no way to navigate from the app back to the marketing
     landing page — clicking the logo did nothing. Fixed by wrapping
     the sidebar logo in a link to landing.html, following the
     standard "click the logo to go home" convention. Verified the
     full loop works both directions: logo click in the app lands on
     landing.html, and "Enter the Platform" from there opens the app.
   - The sidebar logo was rendered quite small (30px tall). Increased
     to 46px — bold and clearly legible at a glance — verified this
     doesn't crowd or overflow the sidebar in either light or dark
     mode, and doesn't blur since the source asset has more native
     resolution than the new display size needs.

NEW: DASHBOARD STUDIO — 30 CHART & WIDGET TYPES ACROSS 6 CATEGORIES
------------------------------------------------------------------------
Dashboard Studio went from 6 basic chart types to a genuinely
comprehensive chart library, organized the same way professional
dataviz references categorize chart types (comparison, correlation,
part-to-whole, time, distribution, specialized):

COMPARISON (7): Column, Horizontal bar, Grouped bar, Stacked bar,
  Lollipop chart, Bullet chart, Dot plot
CORRELATION (3): Scatter plot, Bubble chart, Heatmap
PART-TO-WHOLE (6): Pie chart, Donut chart, 100% stacked bar, Treemap,
  Waffle chart, Funnel chart
TIME (5): Line chart, Area chart, Stacked area, Spline (smooth line),
  Step line chart
DISTRIBUTION (3): Radar/spider chart, Polar area chart, Histogram
SPECIALIZED (4): Gauge chart, Waterfall chart, Population pyramid,
  Combo chart (bar + line on dual axes)
OTHER (2): KPI card, Table

Click "Add widget" to open a categorized picker (30 cards across 7
sections) instead of the old flat 6-button toolbar. Quick-access
chips for the 4 most common types (Line, Bar, Donut, KPI) remain in
the toolbar for one-click adds without opening the picker.

Native Chart.js types (line, bar, pie, doughnut, radar, polarArea,
scatter, bubble, and their stacked/grouped/horizontal variants) are
built directly on Chart.js for reliability. Six types Chart.js doesn't
support natively — gauge, funnel, heatmap, waterfall, bullet, and
treemap — are hand-built with CSS/HTML for the same visual quality
without adding fragile plugin dependencies.

TESTED: added all 30 chart types in a single sweep (zero console
errors), verified remove-widget still works correctly afterward,
checked the picker's responsive 2-column mobile layout, and verified
both light and dark mode for every custom (non-Chart.js) type.

BUGFIX DURING THIS BUILD: the gauge chart's canvas had a sizing
conflict between an inline max-width CSS rule and Chart.js's own
sizing logic, causing it to render invisible in dark mode and
distorted in light mode. Fixed by switching to the same
position:absolute canvas-in-a-sized-wrapper pattern already proven
elsewhere in the app (KPI sparklines, Explorer chart). Also found and
fixed an unrelated class-name collision — a static GovOS info card
was reusing the ".modal-body" class name, which could have caused
future bugs if any code ever queried that class expecting the actual
modal; renamed it to ".info-card-body".

NEW: GIS INTELLIGENCE — 3 MAP STYLES WITH REAL GHANA BOUNDARIES
------------------------------------------------------------------
Reviewed 6 references on map/geo-visualization types (ArcGIS Living
Atlas, GeeksforGeeks, ThoughtSpot, a Medium "top 10 map types"
piece, Flourish, and AnyChart's geovisualization chart guide). They
converge on the same three core map styles for this kind of regional
data — proportional symbol, choropleth, and heatmap — so that's what
got built. GIS Intelligence previously only had one (proportional
symbol / bubble markers).

WHAT'S NEW:
- Proportional symbol (existing) — circle markers sized/colored by value
- Choropleth (NEW) — Ghana's actual 16 region boundaries, shaded by
  whichever layer (health/agriculture/education) is active
- Heatmap (NEW) — density-blended surface via the Leaflet.heat plugin

THE REAL WORK: GHANA REGION BOUNDARIES
-------------------------------------------
The choropleth needed actual geographic polygon data, not just the
16 centroid points already in the app. Sourced a genuine open GeoJSON
of Ghana's 16 regions (traced through geoBoundaries/HDX and a public
GitHub repo — virgoaugustine/Ghana-GeoJSON-data — via the GitHub API,
since the geoBoundaries file itself turned out to be a Git-LFS
pointer rather than real data). Verified all 16 region names matched
the app's existing data exactly before using it. The raw file was
242KB across 10,044 coordinate points — too heavy to embed inline —
so it was simplified with a proper Douglas-Peucker algorithm (not
just crude decimation) down to 36KB / 2,100 points, then visually
verified with a matplotlib render showing all 16 regions still
correctly shaped and labeled before it ever touched the app.

TESTED PROPERLY THIS TIME: Chart.js, Leaflet core, and Leaflet.heat
were all downloaded via npm and loaded fully locally for testing —
previously only Chart.js got this treatment while Leaflet itself
remained CDN-blocked and untested in earlier rounds. With everything
loading, confirmed: all three map styles render correctly, switching
between health/agriculture/education layers correctly re-colors the
choropleth, clicking a choropleth polygon opens the same region
detail modal as the existing list, dark mode and mobile layouts both
hold up, the heatmap gracefully falls back to a friendly empty state
if the plugin can't load, and a full 12-view regression sweep came
back with zero console errors.

NEW: homepage.html — A COMPLETE HOMEPAGE REBUILD (16 sections)
--------------------------------------------------------------------
Built from a detailed, section-by-section brief calling for something
"radically different from a conventional SaaS landing page" — one
that sells the vision and intelligence engine rather than a wall of
modules. This supersedes the earlier landing.html with a much richer
build:

1.  Nav — Platform/Solutions/Intelligence/Data/Resources/Pricing,
    region selector, Sign In / Request Demo / Get Started
2.  Hero — animated "live intelligence" panel: real-time clock,
    pulsing map points, live stat cards, an AI insight with a
    blinking typing cursor. This is the signature visual the brief
    called "the most important section."
3.  The IntelligenceOS Promise — Collect → Understand → Predict →
    Recommend → Act, five icon stages with connecting arrows
4.  Ask IntelligenceOS — a full worked example: a real question, an
    AI analysis paragraph, a mini map, a ranked bar chart, confidence
    level, sources and a recommended action. Built to be "the
    signature experience of the entire website," per the brief.
5.  The Ecosystem — 8 sector-grouped module cards (GovOS, BusinessOS,
    NGO Intelligence, HealthOS, AgroOS, EduOS, ClimateOS, ResearchOS)
    instead of a flat wall of 20 modules
6.  Africa Data Cloud — 14 data-source chips (World Bank, WHO,
    UNICEF, FAO, AfDB, OpenStreetMap, satellite data, etc.)
7.  GIS + Intelligence — layer-chip selector + map visual
8.  AI Command Centre — dark section, terminal-style query demo with
    dataset/district/record counters and an analysis-complete state
9.  From Data to Decision — the Power BI vs. IntelligenceOS contrast
    card, plus the DATA→AI ANALYSIS→INSIGHT→PREDICTION→
    RECOMMENDATION→ACTION→IMPACT flow. The brief calls this "the
    philosophical backbone of the company."
10. Real-World Use Cases — 7 clickable question cards
11. Built for Serious Organizations — 6 trust pillars (Secure,
    Explainable, Scalable, Interoperable, Multilingual, AI-Native)
12. Who Uses IntelligenceOS — 6 audience cards + 4 "coming soon" tags
13. Built in Africa — dark, emotional section with the Ghana → West
    Africa → Africa → The World journey
14. Security & Trust — 10-item security grid, given its own section
    rather than buried in the footer
15. Final CTA
16. Footer — full Platform/Solutions/Company/Social link columns

Color discipline followed per the brief: ~70% white/light, ~20% navy
for authority sections, ~10% teal for actions and highlights — not
"green everywhere just because the logo uses green."

BUGFIX CAUGHT DURING TESTING: the nav's "Sign In" / "Request a Demo"
text links didn't collapse on mobile, causing horizontal page
overflow (confirmed via body.scrollWidth = 618px on a 390px viewport
— the page was actually wider than the screen). Fixed by hiding them
at the same breakpoint as the main nav links; verified scrollWidth
drops to exactly 390px after the fix.

RELATIONSHIP BETWEEN THE THREE HTML FILES
------------------------------------------------
- index.html — the actual product/app (Command Centre and all 12
  modules). This is what a logged-in user works in.
- homepage.html — the NEW, full public marketing homepage described
  above. Recommended as the real public entry point going forward.
- landing.html — the EARLIER, simpler marketing page from a previous
  round. Kept for reference but superseded by homepage.html; you
  likely don't need to keep pushing this one.

If you want homepage.html to be what loads at your root domain,
follow the same rename pattern as before: rename index.html to
app.html, then rename homepage.html to index.html — and update the
"Get Started"/"Explore IntelligenceOS" links inside homepage.html
from href="index.html" to href="app.html" first, or those buttons
will 404.

UPDATE: BIGGER LOGO + SHRINKING STICKY HEADER ON SCROLL
------------------------------------------------------------
Two fixes to homepage.html based on direct feedback:
- Logo increased from 38px to 54px tall at the top of the page —
  bold and clearly visible, matching the same fix applied to the
  app's sidebar earlier.
- The header now shrinks as you scroll: logo, padding, buttons and
  nav links all compact down smoothly (95px → 54px measured height,
  a 43% reduction) while staying pinned to the top in one line with
  every nav item still visible — verified this isn't just a CSS
  effect but an actual JS-driven state change (checked
  el.classList.contains("scrolled") directly), and that scrolling
  back to the top correctly restores full size.

BUGFIX CAUGHT DURING TESTING: increasing the logo size pushed the
mobile nav past the viewport edge — confirmed via
document.body.scrollWidth reading 400px on a 390px-wide viewport,
a real 10px horizontal overflow, not a visual guess. Fixed by adding
a mobile-specific breakpoint that caps the logo and button sizing
tighter on narrow screens; reverified scrollWidth reads exactly 390
in both the top and scrolled states afterward.

UPDATE: THE "ENGINE" IS NOW VISIBLE (homepage review implemented)
------------------------------------------------------------------
Per detailed review feedback, this was explicitly an ADDITIVE update,
not a redesign — the reviewer was clear the existing structure was
strong and should be kept. Five additions make the underlying
IntelligenceOS engine visible rather than implied:

1. OS STATUS BAR — a thin telemetry strip beneath the nav on every
   page load: "● INTELLIGENCEOS ENGINE ONLINE · 12 MODULES ACTIVE ·
   16 REGIONS · 1.2M FARMERS · 3,847 HEALTH FACILITIES · LIVE DATA".
   Same numbers as before, reframed as system telemetry instead of
   marketing stats — exactly the reviewer's suggested reframe.

2. THE INTELLIGENCEOS ENGINE DIAGRAM — new section right after the
   hero: Data Sources (WHO/FAO/GSS/GIS/Survey) flowing into an
   Intelligence Core (AI Engine/Knowledge Graph/Prediction) flowing
   into a Decision Layer (Insights/Forecast/Actions), with small
   animated dots flowing along the connectors and a live telemetry
   line underneath. Built to match the reviewer's ASCII mockup
   closely while staying "premium + executive," not gimmicky.

3. OS KERNEL DIAGRAM — inserted at the top of the Ecosystem section,
   above the existing 8 module cards (which stay exactly as they
   were): IntelligenceOS → OS Kernel (AI Engine, Knowledge Graph,
   Data Engine, GIS Engine, Search Engine, Workflow Engine, Agent
   Engine) branching down via clean tree-style connector lines into
   GovOS / HealthOS / SurveyOS / AgroOS / BusinessOS. Section heading
   changed from "Intelligence for every sector" to "One intelligence
   engine. Twelve applications." per the review.

4. BUTTON RENAME — every primary entry CTA (nav, hero, final CTA)
   changed from "Get Started"/"Explore IntelligenceOS" to "Launch
   IntelligenceOS," reinforcing that visitors are launching an
   operating system, not just entering a website.

5. SECONDARY TAGLINE — "One Intelligence Engine. Every Decision."
   added under the main headline in monospace/system styling,
   giving the two-layer brand message the review recommended.

Explicitly NOT done, per the review's own caution: no fake desktop
UI, no windows/folders/icons gimmick on the landing page. Everything
added is a clean architecture diagram, not a literal "computer
desktop."

BUGS CAUGHT DURING TESTING (both real, both fixed):
- The longer "Launch IntelligenceOS" button text combined with the
  larger logo from the previous round broke the nav layout across a
  wide and very common range of laptop screens — confirmed via
  document.body.scrollWidth exceeding the viewport by up to 218px at
  1024px width, with real overflow present from roughly 980px all
  the way to 1300px. This wasn't visible at the 1440px width used in
  earlier testing, which is exactly why it was missed before. Fixed
  by raising the breakpoint at which the nav simplifies (hiding the
  secondary nav links, keeping logo + theme toggle + primary CTA)
  from 980px to 1320px, closing the gap entirely.
- Reverified with a full sweep across 11 viewport widths from 390px
  to 1440px after the fix: zero overflow at every single width,
  zero console errors throughout, including a full scroll-through of
  the entire page and dark mode toggle.

UPDATE: FIXED A STALE CROSS-LINK BETWEEN THE APP AND HOMEPAGE
------------------------------------------------------------------
Caught while reviewing consistency across all three HTML files: the
app's sidebar logo (click-to-go-home) was still linking to the
EARLIER, simpler landing.html from several rounds ago — not the new
comprehensive homepage.html built to address the review comments.
This meant the round-trip (homepage → Launch IntelligenceOS → app →
click logo) would dead-end back on an outdated page missing the
entire Engine/Kernel/status-bar work.

Fixed the link and verified the full loop with both files actually
present together (not just checking the href string) — launched the
app from homepage.html, confirmed the URL changed to index.html,
clicked the app's logo, confirmed it correctly landed back on
homepage.html. Zero console errors through the whole round-trip.

FILE STATUS — landing.html IS NOW FULLY OBSOLETE
--------------------------------------------------
With this fix, there is no longer any link anywhere in the system
that points to landing.html. It's safe to stop pushing it to your
repo — homepage.html is the complete, current, and only marketing
entry point. Keeping landing.html around only risks someone linking
to it externally (e.g., from a saved bookmark or an old social post)
and seeing the outdated version.

UPDATE: FIXED SYSTEMIC SPACING + A REAL LAYOUT BUG (full review)
------------------------------------------------------------------
Did a proper section-by-section visual audit of the live page (not
just a glance) by rendering it, cropping it into ~900px segments,
and inspecting each one. Found two real issues:

1. EXCESSIVE, INCONSISTENT WHITESPACE BETWEEN SECTIONS. Nearly every
   section boundary had a ~200-250px dead zone — noticeable enough
   that transitions like "Explore all intelligence suites" button →
   "Africa Data Cloud" heading, or the 5-stage flow → "Ask
   IntelligenceOS" heading, felt like separate pages rather than one
   continuous site. Root cause: the base section padding (110px top
   + 110px bottom = 220px combined at every boundary) was too
   generous once the page grew longer with the new Engine and Kernel
   sections. Reduced to 80px top/bottom and tightened the
   section-head bottom margin from 56px to 48px — cut ~890px off the
   total page height while keeping generous, intentional breathing
   room, not a cramped page.

2. THE "IMPACT" PILL IN THE DATA-TO-DECISION FLOW WAS BROKEN. The
   DATA → AI ANALYSIS → INSIGHT → PREDICTION → RECOMMENDATION →
   ACTION → IMPACT chain was overflowing its container width at
   1440px, causing "IMPACT" to wrap onto its own orphaned, oddly
   centered line instead of continuing the flow naturally. Fixed by
   widening the container and tightening the step padding/gap/font
   size slightly so all 7 steps + 6 arrows fit on one line at normal
   desktop widths, while still wrapping gracefully on mobile.

Reverified after both fixes: zero horizontal overflow across 8
viewport widths (390px to 1440px), zero console errors through a
full scroll-through in both light and dark mode.

homepage.html and landing.html remain byte-for-byte identical.

UPDATE: REAL GHANA MAPS + NAV RIGHT-ALIGNMENT BUG FIXED
------------------------------------------------------------------
Two direct fixes from feedback:

1. ALL THREE DECORATIVE MAPS ARE NOW REAL GHANA GEOGRAPHY, NOT
   HAND-DRAWN BLOBS. The hero live panel, the "Ask IntelligenceOS"
   mini map, and the GIS + Intelligence section visual were all
   using invented, generic blob shapes that didn't represent any
   real place. Fixed properly, not just "close enough": computed an
   accurate national outline by taking the real Ghana region
   boundary data already verified and used in the actual app's
   choropleth map (from geoBoundaries via the GitHub API), unioning
   all 16 regions into a single polygon with Shapely (a real GIS
   library, not a manual approximation), then simplifying it to a
   clean ~117-point outline suitable for a small decorative graphic.
   Verified visually before embedding — rendered the outline alone
   on a plain background and confirmed it's immediately recognizable
   as Ghana. Also repositioned the colored dots on each map to sit
   at sensible real locations (e.g., the Ask IntelligenceOS map's
   risk dots now cluster in the north, matching the accompanying
   text about Upper West/North East/Savannah).

2. THEME TOGGLE AND "LAUNCH INTELLIGENCEOS" WERE COLLAPSING TO THE
   TOP-LEFT NEXT TO THE LOGO instead of staying at the top-right.
   Root cause: the right-alignment relied on margin-left:auto on the
   "Africa ▾" region pill — but that pill gets hidden at narrower
   desktop widths (below 1320px, added in an earlier round), and
   once it disappeared, so did the only thing pushing everything
   after it to the right. Fixed properly by moving the auto-margin
   onto a dedicated wrapper around the region pill + icon/button
   cluster together, so right-alignment no longer depends on any one
   specific element staying visible — it now holds regardless of
   which nav elements are hidden at a given screen width. Verified
   specifically at 1024px (where the bug was originally visible) as
   well as across the full 390px-1440px range, in both light and
   dark mode.

homepage.html and landing.html remain byte-for-byte identical.

FILE STRUCTURE — SIMPLIFIED TO TWO FILES
-------------------------------------------
landing.html has been retired entirely. It was only ever a duplicate
copy of homepage.html, kept in sync to paper over a URL-confusion
problem — a real design smell, not a real solution. Going forward
there are exactly two files:

- index.html   — the actual product/app (Command Centre, GIS
                  Intelligence, Dashboard Studio, all 12 modules)
- homepage.html — the public marketing homepage

Confirmed there are zero remaining references to landing.html
anywhere in either file before removing it — the app's "click logo
to go home" link points to homepage.html, and homepage.html's
"Launch IntelligenceOS" buttons point to index.html. Delete
landing.html from your repo; nothing links to it anymore.

Your live URL (https://fadl462.github.io/intelligence-os/) will
continue to open index.html directly (the app) since that's the
GitHub Pages default for a repo root. If you'd rather the homepage
open first at that bare URL, that's the rename described earlier in
this document (index.html → app.html, homepage.html → index.html,
plus updating the internal links to match) — still on offer whenever
you want it, but not done here since you didn't ask for it this time.

UPDATE: SECOND REVIEW ROUND — 8 CHANGES IMPLEMENTED
------------------------------------------------------------------
Went through a detailed 12-point review. Kept 2 points as already
done (nav language, "One engine, twelve applications" heading),
skipped 3 as redundant with existing content (full hero rebuild —
duplicates the Engine section already below it; reduced module-card
emphasis — too subjective to action without cutting good content;
sector list under "decision-makers everywhere" — duplicates the
Ecosystem section's existing 8 sectors), and implemented 8 concrete,
non-redundant changes:

1. Sharpened "There's an engine underneath" copy to read as
   infrastructure language; expanded the Intelligence Core box to
   name specific engines (AI/ML, Knowledge Graph, GIS, Prediction)
2. Made the OS Kernel diagram INTERACTIVE — hover any engine tag
   (AI Engine, GIS Engine, etc.) and a hint line updates live to show
   which application it powers (e.g. "GIS Engine → AgroOS →
   Agricultural Intelligence") — this was the review's single
   biggest recommendation
3. Expanded the Kernel's app row from 5 to all 8 apps, now matching
   the ecosystem cards below it exactly, in a clean 4×2 grid
4. Animated the "Ask IntelligenceOS" demo — it now visibly performs
   a 4-step searching/analysing sequence (spinners → checkmarks,
   staggered) before revealing the answer, auto-triggered once via
   IntersectionObserver when scrolled into view, replayable by
   clicking the question
5. Rebuilt the linear 5-stage flow into "The Intelligence Loop" — 
   added a 6th "Measure" stage and a visual loop-back indicator
   ("feeds back into Collect — the system keeps learning")
6. Replaced the 2-card BI comparison with the full 6-row table the
   review specified (Shows data/Understands data, Reports what
   happened/Explains why, etc.), sharpened the headline to "Not just
   a dashboard. An intelligence system."
7. Added a "DATA SOURCES → INTELLIGENCEOS → AFRICA" flow visual above
   the data-source chip cloud, and made the GIS layer chips
   (Population/Health/Education/etc.) genuinely clickable — clicking
   switches the active state and confirms via toast
8. Animated the Ghana → West Africa → Africa → World journey — a
   wave pulses sequentially through the future expansion path while
   Ghana stays permanently solid as the current live state

BUG CAUGHT AND FIXED DURING TESTING: the completed Ask IntelligenceOS
processing checklist (4 checkmarked rows) was rendering directly
adjacent to the answer content with no visual separation — cramped
and easy to misread as one clashing block. Fixed with a divider and
tighter, muted styling for the completed rows so they read as a
"receipt" rather than competing with the actual insight for
attention.

TESTED PROPERLY THIS TIME BEFORE SHIPPING: screenshotted every one of
the 8 changes individually (not just the overall page) — confirmed
the Ask demo animation actually plays through and completes, the
kernel hover genuinely updates the hint text on real mouse hover (not
just assumed from the CSS), the GIS layer chips actually switch
active state on click, and the journey animation cycles through all
three future steps while Ghana stays solid. Then ran a full regression:
zero horizontal overflow across 5 viewport widths (390px–1440px),
zero console errors through a complete scroll-through in dark mode,
and confirmed the Intelligence Loop's 6 steps reflow cleanly into a
2-column grid on mobile.

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
