---
name: codex-seo
description: Use Codex SEO to audit or improve a website. Routes to this plugin's technical, sitemap, schema, performance, content, and international SEO skills.
user-invocable: true
license: MIT
metadata:
  category: seo
---

# Codex SEO

Use the packaged SEO skills and scripts from this plugin. The upstream `/seo ...` examples describe
Claude Code workflows; in Codex, use the corresponding skill by name and the tools available in the
current session.

## Workflow

1. Identify the target URL or local project and the requested scope. If it is a local project, read
   its own SEO specification and current implementation before recommending changes.
2. For `quran.az`, load `seo-quran-az` first and follow its content and indexing rules.
3. Load only the relevant specialist instructions from `skills/seo-technical`, `skills/seo-schema`,
   `skills/seo-sitemap`, `skills/seo-hreflang`, or another matching skill. For a full audit, read
   `skills/seo-audit/SKILL.md` and adapt its steps to tools actually available in Codex.
4. Treat results as recommendations. Do not edit application files or deploy changes unless the user
   asks.

## Bundled scripts

When working from this source checkout, run tools through `./scripts/claude-seo run <script.py> ...`.
When the plugin is installed, use the runner from the installed plugin root. Resolve that root from
this skill's loaded file path when needed; do not assume Claude Code's `CLAUDE_PLUGIN_ROOT` variable
is expanded by Codex. Never invoke bundled Python scripts with a bare interpreter.

Do not run setup or connect optional APIs unless the user asks. Use optional integrations only when
they are already available and authorized. Do not dispatch Claude-specific subagents or rely on the
Claude Code hook; complete the workflow with Codex tools or run it sequentially.
