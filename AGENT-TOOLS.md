# Agent Tools Reference

## Tools by Agent

| Tool Name | Research Agent | Coding Agent | Orchestrator Agent | Purpose |
|-----------|:--------------:|:------------:|:------------------:|---------|
| **mcp_memory** | ✅ | ✅ | ✅ | Store context between phases and sessions (candidates, decisions, routing) |
| **mcp_filesystem** | ✅ | ✅ | ✅ | Read/write files, explore codebase, manage workspace outputs |
| **mcp_serena** | ✅ | ✅ | ❌ | Symbolic code analysis (find symbols, references, exact line numbers) |
| **github** | ✅ | ✅ | ❌ | Search repositories, discover candidates, verify file paths and structure |
| **mcp_context7** | ✅ | ✅ | ❌ | Fetch documentation, compare patterns with official sources |
| **mcp_sequential-thinking** | ✅ | ✅ | ✅ | Multi-step reasoning, decision matrices, conflict analysis |
| **archon** | ❌ | ✅ | ❌ | User's project knowledge, notes, tasks, reusable code examples |
| **mcp_crawl4ai-rag** | ❌ | ✅ | ❌ | User's crawled official documentation for validation |
| **Total Tools** | **6** | **8** | **3** | |

---

## Tool Details by Agent

### Research Agent (6 Tools)

| Tool | Primary Use Cases |
|------|------------------|
| **mcp_memory** | Store baseline data, candidate lists, comparison matrices, phase handoffs |
| **mcp_filesystem** | Explore codebase structure, reference project files, read configurations |
| **mcp_serena** | Analyze project architecture, check API compatibility, validate integration points |
| **github** | Search repositories, discover tool candidates, analyze patterns/PRs/releases |
| **mcp_context7** | Fetch initial documentation, deep-dive API docs, compare implementation patterns |
| **mcp_sequential-thinking** | Build decision matrices, weighted scoring, final selection reasoning |

**Workflow**: Discovery (github search + memory) → Evaluation (context7 docs + serena compatibility) → Decision (sequential-thinking matrix)

---

### Coding Agent (8 Tools)

| Tool | Primary Use Cases |
|------|------------------|
| **mcp_memory** | Context storage between phases, save architecture/implementation details |
| **mcp_filesystem** | Create/read/write files, explore directory structure, manage code files |
| **mcp_serena** | Find exact symbols/functions/line numbers, symbolic editing, reference analysis |
| **github** | Verify file paths, confirm repository structure, search for patterns |
| **mcp_context7** | Compare official patterns with codebase implementation, pattern search |
| **mcp_sequential-thinking** | Multi-step validation reasoning, architecture planning, review analysis |
| **archon** | Check project notes, retrieve requirements, access saved code examples |
| **mcp_crawl4ai-rag** | Verify against crawled official docs, check API usage, validate patterns |

**5-Source Validation Flow**: archon (notes) → crawl4ai-rag (docs) → serena (symbols) → context7 (patterns) → github (verify)

---

### Orchestrator Agent (3 Tools)

| Tool | Primary Use Cases |
|------|------------------|
| **mcp_filesystem** | Read workspace outputs (research/findings.md, coding/implementation.md, project-state.md) |
| **mcp_memory** | Track routing decisions, store discrepancies, maintain project summary |
| **mcp_sequential-thinking** | Compare agent notes, analyze conflicts, multi-step reasoning for routing decisions |

**Workflow**: Read workspace (filesystem) → Analyze conflicts (sequential-thinking) → Track decisions (memory) → Explain in simple English

---

## Tool Categories

### Core Tools (All Agents)
- **mcp_memory**: Context persistence
- **mcp_filesystem**: File operations
- **mcp_sequential-thinking**: Multi-step reasoning

### Code Analysis Tools (Research + Coding)
- **mcp_serena**: Symbolic analysis, exact locations
- **github**: Repository search, verification
- **mcp_context7**: Documentation and pattern comparison

### Knowledge Tools (Coding Only)
- **archon**: User's project-specific knowledge
- **mcp_crawl4ai-rag**: Crawled official documentation

### Orchestrator Specialty
- **Minimal toolset**: Only needs filesystem, memory, and sequential-thinking
- **Focus**: Coordination and explanation, not code analysis

---

## Tool Installation Requirements

### Required for Research Agent
```bash
# Install MCP servers
mcp_memory, mcp_filesystem, mcp_serena, github, mcp_context7, mcp_sequential-thinking
```

### Required for Coding Agent
```bash
# Install MCP servers
mcp_memory, mcp_filesystem, mcp_serena, github, mcp_context7, mcp_sequential-thinking, archon, mcp_crawl4ai-rag
```

### Required for Orchestrator Agent
```bash
# Install MCP servers (minimal)
mcp_memory, mcp_filesystem, mcp_sequential-thinking
```

---

## Tool Configuration Notes

### Flexible Tool Names
Some MCP servers have naming variations. Update `tools:` array in chat modes if needed:
- `context7` vs `mcp_context7`
- `crawl4ai-rag` vs `mcp-crawl4ai-rag` vs `mcp_crawl4ai-rag`
- `github` vs `mcp_github`

### Optional vs Required
- **Coding Agent**: Can work without archon/crawl4ai-rag (asks user for info)
- **Research Agent**: Can work without context7 (uses github for docs)
- **Orchestrator**: All 3 tools required for full functionality

### VS Code Settings
```json
{
  "github.copilot.chat.tools": {
    "mcp_memory": true,
    "mcp_filesystem": true,
    "mcp_serena": true,
    "github": true,
    "mcp_context7": true,
    "mcp_sequential-thinking": true,
    "archon": true,
    "mcp_crawl4ai-rag": true
  }
}
```

---

## Tool Usage Examples

### Research Agent Example
```
Phase 1: github search → mcp_memory (save candidates)
Phase 2: mcp_context7 docs + mcp_serena compatibility → mcp_memory (save evaluation)
Phase 3: mcp_sequential-thinking (decision matrix) → mcp_filesystem (save to workspace)
```

### Coding Agent Example
```
Validation: archon notes → crawl4ai-rag docs → serena symbols → context7 patterns → github verify
Implementation: serena (find location) → filesystem (edit file) → terminal test
Save: filesystem (write to .agent-workspace/coding/)
```

### Orchestrator Example
```
Status: filesystem (read workspace files) → explain in simple English
Compare: filesystem (read research + coding) → sequential-thinking (analyze) → state which is correct
Route: sequential-thinking (analyze needs) → memory (store decision) → filesystem (update project-state.md)
```

---

*Last Updated: October 8, 2025*  
*Edit this file to match your specific MCP tool configuration*
