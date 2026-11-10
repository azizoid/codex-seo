---
name: seo-quran-az
description: Apply Quran.az-specific SEO rules when auditing the live site or its source. Use for technical SEO, schema, sitemap, and language-indexing reviews.
user-invocable: true
argument-hint: "[audit|technical|schema|sitemap|hreflang] [URL]"
license: MIT
metadata:
  category: seo
---

# Quran.az SEO profile

Use this profile to constrain the generic SEO workflows in this repository when the target is
Quran.az. Treat the live site and local source as separate evidence: the site shows what is deployed;
the code and specification show the intended policy. Report disagreements between them.

## Before auditing

1. Find the quran.az project root. It contains `specs/5-frontend/5.07-SEO.md` and
   `src/helpers/seo.ts` (when the app is the current directory), or those files are under
   `quran.az/` when the workspace root contains multiple projects.
2. Read the SEO specification, then inspect the current helper, route metadata, sitemap resource,
   and `public/robots.txt`. Do not assume this profile is newer than the project specification.
3. For a source audit, inspect current code. For a live audit, use `https://quran.az` unless the user
   names another deployment.

## Quran.az indexing policy

- The canonical origin is `https://quran.az`.
- The indexable reading paths are `/`, valid `/:soorah`, and valid `/:soorah/:ayah` paths.
- Reading URLs with query parameters, including translator selection, stay `noindex,follow` and
  canonicalize to the clean path. Search and analytics pages are also `noindex,follow`.
- The sitemap contains only the home page and valid surah and ayah paths. It has no query strings
  or fabricated `lastmod` values.
- Structured data is limited to visible, maintained `WebSite`, `WebPage`, and `BreadcrumbList`
  information. Do not recommend fabricated FAQs, authors, dates, reviews, ratings, or attribution.
- Azerbaijani is primary and Russian is secondary. Russian translator variants currently use query
  parameters and are non-indexable; do not recommend hreflang tags for those variants. Flag any
  proposed language-indexing change for a human product decision.
- Preserve Quran text, translations, and religious content. Never rewrite or generate them for
  search ranking.

If the current specification or code differs from these rules, describe the exact conflict and
follow the specification's stated policy when making recommendations.

## Audit workflow

- Prefer focused technical, schema, sitemap, or language audits. A generic full audit can return
  irrelevant local-business, ecommerce, or content-generation recommendations.
- Treat every finding as a proposal. Do not edit or deploy quran.az changes unless the user asks.
- Do not access Search Console, GA4, or other credentialed services unless the user asks for that
  data. Keep any credentials outside the application repository.
- In Codex, use the relevant skill instructions and bundled `scripts/claude-seo` runner. Treat
  Claude Code slash-command examples as workflow names if Codex does not expose those commands.

## Report

For each finding, include the affected URL, evidence, relevant source or specification, severity,
confidence, and a concrete recommendation. Separate verified issues from tool heuristics and mark
false positives caused by Quran.az's canonical, translator, or content policies.
