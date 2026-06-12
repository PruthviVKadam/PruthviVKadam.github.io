# Portfolio Hub — CLAUDE.md
Static portfolio site on GitHub Pages (repo: PruthviVKadam.github.io, served at https://pruthvivkadam.github.io). No frameworks, no build step — plain HTML/CSS (+minimal JS).

## Commands
- Preview: open index.html in browser (or `python -m http.server 8000`)
- Deploy: push to main → Pages auto-publishes in ~2 min

## Structure
- index.html (single page: header, project cards grid, footer)
- styles.css · assets/ (resume PDF, project GIFs ≤3MB each)

## Rules
- Every project card needs: live-demo URL, repo URL, 3-line problem→approach→result, stack badges.
- Mobile-first; test at 375px width. No heavy JS libs — Lighthouse score stays >90.
- Never edit project metrics here by hand — copy them verbatim from each project's README.
- Keep personal data limited to: name, email, LinkedIn, GitHub. No phone/address on the public site.
