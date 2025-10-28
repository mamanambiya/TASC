# ADR-002: Require Two Implementations for Trial Use Advancement

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

Draft features need validation before wider community adoption. The question is: how much validation is enough to advance to Trial Use?

**The Problem:**
- Need evidence that Draft features work before promoting to Trial Use
- Want diverse perspectives (avoid single-vendor lock-in)
- Must balance validation rigor vs speed of adoption
- Need to ensure open-source availability

**Alternatives Considered:**

1. **One Implementation**
   - ✅ Faster advancement
   - ❌ No evidence of interoperability
   - ❌ Single vendor perspective

2. **Three+ Implementations**
   - ✅ Strong validation
   - ❌ Too slow for Trial Use (this is Normative criteria)
   - ❌ May never reach threshold

3. **Two Implementations (1 open)** ✓
   - ✅ Evidence of interoperability
   - ✅ Multiple perspectives
   - ✅ Open source ensures transparency
   - ✅ Reasonable bar for Trial Use

4. **No Requirement**
   - ❌ No validation before testing
   - ❌ Wastes community effort

---

## Decision

**Draft → Trial Use requires:**
- Minimum **2 independent implementations**
- At least **1 must be open source**
- Implementers must **commit to supporting** the feature once advanced

**Rationale:**
- Two implementations prove basic interoperability
- Open source requirement ensures transparency and community access
- Aligns with GA4GH Product Development 14.8.3 (implementations requirement)

---

## Consequences

### Positive

✅ Validates features work before wider testing  
✅ Ensures interoperability between independent implementations  
✅ Open source requirement prevents vendor lock-in  
✅ Reasonable bar (not too high/low)  
✅ Builds early adopter community  

### Negative

❌ Slows advancement (must find 2 implementers)  
❌ Small work streams may struggle to find implementers  
❌ Requires tracking of implementers and commitments  
❌ Risk of "friendly" implementations (same team)  

### Risks & Mitigations

**Risk:** Can't find 2 implementers for niche features
- **Mitigation:** Feature may not warrant Trial Use; keep as Draft or close

**Risk:** "Paper implementations" (same team, different repos)
- **Mitigation:** Require "independent" implementers, review in ballot

**Risk:** Open source implementation is abandoned
- **Mitigation:** Maturity can be downgraded if support ends

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#advancing-from-draft-to-trial-use)
- **GA4GH Process:** [Product Development 14.8.3](https://www.ga4gh.org/our-products/development-and-approval-process/#section_5)
- **Related ADR:** [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)

---

## Notes

This requirement applies only to Draft → Trial Use. Normative requires additional implementations beyond these initial two, demonstrating broader interoperability. The "independent" requirement means different organizations, not just different repositories.
