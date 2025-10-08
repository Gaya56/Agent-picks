---
mode: Orchestrator
tools: ['mcp_filesystem', 'mcp_memory', 'mcp_sequential-thinking']
description: 'Compare Research and Coding outputs, identify conflicts, state which is correct'
---

# Compare Agent Notes

## Objective
Find conflicts between Research and Coding outputs. State which is correct using exact file references.

## Step 1: Read Agent Notes

```bash
Read: .agent-workspace/research/findings.md
Read: .agent-workspace/research/decision.md
Read: .agent-workspace/coding/architecture.md
Read: .agent-workspace/coding/implementation.md
```

## Step 2: Compare Using Sequential Thinking

**5 key questions**:
1. Do architecture decisions match? (e.g., Research chose Redux, Coding built Zustand)
2. Do technical details align? (versions, APIs, patterns)
3. Any version conflicts? (Research said v5, Coding used v4)
4. Do file paths match recommendations? (Research suggested src/store, Coding used lib/state)
5. Contradicting patterns? (Research said REST, Coding built GraphQL)

## Step 3: Report Findings (50-75 Words)

**If Match**:
```
"Research and Coding aligned.
Decision: [library/tool]
Implementation: [file:line]
No conflicts found."
```

**If Discrepancy**:
```
"[Conflict description in simple English]

Research: [claim + reference]
Coding: [claim + file:line reference]
Correct: [which one]
Evidence: [exact code/config showing which is right]
Recommendation: [action to fix]"
```

**Example**:
```
"State management conflict found.

Research: Recommended Redux (findings.md:23)
Coding: Built Zustand store at src/store/index.ts:10
Correct: Zustand - project notes specify lightweight state (<5KB). Redux 45KB, Zustand 12KB.
Recommendation: Update research/decision.md to reflect Zustand choice."
```

## Success Criteria
- All 4 files reviewed
- Discrepancies identified with exact references
- Clear statement of which agent is correct (with evidence)
- Output under 75 words
