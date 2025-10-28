# ADR-003: Constrain Child Class Maturity to Parent Class Maturity

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

GA4GH data models use inheritance (e.g., VRS Entity class inherited by Allele, Haplotype). Need rules for how maturity applies to inheritance hierarchies.

**The Problem:**
- Parent classes have shared properties inherited by children
- If child is Normative but parent is Draft, which properties are stable?
- Could a less mature child artificially appear stable through inheritance?

**Example:**
```
Entity (parent, Draft)
  ├─ id: string
  ├─ label: string
  └─ Allele (child, ???)
      └─ state: string
```

**Alternatives Considered:**

1. **Independent Maturity**
   - ✅ Maximum flexibility
   - ❌ Confusing stability (which properties are stable?)
   - ❌ Allele could be "Normative" but inherit unstable properties

2. **Child ≤ Parent** ✓
   - ✅ Clear: child can't exceed parent
   - ✅ Forces upstream stabilization first
   - ✅ No false stability signals
   - ✅ Allows extending mature parents with Draft properties

3. **Child = Parent**
   - ✅ Always consistent
   - ❌ Too restrictive (can't add new properties)
   - ❌ Prevents experimentation on mature classes

4. **Property-Level Only**
   - ✅ Very granular
   - ❌ Complex to track
   - ❌ Doesn't address inherited properties

---

## Decision

**Inheritance Maturity Rules:**
1. **Child classes ≤ parent class maturity**
   - Allele (child) cannot be Normative if Entity (parent) is Trial Use
2. **Properties ≤ containing class maturity**
   - Draft property cannot exist in Normative class

**Rationale:**
- Ensures attention to upstream classes first
- Prevents false stability signals
- Allows extending mature classes with new Draft properties

**Example:**
```
Entity (Normative)        ← Must be stable first
  ├─ id: string (Normative)
  ├─ label: string (Normative)
  └─ Allele (Trial Use)   ← Can be less mature
      ├─ state: string (Trial Use)
      └─ newProp: string (Draft)  ← Can add Draft props
```

---

## Consequences

### Positive

✅ Clear, enforceable rules  
✅ No false stability signals  
✅ Forces bottom-up stabilization (parent → child)  
✅ Still allows experimentation (new properties at lower maturity)  
✅ Implementers know exactly what's stable  

### Negative

❌ Can't stabilize child without stabilizing parent first  
❌ May slow advancement if parent isn't ready  
❌ Requires tracking entire inheritance tree  
❌ More complex validation rules  

### Risks & Mitigations

**Risk:** Parent class blocks child advancement
- **Mitigation:** Prioritize parent stabilization; may indicate parent needs work

**Risk:** Confusion about which properties are stable
- **Mitigation:** Annotate each property with maturity in JSON Schema

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#data-class-inheritance-and-property-maturity)
- **Example:** [GKS Common Library Entity class](https://github.com/ga4gh/gks-common/blob/1b7e52d6013c6785300aa933efa9210e2aafa57b/schema/gks.common-source.yaml#L7-L31)
- **Related ADR:** [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)

---

## Notes

This rule ensures that when an implementer sees "Normative", they can trust ALL inherited properties are also Normative. It prevents situations where a class appears stable but inherits unstable properties from a Draft parent.
