# Makin'Bug website: build stages

2026-10-28 · Adrian N

Nine stages take the site from an empty GitHub account to makinbug.uk live. Each stage is one session. It says who does what, which model to use, and how you know it is done.

## How to use this plan

A big model made the choices once. Each later session only follows the steps, so a cheaper model can do it.

- Do the stages in order. Start a stage only when the one before is ticked.
- After Stage 1 the master copy of this plan is `docs/PLAN.md` in the repo (the project folder on GitHub). This tab then becomes a one-line pointer, so the plan has one home.
- A stage marked "You" is done by you in a browser. Ask Claude in a normal chat if you get stuck.
- A stage with Claude steps runs in Claude Code on the web: open claude.ai/code, pick the repo `makinbug/makinbug.github.io`, pick the model the stage names, and paste the prompt below with the stage number.
- When the pull request (a proposed change you review before it goes live) is ready, look at it on GitHub, then **Merge**.
- Until launch (Stage 7), the site at makinbug.github.io is only a test copy nobody knows about. So merging to see a change is safe. After launch, ask for screenshots in the pull request before you merge.
- Model guide: **Sonnet** for stages that need judgement (templates, design). **Haiku** for stages that only follow steps. If Haiku fails a step twice, run the stage again with Sonnet.

The prompt for every Claude stage:

```
Read CLAUDE.md and docs/PLAN.md. Do Stage N only, following its steps exactly. Open one pull request for it and tick the stage's boxes in docs/PLAN.md in the same pull request. Then stop. If a step fails twice, or the plan looks wrong, stop and tell me what happened.
```

## Decisions

The site is not a shop. It shows your CAD design, 3D printing and laser work, with one page of products that sends buyers to eBay.

| Date | Decision | Why |
| --- | --- | --- |
| 29 Oct 2026 | One "Made to Order" page for all eBay products, in three groups: Miscellaneous Bits, Airsoft Stuff, Cycling Things. No single product pages. Each row shows the eBay title, no description | Simpler to run and to add to. Each product is still found on Google through its eBay listing |
| 29 Oct 2026 | Site shows "Makin'Bug, Telford, UK" and info@makinbug.uk. No Duda shipping or returns text. | Adi's choice at Stage 3. The name and address part is not settled: see Still open |
| 29 Oct 2026 | Keep one Duda photo (the delta printer); product photos come from eBay | The product photos are already on the eBay listings; fewer files to copy |
| 28 Oct 2026 | Plan master moves to `docs/PLAN.md` at Stage 1 | One home; a cheaper model finds it without being told |
| 28 Oct 2026 | Ananke theme, plus one stylesheet of ours. Look based on anthropic.com, mistral.ai, wisprflow.ai and the Duda site | Simple, maintained base; the look comes from our own styles |
| 28 Oct 2026 | Buy buttons link to each Good 'til cancelled eBay listing | These listings keep their item number, so links last |
| 28 Oct 2026 | Claude Code on the web makes pull requests; Adi merges | Works from the phone; nothing goes live without Adi |
| 28 Oct 2026 | Free GitHub organisation `makinbug`, public repo | A private repo with Pages needs GitHub Team, about £35 to £40 a year, and hides little |
| 20 Oct 2026 | Domain from Freethought | UK company, phone support, simple panel |
| 16 Oct 2026 | Product pages with "Buy on eBay" buttons, no cart | eBay handles payment and postage |
| 16 Oct 2026 | GitHub Pages and Hugo | Free hosting, same as the FOTTP site |

Still open: whether "Makin'Bug, Telford, UK" is enough to show on the site. UK rules for online traders may need the owner's name and a full address. Decide before launch (Stage 7).

## Stages at a glance

| Stage | What | Who | Model |
| --- | --- | --- | --- |
| 0 | Set up GitHub | You | None |
| 1 | Basic site live on makinbug.github.io | Claude, then you merge | Sonnet |
| 2 | Copy text and photos off Duda | Both | Haiku |
| 3 | Main pages: Home, Services, Work, About, Contact, Privacy | Claude, from your answers | Sonnet |
| 4 | Made to Order page with eBay buttons | Claude, from your list | Sonnet |
| 5 | Look and feel | Claude, you approve | Sonnet |
| 6 | Checks before launch | Claude | Haiku |
| 7 | Domain and email | You, plus one small Claude step | Haiku |
| 8 | Switch over and close Duda | You | None |

