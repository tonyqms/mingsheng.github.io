### .github/copilot-instructions.md — repo-specific guidance for AI coding agents

Purpose
- Help AI contributors be immediately productive editing this repository: a small static site comprised of HTML pages in the repository root.

Big picture
- This repo is a static site: primary entry is [index.html](index.html). Blog posts are individual files named with the `blog-` prefix (e.g. [blog-kpis.html](blog-kpis.html)).
- There is no build system, package manifest, or test framework present — files are edited and committed directly.

Key files & patterns
- Root HTML pages: [index.html](index.html) and `blog-*.html` files. Edit these in-place; maintain existing relative links between pages.
- Landing / documentation: [README.md](README.md) contains repository description and should be updated when changing site structure or navigation.

Developer workflows (how to preview and validate changes)
- Quick local preview: open `index.html` in a browser or run a local HTTP server:
```bash
python3 -m http.server 8000
# then visit http://localhost:8000/index.html
```
- Recommended in-editor preview: VS Code Live Server extension for iterative HTML edits.
- Commit workflow: standard Git flow — `git add`, `git commit -m "..."`, `git push`.

Editing conventions for agents
- Make minimal, focused changes: update the few HTML files required for the task instead of large-format refactors.
- Preserve DOCTYPE, `<head>` metadata, and existing CSS/JS references unless the change explicitly requires them.
- Use relative links for cross-page references (follow the pattern used by existing blog files).
- If adding files or assets, place them in the repo root or a new top-level folder and update links in the referencing HTML files and the [README.md](README.md).

Project-specific caveats
- No JavaScript build step or dependency manager was detected — do not add a package.json or introduce build tooling without coordinating with maintainers.
- There are no automated tests or CI configuration files in the repository. If adding CI, include clear documentation and a lightweight config (e.g., GitHub Actions) and describe the intent in the README.

What to change in PRs
- Title: concise, e.g., "Update blog-kpis post content" or "Fix relative link in index.html".
- Description: list files changed and the reason. If site navigation is altered, update [README.md](README.md).
- Keep diffs focused (one conceptual change per PR).

Examples (how to implement common edits)
- Edit a post content: update only the corresponding `blog-*.html` file and preview locally.
- Add a new post: create a new `blog-<slug>.html`, follow existing markup patterns from other `blog-*.html` files, and add a link from `index.html` if appropriate.

When in doubt
- Ask for clarification about deployment or site hosting before changing conventions or adding CI/build tooling.

Please review: does any section need more detail (preview commands, examples, or references to other files)?
