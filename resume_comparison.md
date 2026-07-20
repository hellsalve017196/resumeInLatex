# Resume Comparison: `resume.tex` vs `roman_resume.jpg`

**Date:** 2026-07-20

`resume.tex` is the current LaTeX source (builds `resume.pdf`). `roman_resume.jpg` is a screenshot of a different, more ATS-styled rendering of essentially the same resume — likely output from a resume service or template — with meaningfully different content choices.

---

## Things the JPG has that the .tex doesn't

- **Title line** under the name: *"Software Engineering Leader | React & TypeScript | Consumer Payment Platforms"*, plus a matching footer (*"Ali Abdullah Khan | Software Engineering Leader"*).
- **Core Competencies section** — a keyword strip that helps ATS keyword matching:
  > Engineering Leadership | Front-End Architecture | React | TypeScript | JavaScript (ES6+) | Node.js | Consumer Payments | REST APIs | Accessibility (WCAG/ADA) | Agile/Scrum | Stakeholder Management | CI/CD | Testing | Mentoring
- **Extra bullets:**
  - VP role: analytics/product collaboration bullet ("Partner with product, design, analytics, and engineering stakeholders…").
  - Associate role: "Supported production releases and issue resolution in a highly regulated financial-services environment…"
  - Charter: Agile collaboration bullet ("Collaborated with cross-functional teams throughout design, development, testing, and deployment…").
- **Skills additions:** BlueJS listed under Frameworks & Libraries; "analytics instrumentation" under Cloud, Tools & Practices.
- **Education year:** graduation year **2016** is included.
- **Formal company name:** "JPMorgan Chase & Co." (the .tex says "JP Morgan Chase").
- **Certification formatting:** "AWS Certified Cloud Practitioner – Amazon Web Services, Sep 2023" (cleaner attribution).

## Things the .tex has that the JPG dropped

- The **AI-driven SDLC workflow** bullet (GitHub Copilot + Obsidian knowledge base, JIRA intake, PRD generation, task decomposition) — one of the two most distinctive VP achievements.
- The **AI-assisted test automation** bullet (unit, component, and E2E suite generation).
- The **internal CLI tools** bullet (production CDN artifact publishing, feature flag management).
- **Holbrook, NY** location (JPG says "New York, NY").
- The **"U.S. Citizen — no sponsorship required"** line.
- **Raw URLs** for LinkedIn, GitHub, and portfolio (the JPG uses bare labels "LinkedIn | GitHub | Portfolio" — worse for printed/ATS-parsed copies).

## Tone differences

- The JPG softens several bullets into more generic "delivery/coordination" language (e.g., "Own end-to-end execution across roadmap planning, sprint delivery…" vs the .tex's more concrete "Served as project coordinator — drove end-to-end planning, sprint execution…").
- The JPG summary is prose-style and does not name JPMorgan Chase; the .tex summary does.

## Defect in the JPG

- "New York, NY" is rendered **twice** above the second JPMorgan entry — a layout glitch worth not replicating.

---

## Suggested merge direction

Take the good parts of the roman version into `resume.tex` without losing the distinctive content:

1. Add the title line under the name.
2. Add a Core Competencies keyword section.
3. Rename to "JPMorgan Chase & Co."
4. Add graduation year (2016) to Education.
5. Pull in the extra bullets (regulated-environment, stakeholder collaboration, Agile delivery) where they add substance.
6. Add BlueJS and analytics instrumentation to Skills.
7. **Keep** the AI-workflow, test-automation, and CLI-tooling bullets, the citizenship line, and the raw URLs.
