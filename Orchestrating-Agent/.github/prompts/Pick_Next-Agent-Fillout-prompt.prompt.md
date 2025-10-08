---
mode: Orchestrator
tools: ['mcp_filesystem', 'mcp_memory', 'mcp_sequential-thinking']
description: 'Pick next agent (Research or Coding) and prepare their prompt with workspace context'
---

# Route to Next Agent

## Objective
Decide which agent to use next. Fill their prompt with context from workspace.

## Step 1: Analyze Current State

```bash
Read: .agent-workspace/project-state.md
Read: .agent-workspace/research/*.md (if exists)
Read: .agent-workspace/coding/*.md (if exists)
```

**Sequential thinking**:
1. What's the last completed task?
2. Is there a research decision? (check research/decision.md)
3. Is architecture designed? (check coding/architecture.md)
4. What's the logical next step?

## Step 2: Pick Agent

**Research Agent** if:
- No tool/library selected
- Need to compare options
- Need API docs review
- Technical decision pending

**Coding Agent** if:
- Research decision exists
- Ready for architecture design
- Ready to implement feature
- Clear technical direction

## Step 3: Explain in Simple English (Max 75 Words)

**Format**:
```
"[Current situation - 1 sentence]

Next Agent: [Research/Coding]
Reason: [Why this agent now - 1 sentence]
Context: [2-3 key facts from workspace they need]

Expected Output: [What they should produce]
Save To: [which workspace file]"
```

**Example for Research**:
```
"Need state management library for React app.

Next Agent: Research
Reason: No library chosen yet, need evaluation
Context: 
- Small app (~10 components)
- Need <20KB bundle impact
- TypeScript required

Expected Output: Compare Redux/Zustand/Jotai with recommendation
Save To: .agent-workspace/research/decision.md"
```

**Example for Coding**:
```
"Zustand selected for state management (see research/decision.md).

Next Agent: Coding
Reason: Decision made, ready to build
Context:
- Use Zustand v4.5.0
- Store at src/store/index.ts
- Need auth + cart slices

Expected Output: Store architecture + implementation
Save To: .agent-workspace/coding/architecture.md, implementation.md"
```

## Step 4: Update Memory

```bash
Store: orchestrator_last_decision
Content: "[Agent chosen] - [reason] - [timestamp]"
```

## Success Criteria
- Decision based on workspace analysis (not assumptions)
- Clear reason for agent choice in plain English
- Context includes relevant workspace details
- Exact file references where applicable
- Under 75 words
