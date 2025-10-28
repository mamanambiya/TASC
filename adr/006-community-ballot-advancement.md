# ADR-006: Community Ballot for Maturity Advancement

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

Maturity advancement decisions need community input. The question is: how should these decisions be made?

**The Problem:**
- Features affect multiple implementers across organizations
- Need consensus, not just leadership decision
- Must balance rigor vs speed
- Need to document community support

**Alternatives Considered:**

1. **Leadership Decision Only**
   - ✅ Fast
   - ❌ No community input
   - ❌ Risk of advancing unsuitable features

2. **Unanimous Vote**
   - ✅ Strong consensus
   - ❌ One objection blocks (too slow)
   - ❌ May never reach consensus

3. **Simple Majority (51%)**
   - ✅ Fast decisions
   - ❌ Too low bar for significant decisions
   - ❌ Can ignore substantial objections

4. **70% Supermajority with 1-week ballot** ✓
   - ✅ High consensus (70% threshold)
   - ✅ Reasonable timeframe (1 week minimum)
   - ✅ Documented community support
   - ✅ Allows thoughtful review

5. **2-week Required Period**
   - ✅ More time for review
   - ❌ Slows all decisions
   - ❌ 1 week sufficient with flexibility

---

## Decision

**Use community ballot for maturity advancement:**

**Process:**
1. Create ballot release describing features under consideration
2. Survey all Product Implementers implementing the feature
3. Minimum **1-week review period** (extendable at product owner discretion)
4. Voting options: **Approve | Reject | Abstain**
5. **70% of eligible voters** must vote "approve" to advance

**Survey Contents:**
- Name of Product Implementer
- Implementation being referenced
- Which feature(s) suitable for advancement
- Comments (endorsement or gaps description)

**Decision-makers by maturity level:**
- **Draft → Trial Use:** Feature developers, product owners, implementers
- **Trial Use → Normative:** + Work Stream leads

**Fallback:** If multiple rounds fail, TASC Leadership + CPO decide

---

## Consequences

### Positive

✅ Community consensus (70% is high bar)  
✅ Documents community support  
✅ Ensures stakeholders weigh in  
✅ Allows objections to be heard  
✅ Reasonable timeframe (not too slow/fast)  
✅ Flexible (can extend if needed)  

### Negative

❌ Slows advancement (1+ week per ballot)  
❌ Requires tracking implementers and votes  
❌ Non-responsive voters slow process  
❌ 70% may be too high for small communities  
❌ Ballot overhead for each advancement  

### Risks & Mitigations

**Risk:** Low voter turnout blocks advancement
- **Mitigation:** Leadership can decide if 2 consecutive meetings not quorate

**Risk:** Voters don't read materials
- **Mitigation:** Clear expectation that members read memo before vote

**Risk:** Strategic voting (competitors block rivals)
- **Mitigation:** 70% threshold, abstain option, leadership review

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#advancing-from-draft-to-trial-use)
- **Governance:** [TASC Decision-Making Process](../governance/TASC_Governance_and_Leadership_Approved_240825.md#decision-making-process)
- **Related ADRs:**
  - [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)
  - [ADR-002: Two Implementations Required](002-require-two-implementations-trial-use.md)

---

## Notes

The 70% threshold matches TASC's general decision-making threshold. The 1-week minimum provides adequate review time while maintaining momentum. Product owners can extend for complex features. The ballot documents community readiness and avoids surprises.
