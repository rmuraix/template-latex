Run textlint on the repository and fix all reported issues. Follow the steps below in order.

## Step 1 — Install dependencies (if needed)

If `node_modules/` does not exist yet, install the required packages first:

```bash
npm install
```

## Step 2 — Run textlint

Execute the linter against all Markdown and LaTeX source files:

```bash
npm run lint
```

This runs `textlint "**/*.{md,tex}"` using the rules defined in `.textlintrc.json`:

- **`preset-ja-technical-writing`** — Japanese technical writing conventions (sentence length, doubled particles, weak expressions, etc.)
- **`@textlint-ja/preset-ai-writing`** — additional quality rules for AI-assisted writing
- **`ja-no-mixed-period`** — enforces `．` (U+FF0E) as the sentence-ending punctuation mark

## Step 3 — Interpret the results

Each reported issue has the format:

```
path/to/file.tex:LINE:COL  error  <message>  rule-name
```

Common rules and how to fix them:

| Rule | Typical problem | Fix |
|------|----------------|-----|
| `ja-no-mixed-period` | Sentence ends with `。` or `.` instead of `．` | Replace with `．` |
| `ja-no-successive-word` | Same word used twice in a row | Rewrite the phrase |
| `ja-no-weak-phrase` | Vague expressions such as `〜と思います` | Rewrite more assertively |
| `ja-no-abusage` | Commonly misused expressions | Use the suggested alternative |
| `max-ten` | Too many `、` commas in one sentence | Split the sentence or reduce commas |
| `sentence-length` | Sentence exceeds the allowed character limit | Split into shorter sentences |
| `no-doubled-conjunction` | Consecutive sentences starting with the same conjunction | Rephrase one of the sentences |

## Step 4 — Apply auto-fixable corrections

For issues that textlint can fix automatically, run:

```bash
npm run lint:fix
```

This runs `textlint --fix "**/*.{md,tex}"` and rewrites files in place. Review the diff afterwards with `git diff` to confirm the changes are correct.

## Step 5 — Fix remaining issues manually

Re-run `npm run lint` to see which issues were not auto-fixed. For each remaining error:

1. Open the file at the indicated line number.
2. Read the rule description to understand the expected style.
3. Edit the text to satisfy the rule.
4. Re-run `npm run lint` to confirm the error is resolved.

## Step 6 — Suppressing false positives

If a flagged phrase is intentional (e.g., a proper noun, a quoted term), you can suppress the warning with an inline comment:

```latex
% textlint-disable rule-name
Some text that should not be linted.
% textlint-enable rule-name
```

Or add an entry to the `allowlist.allow` array in `.textlintrc.json` for globally allowed phrases.

## Step 7 — Verify a clean run

After all fixes, confirm that the linter exits with no errors:

```bash
npm run lint
```

The command should complete with exit code `0` and produce no output (or only a summary with 0 problems).
