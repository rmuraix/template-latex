Review the LaTeX paper in this repository for academic quality. Follow the steps below systematically and report all findings with specific file locations and suggested corrections.

## 1. Grammar and Writing Style

- Check for grammatical errors, awkward phrasing, and unclear sentences.
- Verify that verb tenses are consistent throughout each section (past tense for methods/results, present tense for general facts).
- Confirm that sentence-level clarity is maintained — no run-on sentences or overly complex constructions.

## 2. Paper Structure

Verify that the paper contains the necessary sections for its type (e.g., conference abstract, technical report). Typical required sections:

- **Introduction** — background, motivation, research questions or objectives
- **Methods / Approach** — clear description of what was done
- **Results** — what was found or produced
- **Discussion / Analysis** — interpretation of results
- **Conclusion** — summary and future work
- **References** — properly formatted and cited

Flag any missing or misplaced sections.

## 3. Abbreviation and Terminology Consistency

- Identify every abbreviation used in the paper.
- Verify that each abbreviation is **defined in parentheses on its first occurrence** (e.g., "Natural Language Processing (NLP)").
- Flag any abbreviation that is used before its definition or is never defined.
- Check that the same term is used consistently throughout (e.g., not switching between "deep learning" and "DL" without prior definition).

## 4. Consistency of Claims

- Identify the main claims or contributions stated in the introduction/abstract.
- Verify that the results and conclusion sections actually support those claims.
- Flag any contradictions or unsupported assertions.
- Check that numerical values, percentages, and statistics cited in multiple places are consistent.

## 5. Citations and References

- Confirm that every `\cite{}` key corresponds to an entry in the `.bib` file.
- Flag any reference that is cited but missing from the bibliography, or listed in the bibliography but never cited.
- Check that reference formatting is consistent.

## 6. Figures and Tables

- Verify that every `\label{fig:…}` or `\label{tab:…}` is referenced in the text with `\ref{}`.
- Flag any figure or table that is defined but not referenced, or referenced but not defined.
- Confirm that captions are descriptive and end with the appropriate punctuation mark (`．` for Japanese text).

## 7. Japanese-Specific Conventions (if applicable)

- Confirm that full-width period `．` (U+FF0E) is used as the sentence-ending punctuation, not `。` or `.`.
- Confirm that full-width comma `，` (U+FF0C) is used where applicable.
- Check for inadvertent mixing of half-width and full-width characters in body text.

## Output Format

For each issue found, report:

1. **File and line number** (e.g., `projects/abstract/main.tex:23`)
2. **Issue type** (Grammar / Structure / Abbreviation / Consistency / Citation / Figure-Table / Convention)
3. **Description** of the problem
4. **Suggested correction**

After listing all issues, provide a brief **overall assessment** of the paper's readiness and the most critical items to address first.
