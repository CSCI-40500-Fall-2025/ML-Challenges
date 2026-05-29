# Challenges in Engineering Machine Learning (Software) Systems

Lecture slides for CSCI 40500 (Software Engineering), CUNY Hunter College, Fall 2025. Engineering challenges unique to ML systems: lack of modularity, concept drift, feedback loops, technical debt, and notebooks in production.

## Viewing

Open `ml_challenges.html` in any web browser. The deck uses [Slidy](https://www.w3.org/Talks/Tools/Slidy2/): advance with the arrow keys (or space), or by clicking; press `c` or the "Contents" button for the table of contents. The distributed `ml_challenges.html` is a single self-contained file (images inlined) and works fully offline.

## Building from Source

The slides are written in Pandoc Markdown (`ml_challenges.md`) and built with [Pandoc](https://pandoc.org) (version 2.11 or newer, which bundles the `slidy` writer, so no extra installs are needed):

```bash
make                  # build ml_challenges.html (references graphics/)
make self-contained   # single-file HTML with images inlined (for distribution)
```

See the `Makefile` for the exact Pandoc invocation and the other targets.

Source files:

- `ml_challenges.md`—the slide content (edit this)
- `header.html`—CSS and JavaScript injected into the document `<head>`
- `graphics/`—figures

The `make deploy` target is for the author's own web host and relies on an ssh alias (`compsci`) defined in `~/.ssh/config`; adopters can ignore it.
