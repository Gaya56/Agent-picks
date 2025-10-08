# Multi-Agent Development System

Three specialized AI agents for research, coding, and project coordination.

## 🚀 Quick Start

**New to this system?** → Read **[QUICK-SETUP.md](./QUICK-SETUP.md)** (Under 50 lines)

For detailed documentation → Read **[COMPLETE-AGENT-SYSTEM.md](./COMPLETE-AGENT-SYSTEM.md)**

---

## Agents Overview

### 🔍 Research Agent
Discovers, evaluates, and recommends tools/libraries through 3-phase process.

- **Use when**: Need to compare libraries, evaluate APIs, research tools
- **Saves to**: `.agent-workspace/research/`
- **Documentation**: [Research-Agent/README.md](./Research-Agent/README.md)

### 💻 Coding Agent
Permission-based development with validation-first workflow.

- **Use when**: Design architecture, implement features, review code
- **Saves to**: `.agent-workspace/coding/` (with exact file:line references)
- **Documentation**: [Coding-Agent/README.md](./Coding-Agent/README.md)

### 🎯 Orchestrator Agent
Your brainstorming partner who explains in simple English with exact technical references.

- **Use when**: Need project status, compare outputs, route next task, clarify ideas
- **Maintains**: `.agent-workspace/project-state.md`
- **Documentation**: [Orchestrating-Agent/README.md](./Orchestrating-Agent/README.md)

---

## Typical Workflow

1. **Start with Orchestrator** → "Where are we in this project?"
2. **Get routed** → "Use Coding Agent to implement X"
3. **Switch to Coding Agent** → Do the work, save to workspace
4. **Back to Orchestrator** → "Compare outputs" or "What's next?"
5. **Repeat** → Orchestrator coordinates everything

---

## Setup for New Repository

See **[QUICK-SETUP.md](./QUICK-SETUP.md)** for step-by-step guide (~15 minutes):

1. Copy agent files to `.github/` folder
2. Create `.agent-workspace/` directory
3. Fill out Coding-Agent instructions with your project details
4. Open 3 VS Code windows with different chat modes
5. Start with Orchestrator analyzing your repo

---

## Repository Structure

```
Agent-picks/
├── QUICK-SETUP.md              # Setup guide for new repos
├── COMPLETE-AGENT-SYSTEM.md    # Full system documentation
├── Research-Agent/             # Research agent files
├── Coding-Agent/               # Coding agent files
├── Orchestrating-Agent/        # Orchestrator agent files
└── .agent-workspace/           # Shared coordination workspace
    ├── research/               # Research outputs
    ├── coding/                 # Coding outputs
    └── project-state.md        # Project status
```

---

## Key Features

- **Token Efficient**: Prompts reduced by 40-50%
- **Exact References**: Always includes file:line, symbols, imports, hooks
- **Simple English**: Orchestrator explains technical concepts plainly
- **Permission-Based**: Coding Agent asks before making changes
- **Validation-First**: Checks 5 sources before implementing
- **Workspace Coordination**: All agents save to shared location

---

## Documentation

- **[QUICK-SETUP.md](./QUICK-SETUP.md)**: New repository setup (under 50 lines)
- **[COMPLETE-AGENT-SYSTEM.md](./COMPLETE-AGENT-SYSTEM.md)**: Full system overview
- **[Research-Agent/README.md](./Research-Agent/README.md)**: Research agent guide
- **[Coding-Agent/README.md](./Coding-Agent/README.md)**: Coding agent guide
- **[Orchestrating-Agent/README.md](./Orchestrating-Agent/README.md)**: Orchestrator guide

---

## Requirements

- VS Code with GitHub Copilot extension
- MCP tools (memory, filesystem, serena, github, Context7, archon, crawl4ai-rag, sequential-thinking)

---

## Support

For issues, improvements, or questions, see individual agent README files or the complete system documentation.
