# Repository Guidelines

## Build & Lint Commands
- `npm install` installs the textlint toolchain used for content checks.
- `npm run lint` runs textlint over `**/*.{md,tex}` files (main quality gate).
- `npm run lint:fix` runs textlint with auto-fix enabled.
- To compile a document, run `latexmk` from within the project directory (e.g., `cd projects/abstract && latexmk`). The `.latexmkrc` files configure LuaLaTeX automatically; output goes to `out/`.

## Writing Your Paper

### Document entry point
Each project lives under `projects/<name>/`. Edit `projects/<name>/main.tex` to write your paper.

### Title metadata (abstract project)
Set the following commands in the preamble of `main.tex`:
```latex
\title{タイトル}
\studentid{2500000}       % 学籍番号
\majorfield{工学}          % 専攻
\authorname{工芸 太郎}     % 氏名
\advisor{教授}{工芸 花子}  % 指導教員の役職と氏名
```

### Bibliography
- Add entries to `references/main.bib` using the `authorYYYY` key convention (e.g., `smith2020`).
- Cite with `\cite{key}` and print the reference list with `\printreferences`.
- For Japanese-language entries, add `keywords = {ja}` so name delimiters switch to `，` automatically.
- The style is IEEE (biblatex + biber). Use `@article`, `@inproceedings`, etc.

### Figures and tables
- Place figures with `\includegraphics` inside a `figure` environment.
- Use descriptive labels with prefixes: `fig:` for figures, `tab:` for tables, `sec:` for sections.
- Reference with `\ref{fig:example}` or `\autoref{fig:example}`.

### Japanese writing conventions
- End sentences with a fullwidth full stop `．` (U+FF0E, not the ASCII period `.`).
- The textlint rule `ja-no-mixed-period` enforces this automatically.
- Use `\cite{a,b}` for multiple citations; they render as a single bracketed list `[1,2]`.

### Style files
- Shared settings (fonts, geometry, headings) are in `shared/style/jp-common.sty`. Avoid editing this unless the change applies to all projects.
- Project-specific overrides belong in `projects/<name>/style/`.

## Commit & Pull Request Guidelines
- Use Conventional Commits format: `type: summary` (e.g., `feat:`, `fix:`, `chore:`).
- Run `npm run lint` before submitting changes that touch prose or LaTeX text.
- Follow the organization-level contributing guide linked in `README.md`.
