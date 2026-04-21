# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Single-page LaTeX resume for Hugo Prado. The main file is `hugoprado.tex` which uses standard LaTeX packages (no custom cls files). Based on a fork of Sourabh Bajaj's resume template.

## Build

```sh
./build.sh          # runs: pdflatex hugoprado.tex
```

Requires `pdflatex` installed locally. Output is `hugoprado.pdf`. Build artifacts (`.aux`, `.log`, `.out`, etc.) are gitignored.

## Structure

- `hugoprado.tex` — the resume source; contains custom commands for consistent formatting (`\resumeItem`, `\resumeSubheading`, `\resumeProjectHeading`, `\resumeSubItem`)
- `info/` — plain-text reference files with full profile details, technical skills, and coursework (used as source material when updating the tex file, not compiled)
- `assets/` — preview image of the resume

## Key Conventions

- Resume must remain **single-page, one-column**. All content fits on one letter-sized page.
- The custom color `myblue` (RGB 25,25,112) is used for the heading.
- ATS parsability is enabled via `\pdfgentounicode=1` and `glyphtounicode`.
- Sections: Heading, About Me, Education, Projects, Technical Skills, Experience, Relevant Coursework.
- When updating resume content, keep `info/` text files in sync as the canonical source of truth for full details.
