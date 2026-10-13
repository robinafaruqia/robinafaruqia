# AGENTS.md

Guidance for AI agents working in this repository.

## Repository overview

This is a **GitHub profile README** repository (`robinafaruqia/robinafaruqia`). It contains a single `README.md` that GitHub renders on the user's profile page. There is no application code, build system, package manager, database, or Docker setup.

## Cursor Cloud specific instructions

### What to expect

- **No services to start.** There is no dev server, API, or database in this repo.
- **No dependency installation.** There is no `package.json`, `requirements.txt`, or similar manifest.
- **No lint or test scripts.** Standard markdownlint rules flag expected GitHub-profile patterns (inline HTML, long lines, no H1 first line). Do not treat those as regressions unless the user asks to fix them.
- **End-to-end validation** for this repo means: validate `README.md` content, check external embed URLs where possible, and preview the rendered profile (locally or on GitHub).

### Previewing the README locally

To approximate how GitHub renders the profile README:

```bash
# Generate a standalone HTML preview (outside the repo)
python3 -c "
from pathlib import Path
readme = Path('README.md').read_text()
html = f'<!DOCTYPE html><html><head><meta charset=\"utf-8\"><title>README Preview</title><style>body{{background:#0d1117;color:#c9d1d9;font-family:system-ui;max-width:900px;margin:auto;padding:2rem}}table,th,td{{border:1px solid #30363d}}th,td{{padding:.5rem}}</style></head><body>{readme}</body></html>'
Path('/tmp/readme-preview/index.html').write_text(html)
print('Wrote /tmp/readme-preview/index.html')
"
mkdir -p /tmp/readme-preview
cd /tmp/readme-preview && python3 -m http.server 8765
```

Open http://localhost:8765/ in a browser. External widgets (capsule-render, readme-stats, shields.io, etc.) load from third-party hosts and may occasionally return transient errors (e.g. 503) or block bots (e.g. LinkedIn HTTP 999).

### Git workflow

- The only tracked content file is `README.md`.
- Changes are validated by viewing the rendered profile on GitHub after push, or via local HTML preview as above.
- Use `gh repo view` to confirm repository metadata and connectivity.

### External dependencies (not in repo)

| Resource | Purpose |
| :--- | :--- |
| GitHub | Hosts and renders the profile README |
| capsule-render.vercel.app | Header/footer wave graphics |
| readme-typing-svg.demolab.com | Animated typing headline |
| github-readme-stats.vercel.app | Contribution and language stats |
| github-readme-streak-stats.herokuapp.com | Contribution streak widget |
| img.shields.io | Technology and social badges |
| komarev.com | Profile view counter |
