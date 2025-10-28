# ADR-001: Adopt Four-Level Maturity Model for GA4GH Technical Specifications

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

GA4GH develops data exchange standards for federated genomic data sharing. New technical specifications (like VRS) must be developed and iterated through community implementations.

**The Problem:**
- Standards need **stability** for initial community adoption
- Standards need to **evolve** with minimal disruption
- Adopters exist across entire Innovation Adoption Lifecycle (innovators → early adopters → majority → laggards)
- Without maturity communication, conservative adopters won't engage; early adopters waste effort on unstable features

**Alternatives Considered:**

1. **No Maturity Model**
   - ❌ All features appear equally stable
   - ❌ Conservative adopters wait indefinitely
   - ❌ No signal for safe vs experimental

2. **Binary (Experimental/Stable)**
   - ✅ Simple
   - ❌ No middle ground for testing
   - ❌ Doesn't show validation level

3. **Three-Level (Draft/Stable/Deprecated)**
   - ✅ Shows progression
   - ❌ Gap too large between Draft and Stable
   - ❌ No distinction between "testing" and "production"

4. **FHIR-style (5+ levels)**
   - ✅ Very granular
   - ❌ Too complex for GA4GH
   - ❌ Hard to define criteria

5. **Four-Level (Draft/Trial Use/Normative/Deprecated)** ✓
   - ✅ Clear progression
   - ✅ "Trial Use" provides testing middle ground
   - ✅ Proven in HL7 FHIR
   - ✅ Manageable complexity

---

## Decision

Adopt **four-level maturity model** for GA4GH technical specification features:

| Level | Description | Target Adopters | Stability |
|-------|-------------|-----------------|-----------|
| **Draft** | Requirements gathered, documented | Innovators only | Unstable, frequent changes |
| **Trial Use** | Community-reviewed, ready for testing | Early Adopters | Changes with consultation |
| **Normative** | Proven stable, long-term support | Majority | No breaking changes in major version |
| **Deprecated** | Being phased out | (Migration) | Removal in next version |

**Scope:** Data classes, properties, protocols (not docs/tests)

**Advancement:** Requires defined criteria, community ballot, decision-maker consensus

**Inheritance:** Child classes ≤ parent maturity; properties ≤ class maturity

---

## Consequences

### Positive

   - ✅ Serves entire adoption lifecycle (innovators can experiment, conservative can wait for Normative)
   - ✅ Explicit stability commitments per level 
   - ✅ Reduces wasted implementation effort
   - ✅ Enables continuous evolution without destabilizing mature components
   - ✅ Aligns with proven HL7 FHIR precedent

### Negative

   - ❌ Annotation overhead (JSON Schema maturity properties)
   - ❌ Advancement process complexity (ballots, tracking)
   - ❌ Slower progression to Normative status
   - ❌ Learning curve for community
   - ❌ More frequent version releases

### Risks & Mitigations

**Risk:** Features stall at Trial Use indefinitely
- **Mitigation:** 12-month maximum, must vote or close

**Risk:** Inconsistent annotations across specs
- **Mitigation:** TASC oversight, templates

**Risk:** Conservative adopters avoid Trial Use
- **Mitigation:** Clear stability commitment docs

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#feature-maturity-levels)
- **Examples:**
  - [VRS Allele maturity annotation](https://github.com/ga4gh/vrs/blob/454c5312e8e425eb170901c7520311f3ca7904e3/schema/vrs/json/Allele#L6)
  - [VA-Spec property-level maturity](https://github.com/ga4gh/va-spec/blob/4c14e9f7f033dce3b6701ecd0fccca415476fd76/schema/va-spec/profiles/caf/json/CohortAlleleFrequency#L142-L143)

---

## Notes

The "Trial Use" level is critical - it provides middle ground where features have community validation but aren't yet committed to long-term API stability. This reflects the Innovation Adoption Lifecycle model and different implementer risk tolerances.
