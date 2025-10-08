---
mode: Orchestrator
tools: ['mcp_filesystem', 'mcp_memory']
description: 'Track project status and explain current state in simple English'
---

# Track Project Progress

## Objective
Review `.agent-workspace/project-state.md`, summarize progress in simple English, confirm status with workspace notes.

## Step 1: Read Project State

```bash
Read: .agent-workspace/project-state.md
```

**Check:**
- What tasks are marked complete (✓)
- What's currently in progress (→)
- What's pending ( )

## Step 2: Verify with Agent Notes

**Cross-reference:**
```bash
If Research complete → Check: .agent-workspace/research/decision.md exists
If Coding complete → Check: .agent-workspace/coding/implementation.md exists
```

**Validate:**
- Does workspace match project-state.md checklist?
- Are there notes without checklist updates?
- Are there checklist items without notes?

## Step 3: Simple English Summary

**Output format (max 75 words):**
```markdown
## Project Status

**Completed**: [What's done - simple terms]
**Current**: [What we're working on now]
**Next**: [What's coming up]

**In Plain English**:
[1-2 sentences explaining where we are]

Example: "We finished researching authentication options and picked Passport.js. 
Currently building the login system. Next step is testing."
```

## Step 4: Update if Needed

If project-state.md is outdated:
```markdown
Update: project-state.md
Add: Completed tasks from workspace notes
Mark: Current task based on latest activity
```

## Success Criteria
- Status reflects actual workspace contents
- Summary is clear and jargon-free
- Next steps are obvious
- project-state.md is current
