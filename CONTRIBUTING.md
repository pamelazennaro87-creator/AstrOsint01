# Contributing to AstrOsint01

This repository contains the research, website and (as it is integrated) the interactive software for the NASA Space Apps Challenge project.

## Team workflow
1. Create a branch for your change; avoid editing `main` directly when work is substantial.
2. Keep research claims linked to primary or peer-reviewed sources.
3. Label observations, interpretations, hypotheses and unknowns separately.
4. Do not add credentials, API keys, private personal data or unpublished sensitive material.
5. Open a pull request with a short summary, files changed and evidence for any new factual claim.
6. Check mobile layout, keyboard navigation, reduced-motion behaviour and text alternatives before proposing website changes.

## Website
The public website is served from the repository root through GitHub Pages. Changes pushed to `main` trigger the deployment workflow in `.github/workflows/deploy-astrosint-pages.yml`.

## Accessibility
No flashing or strobing effects. Respect `prefers-reduced-motion`. Every chart/map must have a text alternative and an accessible data table. Do not rely on colour alone.
