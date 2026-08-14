# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Single-page LaTeX resume for Hugo Prado. The main file is `hugoprado-resume.tex` which uses standard LaTeX packages (no custom cls files). Based on a fork of Sourabh Bajaj's resume template.

## Build

```sh
./build.sh          # runs: pdflatex hugoprado-resume.tex
```

Requires `pdflatex` installed locally. Output is `hugoprado-resume.pdf`. Build artifacts (`.aux`, `.log`, `.out`, etc.) are gitignored.

## Structure

- `hugoprado-resume.tex` — the canonical dev resume; contains custom commands for consistent formatting (`\resumeItem`, `\resumeSubheading`, `\resumeProjectHeading`, `\resumeSubItem`).
- `info/` — plain-text reference files with full profile details, technical skills, and coursework. Used as source material when updating the `.tex` file, not compiled. Keep these in sync — they are the canonical source of truth for full details.
- `tailored-resumes/` — local-only archive (gitignored) of tailored resume variants that have been submitted to specific job applications. Contains `.tex` + `.pdf` pairs only.
- `assets/` — preview image of the resume.

## Key Conventions

- Resume must remain **single-page, one-column**. All content fits on one letter-sized page.
- ATS parsability is enabled via `\pdfgentounicode=1` and `glyphtounicode`.
- Sections on the main resume, in order: Heading, About Me, Experience, Projects, Technical Skills, Education, Relevant Coursework.
- The main `.tex` is the *dev* resume: non-technical roles (food service, tutoring) live in `info/` and in tailored variants only, never here.
- Every URL printed on the resume must return 200 before the PDF is sent anywhere.
- When updating resume content, keep `info/` text files in sync as the canonical source of truth.

## Tailored Resumes (Per-Application Workflow)

When writing a tailored resume for a specific job:

1. Draft the variant in the repo root as `hugoprado-<slug>.tex` (e.g., `hugoprado-vlrc.tex` for Vision Loss Rehabilitation Canada).
2. Compile with `pdflatex` locally. The one-page rule still applies.
3. After the application is submitted, move the `.tex` + `.pdf` pair into `tailored-resumes/` and delete the build artifacts (`.aux`, `.log`, `.out`).
4. Do **not** add the tailored variant to `build.sh` — `build.sh` stays minimal and only compiles the main resume.
5. `tailored-resumes/` is gitignored; never commit its contents.
