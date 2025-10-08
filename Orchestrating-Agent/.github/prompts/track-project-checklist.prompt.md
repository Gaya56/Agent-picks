---
mode: Orchestrator
tools: ['filesystem', 'memory', 'Github', 'Context7', 'sequential-thinking']
description: 'Explain project status in simple English with exact technical references'
---

# Track Project Status

## Objective
Tell user where project is at in **simple English** with **exact code references**.

## Step 1: Read Project State

```bash
Read: .agent-workspace/project-state.md
```

Check sections:
- Completed ✓
- In Progress →
- Pending

## Step 2: Verify with Agent Notes

Cross-reference:
```bash
Read: .agent-workspace/research/decision.md (if exists)
Read: .agent-workspace/coding/implementation.md (if exists)
```

Confirm project-state.md matches actual workspace reality.

## Step 3: Explain in Simple English (Max 75 Words)

**Format**:
```
"[Current stage in plain language].

Completed: [what's done - 1 sentence]
Current: [what you're working on - 1 sentence]
Next: [what's next - 1 sentence]

File: [current work file:line]
Symbol: [function/component working on]
Imports: [key imports if relevant]
Workflow: [step → step → step]"
```

**Example**:
```
"Building authentication system.

Completed: Login form with validation
Current: Token refresh logic
Next: Logout and session timeout

File: src/auth/refresh.ts:23
Function: refreshToken
Imports: jwt, axios
Workflow: Check expiry → request new token → update storage → retry failed request"
```

## Step 4: Update if Needed

If `project-state.md` outdated:
```bash
Update: .agent-workspace/project-state.md
Sync: Match actual agent outputs
```

## Success Criteria
- Status reflects workspace reality
- Explanation in plain English (no jargon)
- Exact file:line references included
- Next steps obvious
- Under 75 words
