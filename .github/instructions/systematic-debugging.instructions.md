---
applyTo: '**'
---

# Systematic Debugging

<!-- Source: https://github.com/obra/superpowers — Jesse Vincent (obra), MIT License -->

## Overview

Random fixes waste time and create new bugs. Quick patches mask underlying issues.

**Core principle:** ALWAYS find root cause before attempting fixes. Symptom fixes are failure.

**Violating the letter of this process is violating the spirit of debugging.**

## The Iron Law

```
NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST
```

If you haven't completed Phase 1, you cannot propose fixes.

## When to Use

Use for ANY technical issue:
- Test failures
- Bugs in production
- Unexpected behavior
- Performance problems
- Build failures
- Integration issues

**Use this ESPECIALLY when:**
- Under time pressure (emergencies make guessing tempting)
- "Just one quick fix" seems obvious
- You've already tried multiple fixes
- Previous fix didn't work
- You don't fully understand the issue

## The Four Phases

You MUST complete each phase before proceeding to the next.

### Phase 1: Root Cause Investigation

**BEFORE attempting ANY fix:**

1. **Read Error Messages Carefully**
   - Don't skip past errors or warnings
   - Read stack traces completely
   - Note line numbers, file paths, error codes

2. **Reproduce Consistently**
   - Can you trigger it reliably?
   - What are the exact steps?
   - If not reproducible → gather more data, don't guess

3. **Check Recent Changes**
   - What changed that could cause this?
   - Git diff, recent commits
   - New dependencies, config changes

4. **Gather Evidence in Multi-Component Systems**

   For each component boundary: log inputs, log outputs, verify config propagation. Run once to gather evidence, then analyze to identify failing component.

5. **Trace Data Flow**

   Where does bad value originate? Keep tracing up until you find the source. Fix at source, not at symptom.

### Phase 2: Pattern Analysis

1. Find working examples of similar code in the codebase
2. Compare references completely — don't skim
3. Identify every difference, however small
4. Understand all dependencies and assumptions

### Phase 3: Hypothesis and Testing

1. State clearly: "I think X is the root cause because Y"
2. Make the SMALLEST possible change to test hypothesis
3. One variable at a time — don't fix multiple things at once
4. If it doesn't work: form a NEW hypothesis, don't stack more fixes

### Phase 4: Implementation

1. Create a failing test case first
2. Implement ONE fix addressing the root cause
3. Verify the fix — test passes, no other tests broken
4. If fix doesn't work: return to Phase 1
5. **If 3+ fixes failed:** Stop. Question the architecture. Discuss before attempting more.

## Red Flags — STOP and Follow Process

If you catch yourself thinking any of these, return to Phase 1:
- "Quick fix for now, investigate later"
- "Just try changing X and see if it works"
- "It's probably X, let me fix that"
- "I don't fully understand but this might work"
- Proposing solutions before tracing data flow
- "One more fix attempt" (when already tried 2+)

## Quick Reference

| Phase | Key Activities | Success Criteria |
|-------|---------------|------------------|
| **1. Root Cause** | Read errors, reproduce, check changes, gather evidence | Understand WHAT and WHY |
| **2. Pattern** | Find working examples, compare | Identify differences |
| **3. Hypothesis** | Form theory, test minimally | Confirmed or new hypothesis |
| **4. Implementation** | Create test, fix, verify | Bug resolved, tests pass |
