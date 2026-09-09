# Claude Code Handoff: a.chandrashaker.in Landing Page

**Status:** Ready for implementation.
**Repo:** NEW, separate from `student-achievement-tracker` and the new `exam-marks-tracker` repo. Repo name: `chandrashaker-app`.
**Purpose:** `a.chandrashaker.in` becomes a simple landing/directory page listing each standalone app, linking out to wherever each is actually hosted. This repo does NOT contain app logic — it's a directory only.

---

## Scope

- Static page (plain HTML/CSS, no framework needed — matches the simplicity of the linked apps).
- Card or list layout, one entry per app: name, one-line description, link.
- Initial entries:
  - **Student Achievement Tracker** → link to wherever `student-achievement-tracker` is actually deployed
  - **Exam Marks Entry** → link to wherever `exam-marks-tracker` is deployed
- Designed to be extended with more entries over time as new apps are built — keep the entry list in a simple array/config at the top of the file (or a small JSON), not hardcoded scattered HTML, so adding a new app later is a one-line change.
- No backend, no auth, no build step ideally (plain static file(s) deployable to Cloudflare Pages directly).

## Hosting

- Cloudflare Pages project, Custom Domain `a.chandrashaker.in` pointed at this new repo's Pages project.
- **[MANUAL]** Confirm whether `a.chandrashaker.in` currently resolves to the achievement-tracker repo directly (likely, if that repo IS what's live there today) — if so, this is a cutover: the achievement tracker moves to its own subpath/URL, and this new landing-page repo takes over the root domain. Flag this explicitly to the user before touching DNS/Custom Domain settings, since it changes what a bookmarked `a.chandrashaker.in` link currently shows.

## Git commit policy

- **No AI co-author trailers** (e.g. `Co-Authored-By: Claude`) on any commit in this repo — standing policy across all Chandras Edu repos. Commit normally under the existing git identity, no attribution footer.

## Explicitly out of scope

- Any app logic, OCR, Sheets integration — lives in each app's own repo.
- Auth — none needed, this is a static directory.

---

## Decision update (2026-09-09): domain layout revised

Supersedes the "Hosting" section's cutover concern above — **no cutover needed**.

- **`apps.chandrashaker.in`** → this landing page repo (plural, since it's a directory of multiple apps — matches common convention, e.g. `apps.google.com`).
- **`a.chandrashaker.in`** → stays exactly as-is, pointed at Student Achievement Tracker directly. No DNS change, no bookmark breakage.
- **`marks.chandrashaker.in`** → Exam Marks Tracker, once deployed. Entry name updated from "Exam Marks Entry" to "Exam Marks Tracker" in [index.html](index.html).

Cloudflare Pages Custom Domain for this repo should be set to `apps.chandrashaker.in`, not `a.chandrashaker.in`.
