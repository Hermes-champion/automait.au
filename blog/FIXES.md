# Legal fixes applied: blog build (staging)

- **Source review:** `/root/venture/reviews/2026-11-10-articles.md` (PASS-WITH-FIXES: K1, A1-1, A2-1 MEDIUM; plus LOWs).
- **Drafts:** `/root/venture/marketing/articles/*.md`. The drafts were not edited. Fixes are applied at build time by `/root/venture/marketing/tools/build_blog.py`. The script uses exact string replacement and asserts exactly one match per fix, so the build fails if a draft changes.
- **Outputs:**
  - `staging/blog/index.html`
  - `staging/blog/<slug>/index.html` (×2)
  - `staging/sitemap.xml`

## Required (MEDIUM) fixes

| Fix | Article | How it was applied |
|---|---|---|
| **K1** CTA promised "compliant" review requests, but kit templates 4A–4C lack ABN/phone | A1 (CTA, L121) | The kit is still unfixed: `kit.md` 4A/4C sign off `– [Name]` / `– [Name], [Business Name]`, with no ABN. So Legal's **fallback CTA wording** was used. After "...covering the Spam Act, the ACL and Google's review rules", I appended: ` (add your ABN and phone number to each message, as described above).` |
| **K1** | A2 (CTA, L125) | Replaced `compliant Google review requests` with `review-request templates with Spam Act basics` (Legal's fallback). |
| **A1-1** checklist said "ABN **or** contact details" | A1 (L114) | Replaced with `- [ ] Business name and ABN, contact details, and an opt-out in every message` (verbatim). |
| **A2-1** overstated that a missed-call text is outside the Spam Act | A2 (L96) | Replaced the sentence `A text that just responds … not a marketing campaign.` with Legal's text, verbatim: "A text that only responds to someone's own call about their job is low risk: … consider ending with a short opt-out such as "Reply STOP to opt out"." Then, for flow, the next sentence's opening `But the ACMA warns` became `The ACMA also warns`. The quote and citation are unchanged. |

The built pages contain no occurrences of "compliant", "ABN or contact details" or "a reply, not a marketing campaign". All the new strings are present.

## LOW fixes (also applied)

| Fix | How it was applied |
|---|---|
| **A1-2** "legal business name" | Replaced with Legal's text verbatim: "The ACMA says to use the correct legal name of your business, or your name and ABN. If you trade under a registered business name, including your ABN is the simple way to cover this". |
| **A1-3** CTA service name | Replaced with: `AUTOMAIT also offers a one-off Review engine setup from $149, with a fixed written quote before you commit.` |
| **A1-4 / A2-4** internal notes and draft status | The `<!-- LEGAL REVIEW NOTES … -->` blocks were stripped; the build asserts exactly one per draft. `status` is set to published, and front matter is not rendered. All 3 pages contain 0 `<!--` comments. CSS `/* */` comments copied from the site `<style>` block were also stripped. |
| **A2-2** Samsung menu name unsourced (optional) | Applied Legal's optional replacement: "…usually in the Phone app's settings; check your phone maker's help pages for the exact name." |

## Not applied (kit-only, outside this task; the kit was not edited)

- **K1 (preferred fix):** add ABN and phone to kit templates 4A/4B/4C and rebuild the PDF/DOCX. Once that is done, the CTA wording can revert.
- **A2-3:** mark the kit 2A booking link as `(Optional)`.
- **K2:** update the kit's §4 menu path to Read reviews > Get more reviews > Copy.
- **K3:** remove `[job] in [suburb]` from the 4D positive reply.
- **Flag for operator:** the live site's kit copy says "Google review request templates, done the compliant way". K1 applies to it equally until the kit is fixed.

## Other build notes

- Each post has:
  - a `<title>`, meta description and canonical `https://automait.au/blog/<slug>/`
  - an `← Back to AUTOMAIT home` link to `/`
  - the footer `AUTOMAIT · ABN 82 801 716 831 · Not registered for GST`, plus `hello@automait.au`, `/terms/` and `/privacy/`
  - a soft $29 kit CTA box linking `https://automait.au/#kit`, plus the article's own CTA
  - BlogPosting JSON-LD (author/publisher: AUTOMAIT organisation)
- The site's `<style>` block and hidden `<svg>` sprite were copied from `/root/work/site/index.html`.
- A case-insensitive grep for the owner's surname across staging returns 0 hits.
- Nothing was deployed, pushed or emailed.
