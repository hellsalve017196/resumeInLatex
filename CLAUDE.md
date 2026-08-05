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

## ATS-scannability gate (blocking)

After any change to `resume.tex` and its rebuild, the generated `Ali_Abdullah_Khan_Resume.pdf`
**must be ATS (Applicant Tracking System) / recruiter scannable before you commit.** This is a
hard stop: if the PDF fails any check below, fix `resume.tex` and rebuild, and repeat until every
check passes. Do not commit or push a resume that fails.

Verify these on the rebuilt PDF:

```sh
# 1. Text is real, selectable text — not an image/scanned. Must print the resume prose.
pdftotext -layout Ali_Abdullah_Khan_Resume.pdf - | head -50

# 2. Reading order is linear and correct (top-to-bottom, no column scramble).
pdftotext Ali_Abdullah_Khan_Resume.pdf -   # scan the plain-text dump for sane order

# 3. Fonts are embedded (recruiters/parsers need embedded fonts, no Type3 bitmaps).
pdffonts Ali_Abdullah_Khan_Resume.pdf      # every font: emb=yes, no "Type 3"
```

Then confirm the parsed text meets ATS content rules:

- **All section headings survive extraction** — Professional Summary, Core Competencies,
  Professional Experience, Technical Skills, Certification, Education all appear as plain text.
- **Contact line is parseable** — phone, email, and LinkedIn/GitHub URLs come through as text
  (they already do via `\href`); email is a real `mailto:` link.
- **No content lives only in headers/footers, images, text boxes, tables-as-layout, or glyphs
  that don't map to Unicode.** Ligatures and special characters must extract as normal letters.
- **Single-column, linear layout** — the `\resumeSubheading` two-`minipage` rows must still
  extract with title and date in a sensible order, not interleaved gibberish.
- **Standard, machine-readable fonts and bullets** — keep the existing macros; don't swap in
  decorative symbols an ATS can't map.

If any check fails, adjust `resume.tex` (wording, macro usage, or character escaping — never by
converting text to an image) and rebuild until all pass. The deeper `resume-ats-optimizer` skill
is available for keyword-match and formatting audits when a fix isn't obvious.

## Commit & push after every change

Whenever you change `resume.tex` or `coverletter.tex`, the standing workflow is: **edit →
rebuild the PDF → verify one page → verify ATS-scannable (see gate above) → commit → push to
GitHub.** The ATS gate is blocking: never commit a resume PDF that fails it. Don't wait to be
asked to commit; pushing is part of "make the change." Stage the edited `.tex` and its regenerated
PDF, write a concise commit message describing the content change, and `git push` to the current
branch.

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
