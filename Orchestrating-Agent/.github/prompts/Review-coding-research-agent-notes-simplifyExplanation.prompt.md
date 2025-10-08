---
mode: Orchestrator
tools: ['mcp_filesystem', 'mcp_memory', 'mcp_sequential-thinking']
description: 'Compare Research and Coding agent notes, identify discrepancies'
---

# Compare Agent Notes

## Objective
Review Research and Coding agent outputs in `.agent-workspace/`, identify conflicts, determine which is correct.

## Step 1: Read Agent Notes

**Research Agent outputs:**
```bash
Read: .agent-workspace/research/findings.md
Read: .agent-workspace/research/decision.md
```

**Coding Agent outputs:**
```bash
Read: .agent-workspace/coding/architecture.md
Read: .agent-workspace/coding/implementation.md
```

## Step 2: Compare Using Sequential Thinking

**Analysis prompts:**
```markdown
1. Does Coding architecture match Research decision?
2. Do implementation details align with researched tool?
3. Are there version mismatches? (e.g., React 17 vs 18)
4. Do file paths/structure match what was researched?
5. Are there contradicting recommendations?
```

**For each discrepancy:**
- Note the conflict (what Research said vs what Coding did)
- Check which aligns with official documentation
- State which agent is correct

## Step 3: Report Findings

**Output format (50-75 words):**
```markdown
## Comparison Results

**Match**: [What aligns between agents]

**Discrepancy Found**: [Specific conflict]
- Research Agent: [What they said]
- Coding Agent: [What they did]
- Correct: [Which one, with reason]

**Recommendation**: [Action to fix - update Research notes or Coding implementation]
```

## Success Criteria
- All agent notes reviewed
- Discrepancies identified with evidence
- Clear statement of which agent is correct
- Actionable recommendation provided