## Rules for every session

Stage 1 copies these rules into the repo's `CLAUDE.md`, which Claude Code reads on its own at the start of every session.

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

## Stage 0: set up GitHub

**Who:** you, in a browser on the laptop or phone. About 30 minutes.

- [x] Signed in as adioan, check two-factor login is on: **Settings**, **Password and authentication**.
- [x] **Settings**, **Emails**: tick "Keep my email addresses private" and "Block command line pushes that expose my email". Your Proton address then never shows in the public history.
- [x] Make the organisation at github.com/organizations/plan. Pick **Free**. Name: `makinbug` (if taken, use `makinbug-uk` and use that name wherever this plan says makinbug). Contact email: your Proton address. It belongs to your personal account.
- [x] In the organisation, **New repository**. Name: `makinbug.github.io`. **Public**. Tick "Add a README". No licence, so your photos and designs stay yours.
- [x] Repo **Settings**, **Pages**: under "Build and deployment", set **Source** to **GitHub Actions**.
- [x] Repo **Settings**, **Rules**, **Rulesets**, **New branch ruleset**. Name "protect main", Enforcement **Active**, target the default branch. Tick "Restrict deletions", "Require a pull request before merging" (0 approvals, so you can merge Claude's work) and "Block force pushes". Save. Stage 1 adds the build check.
- [x] Open claude.ai/code and connect GitHub when asked. Install the Claude GitHub app on the makinbug organisation, with **Only select repositories**: `makinbug.github.io`.

Why the repo name: the test site then works at https://makinbug.github.io with no extra folder in the address, which avoids broken links while testing.

**Done when:** github.com/makinbug/makinbug.github.io exists, Pages source is GitHub Actions, and the repo shows in claude.ai/code.

## Stage 1: basic site live on makinbug.github.io

**Who:** Claude (Sonnet), then you. **You need ready:** Stage 0 done.

Before you start, you:

- [x] Download this tab as Markdown (the doc's download or export menu) and attach the file to the session. Claude saves it as `docs/PLAN.md`.

Claude:

- [x] Make the branch `stage-1-basic-site`.
- [x] Make `hugo.toml`: baseURL `https://makinbug.github.io/`, locale `en-GB` (Hugo 0.158 and later: `languageCode` is deprecated and gives a warning), title `Makin'Bug`, theme `ananke`.
- [x] Copy Ananke v2.19.1 into `themes/ananke` as plain files, not a submodule: `git clone --depth 1 --branch v2.19.1 https://github.com/theNewDynamic/gohugo-theme-ananke themes/ananke`, then delete `themes/ananke/.git`. Write the version in `README.md`.
- [x] Make `.gitignore` with `public/`, `resources/_gen/` and `.hugo_build.lock`.
- [x] Make `.github/workflows/hugo.yml`, based on GitHub's own Hugo workflow for Pages. Pin Hugo extended 0.167.0 (Ananke needs 0.161 or later). Run it on every pull request and every push to `main`. Name the build job `build`. Deploy to Pages only on a push to `main`.
- [x] Make `content/_index.md` with one line: "Makin'Bug: new website coming soon."
- [x] Make `CLAUDE.md`: the "Rules for every session" section of this plan, plus "The plan is docs/PLAN.md."
- [x] Save the attached Markdown as `docs/PLAN.md`.
- [x] Download Hugo extended 0.167.0 for Linux from github.com/gohugoio/hugo/releases into the session (not into the repo) and run `hugo --gc --minify`. No errors, no warnings.
- [x] Open the pull request "Stage 1: basic site".

After the pull request, you:

- [x] Check the pull request's `build` check is green, then **Merge**.
- [x] Wait a few minutes, then open https://makinbug.github.io. You should see the "coming soon" line.
- [x] Ruleset "protect main": tick "Require status checks to pass" and add `build`. Save. Now nothing can merge if the site fails to build.
- [x] Ask Claude in a normal chat to swap this tab for a pointer to `docs/PLAN.md`.

**Done when:** the test site shows the line, and the build check is required.

## Stage 2: copy text and photos off Duda

**Who:** you, then Claude (Haiku). This stage only copies. Later stages turn the copy into pages.

Before you start, you:

- [x] Open each page on makinbug.dudaone.com: Home, Store (Cycling Things, Airsoft Stuff), Services, About, Privacy. Save every photo you want to keep, plus the logo (right-click, **Save image as**), into one folder.
- [x] Attach the photos to the session. If there are too many, upload them on GitHub instead: in the branch `stage-2-duda-copy`, **Add file**, **Upload files**, into a folder `incoming/`.

Claude:

- [x] Make (or use) the branch `stage-2-duda-copy`.
- [x] Read each Duda page and save its text as Markdown in `docs/duda-copy/`, one file per page (for example `services.md`). Skip "My Account". If the session can't open the site, ask Adi to paste each page's text.
- [x] Copy the four customer reviews word for word, with the names exactly as Duda shows them, into `docs/duda-copy/reviews.md`.
- [x] Resize each photo to the photo rule, save it in `docs/duda-copy/images/`, and delete `incoming/` if it was used.
- [x] List every photo in `docs/duda-copy/images.md`: file name and one line on what it shows (later this becomes its alt text).
- [x] Open the pull request "Stage 2: copy of the Duda content".

After the pull request, you:

- [ ] Check nothing is missing, then merge with **Squash and merge**. This keeps any big original photos out of the site's history.

**Done when:** every Duda page and photo you want is in `docs/duda-copy/`.

## Stage 3: the main pages

**Who:** you, then Claude (Sonnet).

Before you start, you write in the session:

- [x] For each service (CAD design, 3D printing, laser), 3 to 5 lines: what you do, materials, typical jobs, how people order.
- [x] Your full name as it should appear, and "trading as Makin'Bug".
- [x] The address to show. Decide between home and a virtual office (a real street address that forwards your post, for a monthly fee). The rule asks for an address where legal papers can reach you, so a PO box is best avoided. Not legal advice: if unsure, ask Trading Standards.
- [x] The email to show, for example `hello@makinbug.uk`. It starts working at Stage 7.

Claude:

- [x] Make the branch `stage-3-pages`. Use the text in `docs/duda-copy/` and Adi's answers. Don't invent facts.
- [x] Home, `content/_index.md`: one line on what Makin'Bug does; three short service blocks linking to their pages; a space for featured products (Stage 4 fills it); the four reviews; Facebook and Instagram links.
- [x] Services: `content/services/_index.md` plus `cad-design.md`, `3d-printing.md` and `laser.md`.
- [x] Work, `content/work/_index.md`: a grid of past work photos with captions. Add a small shortcode `layouts/shortcodes/gallery.html` that shows the page's own photos as a grid.
- [x] About, `content/about.md`.
- [x] Contact, `content/contact.md`: email, Facebook, Instagram, then the legal details (full name, trading as Makin'Bug, address).
- [x] Privacy, `content/privacy.md`: no cookies and no tracking; GitHub Pages logs visitors' IP addresses for security; eBay handles orders under its own privacy policy.
- [x] Menu: Home, Services, Work, Products, About, Contact. Footer: name, address and a Privacy link.
- [x] Build, then open the pull request "Stage 3: main pages".

After the pull request, you:

- [ ] Merge, then read every page on makinbug.github.io.

**Done when:** all six pages show, and the legal details are on Contact and in the footer.

## Stage 4: Made to Order page with eBay buttons

**Who:** you, then Claude (Sonnet).

All eBay products sit on one page, "Made to Order", at `/products/`. There are no single product pages. Each product is one row: a small photo on the left, then the eBay title, then a "See price and buy on eBay" button on the right. On a phone the button drops below the text.

Before you start, you:

- [x] Make a list. For each product: its eBay title, category (Miscellaneous Bits, Airsoft Stuff or Cycling Things), its eBay link and one photo. No descriptions: the eBay title says enough. Attach the list to the session as `products.yaml`.
- [x] Pick 3 products for the home page.
- [ ] Make sure each one is a Good 'til cancelled listing. In eBay's selling settings, check the out-of-stock option is on, so a listing that sells out is hidden but not ended. Then its link keeps working.

Claude:

- [ ] Make the branch `stage-4-products`.
- [ ] Put every product in one file, `data/products.yaml`, as in the example below. Start from Adi's list.
- [ ] For each product, download the photo at `photo_url`, make it at most 1600 pixels wide, and save it in `assets/products/` under the `image` name. Then delete the `photo_url` lines.
- [ ] No prices on the site. eBay prices change, and two prices that disagree look bad.
- [ ] Clean each eBay link down to `https://www.ebay.co.uk/itm/<number>`, with no tracking bits.
- [ ] Template `layouts/products/list.html`: three groups, in this order: Miscellaneous Bits, Airsoft Stuff, Cycling Things. Inside a group, sort by `weight`. Hide a group that has no products. Each row as described above. The photo and the name also link to the listing.
- [ ] Make the photos small with Hugo's image processing (about 160 pixels wide, plus a 320 pixel copy for sharp screens). Keep the full photo out of the page.
- [ ] If a product has a category that isn't one of the three, the build must stop with a clear error (`errorf`), so a typo can't hide a product.
- [ ] `content/products/_index.md`: title "Made to Order" and a one-line intro. In `hugo.toml`, rename the menu item to "Made to Order". Keep the address `/products/`.
- [ ] Home page: in the featured space, show the 3 products marked `featured: true`, each with its photo, title and eBay button, then a "See everything" link to `/products/`.
- [ ] Write `docs/ADD-A-PRODUCT.md`: how Adi adds a product himself on GitHub's website (upload the photo to `assets/products/`, copy one entry in `data/products.yaml` and change its lines, commit to a new branch, open a pull request, merge). Say that the spaces at the start of each line matter.
- [ ] Build, then open the pull request "Stage 4: Made to Order page".

```
- name: "AK ODIN M12 Speedloader Adapter Mid-Cap Magazine Airsoft With BB Retention"
  category: "Airsoft Stuff"
  ebay: "https://www.ebay.co.uk/itm/123456789012"
  image: "odin-speedloader-adapter.jpg"
  alt: "Black 3D printed adapter fitted to an ODIN speedloader"
  weight: 10
  featured: true
```

After the pull request, you:

- [ ] Merge, then click every buy button on makinbug.github.io, on the page and on the home page. Each must open the right listing.

**Done when:** every product shows in the right group and every button opens its listing.

## Stage 5: look and feel

**Who:** you, then Claude (Sonnet).

Before you start, you:

- [ ] Take screenshots of the home pages of anthropic.com, mistral.ai, wisprflow.ai and your Duda site, on the laptop and on the phone.
- [ ] Under each one, write a line on what you like (for example "calm colours", "big clear headings").
- [ ] Attach the screenshots, your notes and the logo file to the session.

Claude:

- [ ] Make the branch `stage-5-look`.
- [ ] Write `docs/STYLE.md`, a short style guide: 4 to 6 colours with hex codes, two fonts, spacing, buttons and cards. Base it on what Adi likes. Don't copy any site's logo, artwork or exact layout.
- [ ] Fonts: free fonts with an open licence, stored in `static/fonts/` and served from the site itself, never linked from Google Fonts.
- [ ] Put all the styles in `assets/css/custom.css` and load it with Ananke's `custom_css` setting (see `themes/ananke/README.md`). Template tweaks go only in `layouts/`.
- [ ] Add the logo and a favicon (the small icon in the browser tab).
- [ ] If the session can run a browser, take screenshots of every page type at phone width (390 pixels) and laptop width (1280 pixels), and describe them in the pull request.
- [ ] Build, then open the pull request "Stage 5: look and feel".

After the pull request, you:

- [ ] Merge, then check every page on the phone and the laptop. For changes, run a new session: "Stage 5 fix: " plus what to change.

**Done when:** you are happy with how it looks on both screens.

## Stage 6: checks before launch

**Who:** Claude (Haiku), then you.

Claude:

- [ ] Make the branch `stage-6-checks`.
- [ ] Build: no errors, no warnings.
- [ ] Check every link and image inside the built site (the `public/` folder). Fix any broken ones.
- [ ] Check every image has alt text, and every page has a title and a one-line description (Google shows it in search results).
- [ ] Check there is a "page not found" page, and that `sitemap.xml` and `robots.txt` are made and let search engines in.
- [ ] Search the built pages for scripts, fonts or styles loaded from other websites. There must be none.
- [ ] Check the only email and address are the ones on Contact and in the footer.
- [ ] Open the pull request "Stage 6: checks", with each check and its result.

After the pull request, you:

- [ ] Read every page once more on your phone, then merge.

**Done when:** every check in the pull request passed.

## Stage 7: domain and email

**Who:** you, plus one small Claude step (Haiku). DNS is the address book that sends visitors to your site. Changes can take up to 24 hours to work. Keep to this order: GitHub must know about the domain before DNS points to it, or someone else could use it ([GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)).

You:

- [ ] Buy makinbug.uk (see "Step 1: get makinbug.uk" in the first tab).
- [ ] Prove the domain is yours: organisation **Settings**, **Pages**, **Add a domain**, `makinbug.uk`. GitHub shows a TXT record with a name like `_github-pages-challenge-makinbug` and a value to copy. Add it in the Freethought portal's DNS, wait, then click **Verify**. Never delete this record.
- [ ] Repo **Settings**, **Pages**, **Custom domain**: `makinbug.uk`, **Save**.
- [ ] In Freethought's DNS, remove any parking records for `@` and `www`, then add:

| Type | Name | Points to |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | makinbug.github.io |

- [ ] When the Pages settings say the DNS check passed, tick **Enforce HTTPS** (the padlock). It can take up to 24 hours to appear.

Claude (prompt: "Do the Claude step of Stage 7"):

- [ ] Branch `stage-7-domain`: change baseURL in `hugo.toml` to `https://makinbug.uk/`. Build, then open the pull request. You merge it.

Email, you:

- [ ] In Proton's settings, under domain names, add `makinbug.uk`. Add each record Proton shows (verification, MX, SPF, DKIM, DMARC) in Freethought's DNS.
- [ ] Make the address you chose at Stage 3, then send a test email both ways.

**Done when:** https://makinbug.uk and https://www.makinbug.uk both show the site with the padlock, and the test email works.

## Stage 8: switch over and close Duda

**Who:** you.

- [ ] Change the website link on Facebook and Instagram to https://makinbug.uk. Not on eBay: eBay's rules ban links to other websites in listings, shop pages and profiles ([eBay links policy](https://www.ebay.ie/pages/help/policies/listing-links.html)).
- [ ] Google Search Console (a free Google tool that tells Google about your site): add makinbug.uk as a **Domain** property, prove it with the TXT record it gives you in Freethought's DNS, then submit `https://makinbug.uk/sitemap.xml`.
- [ ] If you have a Google Business Profile, change its website link.
- [ ] Keep Duda running for 2 to 4 weeks. If Duda lets you, add a line on its home page: "We've moved to makinbug.uk".
- [ ] Check Duda's renewal date, then cancel it before then.
- [ ] In a laptop vault session, ask Claude to save the plan in the wiki and update the project's links doc.

**Done when:** every box is ticked and Duda is closed.

## Sources

Checked 28 Oct 2026.

- [GitHub: what is GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages) (private repos need a paid plan; visitor IP addresses are logged)
- [GitHub: plans](https://docs.github.com/en/get-started/learning-about-github/githubs-plans) and [GitHub pricing](https://github.com/pricing) (Team at US$4 a person a month)
- [GitHub: managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) (DNS records and order)
- [GitHub: verifying a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages)
- [Ananke releases](https://github.com/theNewDynamic/gohugo-theme-ananke/releases) (v2.19.1, 26 Sep 2026; needs Hugo 0.161 or later)
- [eBay links policy](https://www.ebay.ie/pages/help/policies/listing-links.html)
- [Business Companion: business names and website details](https://www.businesscompanion.info/node/604/printable/print)
- [ByteStart: PO boxes for sole traders](https://www.bytestart.co.uk/go-self-employed/royal-mail-po-box-business-address/)
