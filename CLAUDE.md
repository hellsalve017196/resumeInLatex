# resumeInLatex

Ali Abdullah Khan's resume and cover letter, maintained in LaTeX. This is the single source of
truth — the resume is only ever updated here, never by editing a PDF or a copy elsewhere.

## Files

- `resume.tex` → builds `Ali_Abdullah_Khan_Resume.pdf`
- `coverletter.tex` → builds `Ali_Abdullah_Khan_Cover_Letter.pdf`
- `roman_resume.jpg` — layout reference

## Build

Compiled with XeTeX (`xelatex`), not pdfLaTeX — `glyphtounicode` / `\pdfgentounicode` are
intentionally commented out in `resume.tex` because they are pdfLaTeX-only.

```sh
xelatex -interaction=nonstopmode -jobname=Ali_Abdullah_Khan_Resume resume.tex
xelatex -interaction=nonstopmode -jobname=Ali_Abdullah_Khan_Cover_Letter coverletter.tex
```

After any content change, rebuild and verify the resume is still **one page**:

```sh
mdls -name kMDItemNumberOfPages Ali_Abdullah_Khan_Resume.pdf
pdftotext -f 2 -l 2 Ali_Abdullah_Khan_Resume.pdf -   # should output nothing
```

To eyeball the rendered layout, rasterize to PNG in the scratchpad and read the image:

```sh
pdftoppm -png -r 100 Ali_Abdullah_Khan_Resume.pdf <scratchpad>/resume_check
```

## Commit & push after every change

Whenever you change `resume.tex` or `coverletter.tex`, the standing workflow is: **edit →
rebuild the PDF → verify one page → commit → push to GitHub.** Don't wait to be asked to commit;
pushing is part of "make the change." Stage the edited `.tex` and its regenerated PDF, write a
concise commit message describing the content change, and `git push` to the current branch.

Do **not** add a `Co-Authored-By: Claude` trailer to the commit (it surfaces a Claude icon on
GitHub).

## Editing conventions

- Use the existing macros (`\resumeItem`, `\resumeSubheading`, `\resumeOrganizationHeading`,
  `\resumeItemListStart/End`, `\resumeSubHeadingListStart/End`). Don't introduce new formatting
  commands or restructure the preamble to fit content — tighten wording instead.
- Fit content to one page by cutting or condensing bullets, not by shrinking margins or spacing.
- Escape LaTeX specials in prose: `&` → `\&`, `%` → `\%`, `|` → `\textbar{}`.
- Every claim must correspond to something that actually happened. Rewording and reframing are
  fine; inventing experience, metrics, or titles is not.

## Positioning

Target: **product engineer / whole-slice ownership** — broadening from lead front-end without
diluting that spike ("full-stack developer" is banned as a self-label). The imported file below
carries the market thesis, the resume audit, the editing rules — including the operated-reps bar
for backend claims — and pending edits awaiting Ali's confirmation. Read it before touching
`resume.tex` or `coverletter.tex`.

@.claude/resume-context.md
