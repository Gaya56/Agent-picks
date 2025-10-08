# Research Agent Framework

A token-efficient, multi-phase research framework for GitHub Copilot. Discover, evaluate, and implement tools/libraries through structured workflows.

## Quick Start

1. **Customize Instructions**: Fill out `.github/instructions/Research-Instructions.instructions.md` with your project context
2. **Run Phase 1**: Use Phase-1 prompt to discover 5-8 candidates → narrow to top 3-4
3. **Run Phase 2**: Deep evaluation of finalists → narrow to top 2-3
4. **Run Phase 3**: Final decision + implementation plan with code examples

## Component Fill-Out Guide

### Chat Mode (`.github/chatmodes/Research-Agent-code.chatmode.md`)

| Field | Value | Notes |
|-------|-------|-------|
| **description** | One-line summary | Keep under 100 chars |
| **tools** | `['mcp_memory', 'mcp_filesystem', 'mcp_serena', 'github', 'mcp_context7', 'mcp_sequential-thinking', 'crawl4ai-rag-mcp']` | Add/remove based on available MCP servers |

### Instructions (`.github/instructions/Research-Instructions.instructions.md`)

| Section | What to Fill | Example |
|---------|-------------|---------|
| **Research Objectives** | Domain, stack, architecture | "Discover state management for React 18" |
| **Current Stack** | Language, framework, build tools | "React 18, TypeScript 5.x, Vite" |
| **Evaluation Criteria Weights** | Adjust percentages | Maturity 20%, Compatibility 25%, etc. |

### Phase 1 Prompt (Discovery)

| Section | What to Fill | Example |
|---------|-------------|---------|
| **Search Criteria** | Stars, activity, language, keywords | ">1000 stars, 'state management'" |
| **Output per Candidate** | GitHub URL, stars, score, features | Document 5-8 tools |

### Phase 2 Prompt (Evaluation)

| Section | What to Fill | Example |
|---------|-------------|---------|
| **API Patterns** | Code examples (10-15 lines) | Installation, config, usage snippets |
| **Comparison Matrix** | Weighted scores | API Compatibility 25%, Community 15% |

### Phase 3 Prompt (Implementation)

| Section | What to Fill | Example |
|---------|-------------|---------|
| **Decision Matrix** | Final weighted scoring | Technical Fit 40%, Maintenance 35% |
| **Implementation Checklist** | Install, config, integrate, test | Prerequisites, code snippets (15-20 lines) |

## Available Tools

**Core**: `mcp_memory`, `mcp_filesystem`, `mcp_serena`, `github`, `mcp_context7`, `mcp_sequential-thinking`  
**Optional**: `crawl4ai-rag-mcp` (for live doc scraping + RAG)

## Key Features

- **Token-efficient**: 150-200 words per section
- **Progressive narrowing**: 8→4→3 candidate funnel
- **Context continuity**: Memory-based handoffs between phases
- **Modular**: Reusable across projects

## Documentation

- **FRAMEWORK-GUIDE.md**: Architecture overview
- **VALIDATION-CHECKLIST.md**: Validation + enhancement roadmap
- **CRAWL4AI-INTEGRATION.md**: Live documentation scraping setup

---

**Version**: 1.0 | **Last Updated**: 2025-10-08 | **Compatible With**: GitHub Copilot Chat (VS Code)
