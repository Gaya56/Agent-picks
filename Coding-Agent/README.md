# Coding Agent Framework

Permission-based, validation-first development assistant. Works with your project knowledge (archon) and official docs (crawl4ai-rag).

## Quick Start

1. **Add Your Knowledge**: Store project notes/tasks in `archon`
2. **Crawl Docs**: Use `crawl4ai-rag` to index official documentation
3. **Configure**: Edit `.github/instructions/Coding-Agent.instructions.md` (minimal setup)
4. **Run Phases**: Architecture → Implementation → Review (permission at each step)

## What Makes This Different

- **Always asks permission** before making changes
- **Validates with your knowledge** (archon notes + crawl4ai docs)
- **Double-checks codebase** (serena symbols + Context7 patterns + github structure)
- **Tests in terminal** (no new test files)
- **Flexible** - works with any project type

## Fill-In Guide (Minimal)

### Instructions: `.github/instructions/Coding-Agent.instructions.md`

| Section | Fill With |
|---------|-----------|
| Project Context | Name, goal, tech stack (1-2 sentences) |
| Code Quality | Your naming/comment preferences |
| Architecture | Your patterns (if any) |
| File Organization | Your project structure (if non-standard) |

Everything else is optional and flexible.

## How It Works

### Phase 1: Architecture (Permission Required)

1. Checks **your archon notes/code examples** for requirements
2. Checks **crawl4ai-rag docs** for best practices
3. Uses **serena** to find exact symbols/paths
4. Uses **Context7** to review official docs + compare with your patterns
5. Uses **github MCP** to verify structure
6. **Asks permission** to proceed

### Phase 2: Implementation (Permission Per Component)

1. Validates symbols with **serena** (exact line numbers)
2. Validates patterns with **Context7**
3. Validates paths with **github MCP**
4. **Asks permission** for each component
5. Tests in **terminal** (no new files)
6. Validates after each change

### Phase 3: Review (Permission for Optimizations)

1. Compares before/after with **serena**
2. Checks patterns with **Context7**
3. Verifies against **archon notes**
4. **Asks permission** for any optimizations
5. Offers to save learnings to archon

## Tools

| Tool | Purpose |
|------|---------|
| **archon** | Your project knowledge, notes, tasks, code examples |
| **mcp_crawl4ai-rag** | Official docs you've crawled |
| **mcp_serena** | Find exact symbols, functions, line numbers |
| **mcp_context7** | Review official docs + compare with your codebase patterns |
| **github** | Verify file paths and structure |
| **mcp_memory** | Phase handoffs |
| **mcp_sequential-thinking** | Validation reasoning |

## Key Features

✓ Permission-based (never changes without approval)  
✓ Validation-first (checks serena + Context7 + github before implementing)  
✓ Knowledge-integrated (uses your archon notes + crawl4ai docs)  
✓ Terminal testing (no test file clutter)  
✓ Flexible (works with any project structure)  

## Usage Example

```bash
# Phase 1: Plan with validation
@workspace Use Coding-Agent-1.prompt.md for authentication

# Phase 2: Implement component by component
@workspace Use Coding-Agent-2.prompt.md

# Phase 3: Review and save learnings
@workspace Use Coding-Agent-3.prompt.md
```

## Documentation

- **[FRAMEWORK-GUIDE.md](FRAMEWORK-GUIDE.md)**: Detailed guide with validation protocol
- **[ARCHON-INTEGRATION.md](ARCHON-INTEGRATION.md)**: Using archon for project knowledge
- **[VALIDATION-CHECKLIST.md](VALIDATION-CHECKLIST.md)**: Complete validation steps
