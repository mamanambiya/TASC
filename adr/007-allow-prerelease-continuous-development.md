# ADR-007: Allow Pre-releases for Continuous Development

**Date:** 2025-07-18 | **Status:** Accepted

**Deciders:** TASC Leadership, CPO, Work Stream Representatives

---

## Context

GA4GH specs need continuous development between formal releases. The question is: how to support iterative work without formal release overhead?

**The Problem:**
- Implementers need stable snapshots for testing
- Formal releases require ballots, documentation, approvals (slow)
- Draft features evolve rapidly
- Need way to share work-in-progress
- Want to reference specific snapshots in GitHub issues

**Alternatives Considered:**

1. **Release Only (no pre-releases)**
   - ✅ Clear versioning
   - ❌ Slow iteration
   - ❌ Hard to reference WIP
   - ❌ No testing snapshots

2. **Nightly Builds**
   - ✅ Always current
   - ❌ Unstable (build-to-build churn)
   - ❌ Not SemVer compliant
   - ❌ Hard to track which build has what

3. **Feature Branches Only**
   - ✅ Isolates work
   - ❌ No numbered releases
   - ❌ Hard to reference
   - ❌ Doesn't work with package managers

4. **SemVer Pre-releases** ✓
   - ✅ SemVer compliant (1.2.0-alpha.1)
   - ✅ Stable snapshots
   - ✅ Can reference in issues
   - ✅ Works with package managers
   - ✅ Clearly marked as pre-release

---

## Decision

**Support SemVer 2.0 pre-release syntax** for continuous development:

**Format:** `MAJOR.MINOR.PATCH-PRERELEASE`

**Examples:**
- `2.0.0-alpha.1` - Early testing
- `2.0.0-beta.3` - Later testing
- `2.0.0-rc.1` - Release candidate
- `2.1.0-ballot.1` - Ballot release

**Rules:**
- Product leads can create pre-releases **at any time**
- Pre-releases used for:
  - Testing Draft features
  - Ballot releases (features under consideration for advancement)
  - Work-in-progress snapshots
- Pre-releases **do not require** formal approval process
- Pre-releases **clearly marked** in GitHub releases

**Precedent:** [VRS repository](https://github.com/ga4gh/vrs/releases) already uses this pattern

---

## Consequences

### Positive

✅ Enables rapid iteration  
✅ Stable snapshots for testing  
✅ SemVer compliant (tooling support)  
✅ Can reference specific versions in issues/PRs  
✅ No formal approval overhead  
✅ Clear signal (pre-release = not stable)  
✅ Works with package managers (opt-in to pre-releases)  

### Negative

❌ Proliferation of version numbers  
❌ Implementers might use pre-releases in production (despite warnings)  
❌ Old pre-releases clutter release page  
❌ Must document pre-release meaning  

### Risks & Mitigations

**Risk:** Implementers treat pre-releases as stable
- **Mitigation:** Clear warnings in release notes, documentation

**Risk:** Too many pre-releases (version spam)
- **Mitigation:** Product leads discretion, clean up old pre-releases

**Risk:** Confusion about which pre-release to use
- **Mitigation:** Point to latest stable in README, mark pre-releases clearly

---

## References

- **Full Policy:** [TASC Technical Specification Maintenance](../recommendations/TASC%20Technical%20Specification%20Maintenance.md#pre-releases)
- **SemVer 2.0 Pre-releases:** [semver.org section 9](https://semver.org/#spec-item-9)
- **Example:** [VRS Releases](https://github.com/ga4gh/vrs/releases)
- **Related ADRs:**
  - [ADR-004: Semantic Versioning Rules](004-semantic-versioning-maturity-rules.md)
  - [ADR-001: Four-Level Maturity Model](001-adopt-four-level-maturity-model.md)

---

## Notes

Pre-releases solve the tension between continuous development and stable releases. They allow rapid iteration on Draft features without the overhead of formal releases. The SemVer format ensures tooling compatibility while clearly signaling "not production-ready."
