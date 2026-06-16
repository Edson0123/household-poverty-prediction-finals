Poverty App — Data Flow Diagram

Files:
- [app/docs/dfd.mmd](app/docs/dfd.mmd)
- [app/docs/dfd.md](app/docs/dfd.md)

How to export the diagram to PNG or SVG

Option A — mermaid-cli (recommended):

```bash
npm install -g @mermaid-js/mermaid-cli
mmdc -i app/docs/dfd.mmd -o app/docs/dfd.png
mmdc -i app/docs/dfd.mmd -o app/docs/dfd.svg
```

Option B — VS Code (quick):
- Install a Mermaid preview extension (e.g. "Mermaid Preview" or "Markdown Preview Mermaid Support").
- Open `app/docs/dfd.md` and use the extension's export command to save PNG/SVG.

Option C — GitHub/GitLab Preview:
- Some renderers display Mermaid inside Markdown; view `dfd.md` in your editor or CI that supports Mermaid.

If you want, I can attempt to render and save a PNG here — allow me to install mermaid-cli or run a rendering step.