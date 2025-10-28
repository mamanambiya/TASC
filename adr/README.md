# TASC Architectural Decision Records

This directory contains Architectural Decision Records (ADRs) documenting key technical decisions made by the GA4GH Technical Alignment Sub-Committee (TASC).

## About TASC ADRs

TASC ADRs capture significant architectural and process decisions that affect GA4GH technical specifications. Each ADR documents:

- **What** decision TASC made
- **Why** it was made (context and alternatives considered)
- **When** it was made (date and approval status)
- **Consequences** of the decision (trade-offs, risks, and benefits)

ADRs are **immutable** historical records. Once accepted, they are never edited. If a decision changes, a new ADR supersedes the original.

## ADR Index

| ADR | Title | Status | Date |
|-----|-------|--------|------|
| [001](001-adopt-four-level-maturity-model.md) | Adopt Four-Level Maturity Model | Accepted | 2025-07-18 |
| [002](002-require-two-implementations-trial-use.md) | Require Two Implementations for Trial Use | Accepted | 2025-07-18 |
| [003](003-constrain-child-class-maturity.md) | Constrain Child Class Maturity to Parent | Accepted | 2025-07-18 |
| [004](004-semantic-versioning-maturity-rules.md) | Semantic Versioning with Maturity Rules | Accepted | 2025-07-18 |
| [005](005-annotate-maturity-json-schema.md) | Annotate Maturity in JSON Schema | Accepted | 2025-07-18 |
| [006](006-community-ballot-advancement.md) | Community Ballot for Maturity Advancement | Accepted | 2025-07-18 |
| [007](007-allow-prerelease-continuous-development.md) | Allow Pre-releases for Continuous Development | Accepted | 2025-07-18 |

## Process for Creating ADRs

1. Copy [template.md](template.md)
2. Assign next ADR number
3. Fill in all sections
4. Submit for review via pull request
5. Update this index when accepted

## Related Documentation

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md)
- **Governance:** [TASC Governance and Leadership](../governance/TASC_Governance_and_Leadership_Approved_240825.md)

## ADR Format

ADRs follow the **Michael Nygard template**:
- Title with ADR number
- Status (Proposed | Accepted | Deprecated | Superseded)
- Context (problem and alternatives)
- Decision (what was chosen)
- Consequences (trade-offs and risks)

ADRs should be **concise** (1-2 pages) and **focused** on a single decision.
