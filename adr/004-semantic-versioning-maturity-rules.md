# ADR-004: Semantic Versioning with Maturity-Based Rules

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

GA4GH specs need versioning that communicates stability while supporting continuous evolution. Need to integrate maturity model with semantic versioning.

**The Problem:**
- Standard SemVer doesn't account for feature maturity
- Breaking change to Draft feature shouldn't trigger major version
- Breaking change to Normative feature MUST trigger major version
- Implementers need version numbers to signal API stability

**Alternatives Considered:**

1. **Standard SemVer (no maturity consideration)**
   - ✅ Simple, well-known
   - ❌ Major version bump for any breaking change (including Draft)
   - ❌ Doesn't communicate maturity

2. **Date-Based Versioning**
   - ✅ Clear chronology
   - ❌ No stability signal
   - ❌ Doesn't align with SemVer ecosystem

3. **Maturity-Aware SemVer** ✓
   - ✅ Major = breaking Normative changes
   - ✅ Minor = breaking Trial Use, new Trial Use/Normative features
   - ✅ Patch = Draft changes, non-breaking
   - ✅ Preserves SemVer familiarity

4. **Independent Feature Versioning**
   - ✅ Very granular
   - ❌ Too complex (version explosion)
   - ❌ Implementers can't track

---

## Decision

Use **Semantic Versioning 2.0** with maturity-based rules:

### **Major Version (X.0.0)**
- Breaking changes to **Normative** features
- Breaking changes to Normative property names
- Breaking changes to Normative definitions
- Breaking changes to Normative digests
- Addition of required fields to Normative classes

### **Minor Version (X.Y.0)**
- Breaking changes to **Trial Use** features
- New **Trial Use or Normative** features
- Addition of optional fields (Trial Use/Normative)
- Breaking changes to Trial Use property names/definitions

### **Patch Version (X.Y.Z)**
- New **Draft** features
- Any changes to **Draft** features
- Implementation guidance, tests, docs
- Non-breaking additions

**Commitment:** Normative features have long-term API stability (no breaking changes within major version).

---

## Consequences

### Positive

✅ Version numbers signal stability level  
✅ Normative features protected by major version  
✅ Draft features can iterate without major version churn  
✅ Aligns with SemVer ecosystem (tooling, expectations)  
✅ Clear upgrade path for implementers  

### Negative

❌ More frequent minor releases (Trial Use advancements)  
❌ Complex version decision logic  
❌ Must track maturity to determine version bump  
❌ Potential confusion (why is X breaking change minor?)  

### Risks & Mitigations

**Risk:** Confusion about why certain breaking changes are minor
- **Mitigation:** Document clearly, include maturity in release notes

**Risk:** Too many minor versions
- **Mitigation:** Batch Trial Use advancements

**Risk:** SemVer tools don't understand maturity context
- **Mitigation:** Release notes explain rationale

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#versioning)
- **SemVer 2.0:** [semver.org](https://semver.org)
- **Related ADRs:**
  - [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)
  - [ADR-007: Pre-releases](007-allow-prerelease-continuous-development.md)

---

## Notes

This versioning strategy reflects our maturity commitments: Normative = stable (major version protection), Trial Use = testing (minor version), Draft = experimental (patch version). It allows continuous evolution without penalizing early adopters with constant major version churn.
