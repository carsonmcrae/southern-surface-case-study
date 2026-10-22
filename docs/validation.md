# Validation scope

## What the evidence supports

- The application stack and component boundaries were reviewed in source and documentation on October 22, 2026.
- Architecture records support the candidate-first review boundary, source evolution, scheduler hardening, inbound inquiry distinction, and manual outreach model.
- The private repository contains unit, component, request-boundary, persistence, security, and browser tests using Vitest, Testing Library, and Playwright. Their presence is not a newly executed production test result.
- The owner reported 150 new leads and 5 jobs last month on October 22, 2026. The underlying business records, exact reporting dates, job attribution, and common cohort were not independently audited for this case study.
- The public website implements specific accessibility and SEO provisions described in the README. This does not establish complete WCAG conformance, ranking gains, or business impact from SEO.

No production coverage percentage, uptime percentage, ROI, revenue, time saved, or conversion rate is claimed.

## Executed showcase checks

The following checks were run against the portfolio release branch on October 22, 2026:

| Check | Result |
| --- | --- |
| `node --test southern-surface/demo/model.test.mjs` | 6 of 6 tests passed: ordered discovery, duplicate handling, human review, combined filtering and sorting, manual lead changes, and fresh-state reset |
| `node scripts/check-ssc.mjs` | Passed local link and anchor checks plus sensitive-content, network-operation, and storage scans |
| `git diff --check` | Passed whitespace checks for the portfolio changes |
| Standalone Markdown link check | All local document links resolved across the six Markdown files |
| Prototype browser interaction | Desktop and 390 × 844 mobile interaction, keyboard controls, reset during an active run, and the separate outcome walkthrough passed; no browser warnings or errors were logged |
| Portfolio browser interaction | Case-study and home pages had no horizontal overflow at 320 px and 390 px; Products-menu Escape focus handling and both themes passed |
| axe-core 4.13.0 | 13 scans reported zero automated violations: all four desktop prototype tabs in both themes, desktop case study in both themes, mobile candidate review in light mode, mobile verified leads in dark mode, and mobile case study in light mode |

These checks concern the fictional static showcase. They neither exercise SSC production nor validate the owner's business figures. Static scans support the separation review but do not replace browser interaction and network inspection.

Some automated prototype contrast checks were incomplete and remain subject to manual assessment. The case-study scans had no incomplete checks. Zero reported automated violations does not establish complete WCAG conformance or accessibility certification; WCAG 2.2 AA remains the target.

## Prototype release checks

The executable prototype is maintained in the portfolio repository rather than this documentation bundle. For future prototype changes, verify the following before deployment:

1. Discovery advances in the reviewed order, uses bounded fictional inputs, and does not approve or contact a lead automatically.
2. Duplicate input does not inflate the fictional candidate count, including when a simulation is repeated.
3. Search, filters, sorting, status changes, and reset operate on disposable state.
4. Controls support keyboard use, focus is visible, status updates are announced, and layouts work at mobile widths and in light and dark modes.
5. Browser inspection shows no production API, data, authentication, source collection, or outreach requests.
6. Local links resolve, public links point only to reviewed public destinations, and new portfolio destinations are checked after deployment.
7. Every staged file and new commit is reviewed for private source, personal data, secrets, privileged links, and infrastructure details.

Record concrete commands and actual results in the portfolio pull request. This maintenance checklist does not claim additional test results beyond those recorded above. Accessibility testing can identify defects but does not establish certification.

## Limits of the public artifact

The prototype demonstrates simplified, supported workflows with records invented for this project. Its counts describe its fixtures. They are unrelated to the owner's reported leads and jobs. It does not reproduce operational permissions, private interfaces, integrations, or business data.
