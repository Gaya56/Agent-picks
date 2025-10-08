# Agent System - Quick Setup Guide

## New Repository Setup (Under 50 Lines)

### Prerequisites
✅ Repository cloned and running locally  
✅ VS Code opened in repository root  
✅ GitHub Copilot extension installed

---

## Step 1: Create Agent Configuration (5 minutes)

### 1.1 Create Directory Structure
```bash
mkdir -p .github/chatmodes .github/instructions .github/prompts
```

### 1.2 Copy Agent Files
Copy from Agent-picks repo to your new repo:

**Research Agent** (if needed for this project):
- `.github/chatmodes/Research-Agent-code.chatmode.md`
- `.github/instructions/Research-Instructions.instructions.md`
- `.github/prompts/Phase-1-Research.prompt.md`
- `.github/prompts/Phase-2-Research.prompt.md`
- `.github/prompts/Phase-3-Research.prompt.md`

**Coding Agent** (primary development):
- `.github/chatmodes/Coding-Agent.chatmode.md`
- `.github/instructions/Coding-Agent.instructions.md`
- `.github/prompts/Coding-Agent-1.prompt.md`
- `.github/prompts/Coding-Agent-2.prompt.md`
- `.github/prompts/Coding-Agent-3.prompt.md`

**Orchestrator Agent** (coordination):
- `.github/chatmodes/Orchestrator.chatmode.md`
- `.github/instructions/Orchestrator.instructions.md`
- `.github/prompts/Review-coding-research-agent-notes-simplifyExplanation.prompt.md`
- `.github/prompts/track-project-checklist.prompt.md`
- `.github/prompts/Pick_Next-Agent-Fillout-prompt.prompt.md`

---

## Step 2: Create Workspace (1 minute)

```bash
mkdir -p .agent-workspace/research .agent-workspace/coding
touch .agent-workspace/project-state.md
```

Add to `.agent-workspace/project-state.md`:
```markdown
# Project Status

## Completed ✓

## Current →

## Next
```

---

## Step 3: Fill Out Instructions (10 minutes)

**Edit**: `.github/instructions/Coding-Agent.instructions.md`

Fill in YOUR project details:
- Project Name & Tech Stack
- Directory structure
- Naming conventions
- Code quality standards
- Testing approach

**Keep Research/Orchestrator instructions as-is** (they're generic)

---

## Step 4: Open 3 VS Code Windows

### Window 1: Orchestrator (Primary - Always Open)
1. Open Copilot Chat (`Ctrl+Shift+I`)
2. Type: `@workspace /chatmode`
3. Select: **Orchestrator**
4. First message: "Review this repository and explain the structure in simple English"

### Window 2: Coding Agent (Development Work)
1. Open Copilot Chat
2. Type: `@workspace /chatmode`
3. Select: **Coding-Agent**
4. Keep ready for when Orchestrator routes coding tasks

### Window 3: Research Agent (Optional - Tool Evaluation)
1. Open Copilot Chat
2. Type: `@workspace /chatmode`
3. Select: **Research-Agent-code**
4. Use only when you need to evaluate libraries/tools

---

## Step 5: Start with Orchestrator

**First command**:
```
"Analyze this repository and explain:
1. What this project does
2. Tech stack and file structure  
3. Key files, symbols, and entry points

Include exact file:line references."
```

Orchestrator will respond with simple English explanation + exact references.

---

## Workflow After Setup

1. **Ask Orchestrator**: "Where should I start?" or "What needs to be done?"
2. **Orchestrator routes you**: "Use Coding Agent for X" or "Use Research Agent for Y"
3. **Switch to that window**: Do the work with that agent
4. **Agent saves outputs**: To `.agent-workspace/research/` or `coding/`
5. **Back to Orchestrator**: "Compare the outputs" or "What's next?"
6. **Repeat**: Orchestrator → Coding/Research → Orchestrator

---

## Quick Reference

**Orchestrator Prompts** (Window 1):
- `/track-project-checklist` - Where are we?
- `/Review-coding-research-agent-notes` - Do outputs match?
- `/Pick_Next-Agent-Fillout-prompt` - What's next?

**Coding Prompts** (Window 2):
- `/Coding-Agent-1` - Architecture & planning
- `/Coding-Agent-2` - Implementation
- `/Coding-Agent-3` - Review & validation

**Research Prompts** (Window 3):
- `/Phase-1-Research` - Discovery
- `/Phase-2-Research` - Evaluation
- `/Phase-3-Research` - Implementation plan

---

## That's It! 🚀

Total setup time: ~15 minutes  
You're ready to start with Orchestrator analyzing your new repository.
