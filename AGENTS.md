# xchainger-trade-pages Agent Guide

Public GitHub Pages **deploy-artifact** repo: only the already-built static files
(`public_site/`) plus the Pages deploy workflow. Source of truth is the private
builder repo `arsiktech/xchainger-trade-site` — read its `AGENTS.md` before any
work that touches content, QA, or deploys.

## Boundaries (owner directive, 2026-09-24)

- Never hand-edit `public_site/` from other repos' work; files arrive only through
  trade-site's own publish flow.
- Deploys trigger automatically on push to `main` — PRs and branches trigger
  nothing hosted (the workflow fires on `push: [main]` and `workflow_dispatch`
  only). Do not push to `main` without explicit owner approval.

## Test signal policy (owner directive, 2026-09-24)

- This repo contains no tests and must not gain any. Behavioral verification of
  this site lives end to end in trade-site: `npm run qa:e2e` there builds, boots
  preview, and runs the three Playwright journeys, ending in the durable,
  repeatable artifacts under `qa-artifacts/` that prove a deployed shape.
- Never write unit tests after writing code. If a check seems needed for these
  artifacts, first write down every way the artifact could be wrong, then prove
  it through the trade-site E2E journeys or the live deploy — not a new test file
  here.
