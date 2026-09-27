# CCSO Constitution

This repository tracks changes to the constitution of Penn State's Competitive Cyber Security Organization (CCSO).

The constitution is maintained as a LaTeX document (`CCSO_Constitution.tex`), formatted to match the official Penn State Office of Student Activities constitution template so it satisfies OrgCentral submission requirements.

## Amending the Constitution

Changes to the constitution can be proposed through a pull request and must be voted on as outlined within the constitution. Voting results should be appended to a pull request before merging.

## Editing the Constitution (LaTeX)

The source of truth is `CCSO_Constitution.tex`. Do not reintroduce a markdown copy — edit the `.tex` file directly and keep it in sync with the compiled PDF.

### Prerequisites

Install a LaTeX distribution with `pdflatex`. On Debian/Ubuntu:

```bash
sudo apt-get update
sudo apt-get install -y texlive-latex-base texlive-latex-recommended texlive-latex-extra
```

### Building the PDF locally

```bash
pdflatex -interaction=nonstopmode CCSO_Constitution.tex
pdflatex -interaction=nonstopmode CCSO_Constitution.tex
```

Run it twice so section references resolve correctly. This produces `CCSO_Constitution.pdf` in the repo root.

### Editing tips

- Each Article maps to a `\section*{Article N -- ...}` block. Keep article numbering and ordering consistent with the PSU template (Name/Affiliation, Mission, Membership, Officers, Operating Procedure, Advisors, Financial Statement, Enabling Clause).
- Officer/chair duties use nested `itemize`/`enumerate` lists — match the existing list style when adding new roles so formatting stays consistent.
- Required PSU compliance language (Non-Hazing Compliance Statement, Non-Discrimination Statement, co-President/co-Treasurer restriction, Enabling Clause) must remain present verbatim; OrgCentral submissions are rejected without them.
- The Enabling Clause ratification date is a blank line (`\underline{\hspace{4cm}}`) — fill it in with the actual date before submitting to OrgCentral, then revert to blank (or update) after the next ratification.
- Clean up build artifacts before committing (`*.aux`, `*.log`, `*.out` — already covered by `.gitignore`).

### CI

Pushing changes to `CCSO_Constitution.tex` triggers `.github/workflows/pdf-publish.yaml`, which builds the PDF with `pdflatex` and cuts a dated GitHub release with the compiled PDF attached.

## License

[MIT](https://choosealicense.com/licenses/mit/)
