# ADR-005: Annotate Maturity in JSON Schema

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

Maturity levels need to be communicated to implementers. The question is: how should maturity information be stored and distributed?

**The Problem:**
- Implementers need to know maturity level of data classes and properties
- Maturity must be machine-readable (for tooling, validation)
- Maturity must be human-readable (for documentation)
- Need single source of truth (avoid documentation drift)

**Alternatives Considered:**

1. **Documentation Only**
   - ✅ Simple, human-readable
   - ❌ Not machine-readable
   - ❌ Documentation can drift from spec
   - ❌ No tooling support

2. **Separate Metadata File**
   - ✅ Clean separation
   - ❌ Must keep in sync with schema
   - ❌ Not co-located with definitions

3. **JSON Schema Annotations** ✓
   - ✅ Machine-readable
   - ✅ Co-located with definitions (single source of truth)
   - ✅ Can generate docs from schema
   - ✅ Tooling can validate maturity rules

4. **Comments Only**
   - ✅ Simple
   - ❌ Not machine-readable
   - ❌ Comments ignored by parsers

---

## Decision

**Use JSON Schema `maturity` property** to annotate:
- Data classes (e.g., `Allele`)
- Data class properties (e.g., `Allele.state`)

**Format:**
```json
{
  "Allele": {
    "maturity": "trial use",
    "properties": {
      "state": {
        "maturity": "trial use"
      },
      "experimentalProp": {
        "maturity": "draft"
      }
    }
  }
}
```

**Requirements:**
- Primary documentation sites (e.g., vrs.ga4gh.org) display maturity
- Properties cannot exceed class maturity (enforced by validation)
- Child classes cannot exceed parent maturity (enforced by validation)

---

## Consequences

### Positive

✅ Machine-readable (tooling, validation)  
✅ Single source of truth (schema = docs)  
✅ Can auto-generate documentation  
✅ Co-located with definitions (reduces drift)  
✅ Validation tools can enforce maturity rules  
✅ Standard JSON Schema extension (not vendor-specific)  

### Negative

❌ Requires schema authoring tooling updates  
❌ Adds verbosity to schema files  
❌ Implementers must parse maturity property  
❌ Not a standard JSON Schema keyword (custom extension)  

### Risks & Mitigations

**Risk:** Inconsistent annotation across specs
- **Mitigation:** TASC provides templates, reviews all specs

**Risk:** Tooling doesn't understand custom property
- **Mitigation:** Provide reference parser, document clearly

**Risk:** Annotations fall out of date
- **Mitigation:** CI validation checks maturity consistency

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#communicating-maturity-level)
- **Examples:**
  - [VRS Allele class-level maturity](https://github.com/ga4gh/vrs/blob/454c5312e8e425eb170901c7520311f3ca7904e3/schema/vrs/json/Allele#L6)
  - [VA-Spec property-level maturity](https://github.com/ga4gh/va-spec/blob/4c14e9f7f033dce3b6701ecd0fccca415476fd76/schema/va-spec/profiles/caf/json/CohortAlleleFrequency#L142-L143)
- **Related ADRs:**
  - [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)
  - [ADR-003: Constrain Child Class Maturity](003-constrain-child-class-maturity.md)

---

## Notes

JSON Schema allows custom properties for metadata. The `maturity` property serves as both human documentation and machine-readable metadata. Documentation generators can extract and display maturity badges. Validation tools can enforce inheritance rules.
