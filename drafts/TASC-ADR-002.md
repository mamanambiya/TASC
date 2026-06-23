# TASC-ADR-002: Separate Citation Identifiers from Machine-Readable Standard Identifiers

**Date:** 2026-03-23 | **Status:** Proposed

**Deciders:** TASC, Technical Team, Architecture Community  
**Keywords:** identifiers, citation, interoperability, APIs, governance  
**Work Streams Impacted:** All  
**Products Affected:** DRS, TRS, WES, TES, Beacon, VRS and future standards

---

## Context

During discussions around standard citation, concerns were raised regarding the use of identifiers within APIs, schemas, registries, and machine-readable metadata

**The Problem:**
- Human citation and machine identification solve different problems
- A DOI is useful for publication and citation
- Software systems often require version-aware and machine-readable identifiers

**Alternatives Considered:**

1. **Use DOIs for all purposes**
   - ✅ Single identifier system
   - ❌ Poor fit for API and protocol interactions

2. **Allow each Work Stream to define its own identifiers**
   - ✅ Maximum flexibility
   - ❌ Inconsistent user experience
   - ❌ Reduced interoperability

3. **Separate citation and technical identification concerns**
   - ✅ Clear governance boundaries
   - ✅ Preserves future architectural flexibility
   - ✅ Supports multiple technical use cases

---

## Decision

GA4GH will use DOIs for documentary citation only. Future machine-readable identifier schemes MAY be developed independently where required for APIs, service registries, metadata models, and protocol implementations

**Key Points:**
- A DOI MUST NOT be considered the sole identifier mechanism for all standards-related use cases
- Citation requirements and interoperability requirements SHOULD be governed separately
- Future identifier frameworks MAY complement DOI-based citation

---

## Consequences

### Positive

- ✅ Avoids overloading DOI semantics
- ✅ Enables future architectural evolution
- ✅ Better alignment with software interoperability requirements

### Negative

- ❌ Multiple identifier systems may coexist
- ❌ Additional governance may be required

### Risks & Mitigations

**Risk:** Users become confused by multiple identifiers
- **Mitigation:** Clearly document the purpose and scope of each identifier type

---

## References

- **Full Policy:** [Citing GA4GH Standards Recommendation](../drafts/Citing%20GA4GH%20Standards.md)

---

## Notes

This ADR intentionally leaves open the possibility of future GA4GH identifier frameworks for machine-readable use cases.