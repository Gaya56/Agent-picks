---
mode: Coding-Agent
tools: ['mcp_memory', 'mcp_serena', 'mcp_context7', 'github', 'archon', 'mcp_sequential-thinking']
description: 'Phase 3: Review implementation, validate changes, optimize'
---

# Phase 3: Review, Validation & Optimization

## Step 1: Compare Before/After

**Load Implementation:**
- Memory: `phase2_implementation`, `phase2_validation`

**Validation Checks:**
1. **Serena**: Compare implementation vs Phase 1 architecture
   ```
   find_symbol: [each implemented component]
   Verify: Matches designed interfaces
   ```

2. **Context7**: Search for similar patterns
   ```
   Search: [feature type]
   Compare: Your implementation vs existing patterns
   ```

3. **Archon**: Check your notes
   ```
   Query: [project requirements for this feature]
   Verify: Implementation meets your documented needs
   ```

**Output:**
```markdown
## Validation Results
✓ Matches architecture: [Yes/No]
✓ Follows codebase patterns: [Yes/No]
✓ Meets project requirements: [Yes/No]
```

**Ask:** "Implementation validated. Any concerns before optimization?"

---

## Step 2: Identify Optimizations (Optional)

**Sequential Thinking:**
- Is there duplicate code?
- Can performance be improved?
- Are error messages clear?
- Does it follow your archon documented standards?

**If optimizations needed:**

**Ask:** "Found [N] optimization opportunities. Should I apply them?"

**For each approved optimization:**
1. Use serena to make precise changes
2. Test in terminal
3. Validate with Context7 (similar patterns still work)

---

## Step 3: Final Summary

**Store in Memory:**
- `phase3_review`: Validation results
- `coding_session_summary`: Complete summary for orchestrator

**Summary Output:**
```markdown
## Implementation Complete
**Files Changed**: [list with line numbers]
**Symbols Added/Modified**: [exact names]
**Tests**: [terminal commands that passed]
**Validation**: Serena ✓ | Context7 ✓ | GitHub ✓
**Notes for Archon**: [Any learnings to save]
```

**Ask:** "Review complete. Save these learnings to your archon knowledge base?"

---

## Constraints
- Always compare against Phase 1 architecture
- Use serena to verify no breaking changes
- Check Context7 for pattern consistency
- Ask permission before any optimizations
- Offer to save learnings to archon
