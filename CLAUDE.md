# Cookie Crumbs — Project Context

## What this is
A website for a UI Programming class (SNU Spring 2026, P2 Public Utility assignment).
The concept: an adaptation of the Vildkatten game mechanic to visualize HTTP cookies.
Visitors paste a URL they've been to → it becomes a "crumb" (organic blob shape) scattered on a shared canvas.
Inspired by everynoise.com (dense scatter of labels) and clickclickclick.click (surveillance aesthetic).

## The file
`cookie-crumbs.html` — single self-contained HTML/CSS/JS file. No build step, no dependencies.
Also in this folder: `assets/style.css` (not currently used).

## How it works
1. Visitor opens the site
2. Reads intro text explaining HTTP cookies and the concept
3. Pastes a URL + optional alias/tag in the fixed bottom bar
4. A crumb (white organic SVG blob) scatters randomly on the canvas
5. Hover any crumb → neon glow + domain name + cookie fact tooltip + timestamp
6. Click any crumb → opens the URL in a new tab
7. Crumbs persist via localStorage (no backend needed yet)

## Current state (as of last session)
- ✅ Full layout: fixed top stats bar, scrollable canvas, fixed bottom form bar
- ✅ Light mode by default, auto dark mode at night (20:00–06:00 local time)
- ✅ Organic SVG blob crumbs with random shape/size/rotation
- ✅ Hover: neon color glow + domain label + tooltip (alias, cookie fact, timestamp)
- ✅ Click crumb → opens URL
- ✅ localStorage: crumbs survive page refresh
- ✅ Seed crumb: everynoise.com appears automatically on first load
- ✅ Bottom bar: "Make crumb here → | alias input | Randomize | url input | Add crumb"
- ✅ Top bar: Crumbs collected | People visited | Your time spent here | People here right now
- ✅ Randomize button assigns a random cookie-type tag (session cookie, rabbit hole, etc.)
- ✅ Neon random color on button hover
- ✅ Firebase code is written but disabled (FIREBASE_ENABLED = false)

## What still needs to be done
- [ ] Set up Firebase for real-time multiplayer (for class presentation)
  - Go to console.firebase.google.com
  - Create project → Realtime Database → test mode rules
  - Paste config into the firebaseConfig block
  - Set FIREBASE_ENABLED = true
- [ ] Replace intro SVG blob with a real PNG image (place in assets/)
- [ ] Final visual polish before crit (June 9 / June 16)
- [ ] Host publicly (Firebase Hosting recommended: `firebase deploy`)

## Key design decisions made
- Black (#000) / white (#fff) with Courier New monospace throughout
- Light mode default, dark mode triggers at 8pm automatically
- Crumbs are white SVG blobs (not favicons) — organic, not corporate
- No find-the-cookie game mechanic (dropped due to time — sticker assets too much work)
- Alias/tag field: user types their own OR hits Randomize for a cookie-type label
- The site watches you back: tooltip shows cookie surveillance facts per domain

## Cookie facts by domain (in JS)
google, youtube, facebook, instagram, twitter/x, amazon, tiktok, reddit, naver, kakao, everynoise
+ 8 generic facts that rotate for unknown domains

## Firebase structure (when enabled)
- /sessions/{id}  → active user presence (auto-removed on disconnect)
- /crumbs/{id}    → { domain, href, alias, ts }
- /visitCount     → integer, increments each session

## Assignment details
- Class: UI Design Programming 1, SNU Spring 2026
- Instructor: Chris Hamamoto
- Final crit: June 9 + June 16, 2026
- Requirement: publicly accessible web utility + landing page + 2 user interviews + static mockups
