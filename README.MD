# Multi-Agent Development System

Three specialized AI agents for research, coding, and project coordination. See [AGENT-TOOLS.md](./AGENT-TOOLS.md) for tool details.

## The Three Agents

**🔍 Research Agent** - Discovers, evaluates, and recommends tools/libraries through 3-phase process  
**💻 Coding Agent** - Permission-based development with 5-source validation  
**🎯 Orchestrator** - Coordinates agents, explains in simple English with exact technical references

## Quick Setup (15 minutes)

1. **Copy agent files** to `.github/chatmodes/`, `.github/instructions/`, `.github/prompts/`
2. **Create workspace**: `mkdir -p .agent-workspace/research .agent-workspace/coding`
3. **Fill out** `Coding-Agent.instructions.md` with your project details
4. **Open 3 VS Code windows**, select chat modes: Orchestrator, Coding-Agent, Research-Agent-code
5. **Start**: Ask Orchestrator to analyze your repository

## Typical Workflow

1. Orchestrator → "Where are we?" or "What's next?"
2. Orchestrator routes → "Use Coding Agent for X"
3. Switch to Coding/Research window → Do the work
4. Agents save outputs → `.agent-workspace/research/` or `coding/`
5. Back to Orchestrator → "Compare outputs" or track progress

## Repository Structure

```
.github/
├── chatmodes/          # Agent behaviors (3 files)
├── instructions/       # Project context (3 files)
└── prompts/            # Workflows (9 files: Research 3, Coding 3, Orchestrator 3)
Research-Agent/         # Docs + framework guides
Coding-Agent/           # Docs + implementation notes
Orchestrating-Agent/    # Docs + usage guides
.agent-workspace/       # Shared outputs (research/, coding/, project-state.md)
```

## Key Features

- **Token Efficient**: Prompts 40-50% smaller, responses 50-75 words (Orchestrator)
- **Exact References**: file:line, symbols, imports, hooks, workflows
- **Permission-Based**: Coding Agent asks before changes
- **5-Source Validation**: archon → crawl4ai-rag → serena → context7 → github
- **Simple English**: Technical precision in plain language
- **Workspace Coordination**: All agents save outputs for handoffs

## Requirements

- VS Code + GitHub Copilot extension
- MCP tools: memory, filesystem, serena, github, context7, sequential-thinking, archon, crawl4ai-rag

## Documentation

- **[AGENT-TOOLS.md](./AGENT-TOOLS.md)**: Tool reference for all agents
- **[Research-Agent/README.md](./Research-Agent/README.md)**: Research workflows
- **[Coding-Agent/README.md](./Coding-Agent/README.md)**: Development patterns
- **[Orchestrating-Agent/README.md](./Orchestrating-Agent/README.md)**: Coordination guide
