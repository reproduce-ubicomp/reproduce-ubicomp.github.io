# Reproduce! Workshop Website (`reproduce-ubicomp.github.io`)

Official website for the **Reproduce!** workshop series on reproducible methods for wearable sensing and ubiquitous computing, co-located with ACM UbiComp/ISWC. Built with Jekyll and the [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) remote theme for GitHub Pages.

---

## Repository Structure

- `index.html` — Landing page for the **active edition** (currently Reproduce! 2027, UbiComp/ISWC 2027 in Seoul).
- `_pages/` — Pages for the **active edition** (`/cfp/`, `/submission/`, `/schedule/`, `/organizers/`, `/news/`) plus `/editions/` (`_pages/editions.md`) and `/404.html`.
- `_pages/<year>/` — Archived pages for past editions (e.g., `_pages/2026/` served at `/2026/`, `/2026/schedule/`, `/2026/cfp/`, `/2026/submission/`, `/2026/organizers/`).
- `_organizers_<year>/` — Per-edition organizer collection (e.g., `_organizers_2026/` registered in `_config.yml`).
- `_posts/` — News posts across all editions (displayed by year on `/news/`).
- `_includes/archive-banner.html` — Reusable `.notice--info` banner displayed on archived edition pages.
- `_data/navigation.yml` — Top bar (`main`) and per-edition archive sidebars (e.g., `archive_2026`).
- `assets/css/main.css` — Minimal Mistakes compiled styles plus custom `.schedule-*` classes.

---

## Finalizing Reproduce! 2027 (Once Accepted & Confirmed)

1. **Remove early-planning notices & fill in dates:**
   - Update `index.html` (remove the early-planning `.notice--info` box and update wording/excerpt as needed).
   - Update `_pages/cfp.md` (replace `TBD` deadlines and remove the `.notice--warning` box).
   - Update `_pages/submission.md` (add PCS Conference/Track names and deadline; remove the `.notice--info` box).
   - Update `_pages/editions.md` (replace `"In early planning"` status under 2027).
2. **Add the 2027 Organizing Committee:**
   - Create `_organizers_2027/` with one `.md` file per organizer.
   - Register `organizers_2027` in `_config.yml` (`permalink: /organizers/:path/`) and add its `defaults:` scope (`layout: single`, `author_profile: false`).
   - Update `_pages/organizers.md` back to `layout: collection`, `collection: organizers_2027`, `entries_layout: grid`.
3. **Publish the 2027 Schedule:**
   - Replace `_pages/schedule.md` using the `.schedule` / `.schedule-day` / `<details class="schedule-item schedule-expandable">` markup (see `_pages/2026/schedule.md` for reference).
4. **Update 2026 ACM DL Links (once DOIs are published):**
   - Add paper DOIs and Adjunct Proceedings URLs to `_pages/2026/schedule.md`, `_pages/2026/index.md`, and `_pages/editions.md`.
5. **Post News Updates:**
   - Add dated posts in `_posts/YYYY-MM-DD-post-title.md` as milestones occur.

---

## Annual Rollover Checklist (Archiving 2027 for 2028+)

1. Commit final 2027 state and create an immutable git tag:
   ```bash
   git tag -a v2027 -m "Final Reproduce! 2027 website snapshot before 2028 rollover"
   ```
2. Move `_organizers_2027/` collection permalink in `_config.yml` to `/2027/organizers/:path/` and add `archive_2027` defaults.
3. Add `archive_2027` sidebar navigation in `_data/navigation.yml`.
4. Copy `index.html` body and `_pages/{cfp,submission,schedule,organizers}.md` into `_pages/2027/` with `/2027/` permalinks, `sidebar: { nav: "archive_2027" }`, and `{% include archive-banner.html year="2027" venue="UbiComp/ISWC 2027, Seoul, South Korea" %}`.
5. Update any internal `/cfp/` or `/schedule/` links inside 2027 `_posts/` to `/2027/...`.
6. Update `_pages/editions.md` to move 2027 under **Past Editions** and add 2028 under **Upcoming Edition**.
7. Reset `index.html` and root `_pages/` for the 2028 edition, verify locally, commit, and push `master` + tag `v2027`.
