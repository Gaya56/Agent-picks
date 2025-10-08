# Orchestrator Agent - Quick Start (20 Lines)

## Setup (3 lines)
1. Create workspace: `.agent-workspace/` with subdirs: `research/`, `coding/`
2. Create `project-state.md` template: `# Completed ✓`, `# In Progress →`, `# Pending`
3. Ensure Research and Coding agents save outputs to respective directories

## Three Prompts Usage (9 lines)
**1. Compare Notes** (`Review-coding-research-agent-notes-simplifyExplanation.prompt.md`)
- Use after both agents have written outputs
- Finds conflicts between research/decision.md and coding/architecture.md
- States which agent is correct with reasoning

**2. Track Progress** (`track-project-checklist.prompt.md`)
- Use anytime to understand "where are we?"
- Explains status in plain English (max 75 words)
- Updates project-state.md to reflect current reality

**3. Pick Next Agent** (`Pick_Next-Agent-Fillout-prompt.prompt.md`)
- Use when ready for next task
- Analyzes workspace, decides Research or Coding
- Fills out chosen agent's prompt with context

## Workflow (4 lines)
1. Research Agent runs → saves to `.agent-workspace/research/`
2. Orchestrator compares notes → identifies discrepancies
3. Coding Agent runs → saves to `.agent-workspace/coding/`
4. Orchestrator tracks progress → picks next agent → repeat

## Response Style (4 lines)
- Ultra-concise: 50-75 words max
- No procedures - just answers
- Decisive, not exploratory
- Coordinator, not executor
