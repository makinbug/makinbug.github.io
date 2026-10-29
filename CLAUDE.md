# Rules for every session

The plan is docs/PLAN.md.

- Do only the stage you were asked for. One branch and one pull request per stage. Never push to `main`.
- Follow the steps; don't redesign. If a step looks wrong, say so in the pull request and stop.
- The repo is public. Nothing private goes in it: no notes, no supplier details, no phone numbers. The only address is the one Adi picks at Stage 3.
- British spelling. Plain, short sentences. No em dashes or en dashes, in site text or in messages to Adi.
- Never edit `themes/ananke`. Styles go in `assets/css/custom.css`. Template changes go in `layouts/`.
- Never commit `public/`, `resources/_gen/` or `.hugo_build.lock`.
- Photos: at most 1600 pixels wide, JPEG quality about 82, file names in lower case with hyphens. Every image has alt text (a short description for people who can't see it).
- No tracking, no cookies, and no scripts or fonts loaded from other websites.
- Test with `hugo --gc --minify`, using the Hugo version pinned in `.github/workflows/hugo.yml`. A clean build shows no warnings.
- Pull request text has three parts: **What changed**, **How I checked**, **Still open** (or "Nothing").
- If a step fails twice, stop and explain what failed.
