---
mode: Orchestrator
tools: ['mcp_filesystem', 'mcp_memory', 'mcp_sequential-thinking']
description: 'Decide next agent (Research or Coding) and prepare their prompt'
---

# Route to Next Agent

## Objective
Analyze workspace state, decide which agent to use next, fill out their prompt with context from shared workspace.

## Step 1: Analyze Current State

**Read workspace:**
```bash
Read: .agent-workspace/project-state.md
Read: .agent-workspace/research/*.md (if exists)
Read: .agent-workspace/coding/*.md (if exists)
```

**Sequential thinking:**
```markdown
1. What was the last completed task?
2. Is there a research decision? (check research/decision.md)
3. Is architecture designed? (check coding/architecture.md)
4. What's the next logical step?
```

## Step 2: Decision Logic

**Choose Research Agent if:**
- No tool/library selected yet
- Need to compare options
- Need API documentation review
- Technical decision pending

**Choose Coding Agent if:**
- Research decision exists
- Ready to design architecture
- Ready to implement feature
- Have clear technical direction

## Step 3: Prepare Agent Prompt

**For Research Agent:**
```markdown
## Research Task
**Goal**: [From project-state.md next task]
**Context**: [What Coding Agent needs - from coding notes]
**Constraints**: [Project requirements - from workspace]

Use: Research-Agent Phase-[1/2/3].prompt.md
```

**For Coding Agent:**
```markdown
## Coding Task
**Research Decision**: [From research/decision.md]
**Integration Points**: [From coding/architecture.md if exists]
**Requirements**: [From project-state.md]

Use: Coding-Agent-[1/2/3].prompt.md
```

## Step 4: Output Decision

**Format (max 75 words):**
```markdown
## Routing Decision

**Current Status**: [1 sentence summary]
**Next Agent**: Research/Coding
**Reason**: [Why this agent now]
**Prompt File**: [Exact prompt filename]

**Context for Agent**:
[2-3 key facts from workspace they need to know]

**Expected Output**:
[What this agent should produce]
```

## Step 5: Update Memory

```bash
Store: orchestrator_last_decision
Content: [Agent chosen, reason, timestamp]
```

## Success Criteria
- Decision based on workspace analysis (not assumptions)
- Clear reason for agent choice
- Prompt context includes relevant workspace info
- Next agent has everything they need to proceed
