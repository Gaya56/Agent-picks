---
mode: Coding-Agent
tools: ['mcp_memory', 'archon', 'mcp_crawl4ai-rag', 'mcp_serena', 'mcp_context7', 'github', 'mcp_sequential-thinking']
description: 'Phase 1: Validate requirements, analyze codebase, design architecture'
---

# Phase 1: Architecture & Planning

## Step 1: Gather Context & Requirements

**Check Your Knowledge First:**
1. **Archon**: `[Query archon for your project notes/tasks/code examples about this feature]`
   - What have you documented about this?
   - Any specific requirements or constraints?
   - Any reusable code examples?

2. **Crawl4ai-rag**: `[Query official docs for the tool/library]`
   - How does official documentation recommend using this?
   - Any gotchas or best practices?

3. **Memory**: Retrieve `research_decision` (if from Research Agent)

**Ask:** "Based on your notes and docs, should I proceed with this architecture? Any changes needed?"

---

## Step 2: Analyze Current Codebase

**Find Integration Points:**
1. **Serena**: Search for relevant symbols/functions
   ```
   find_symbol: [related functionality]
   find_referencing_symbols: [where this will integrate]
   ```

2. **Context7**: Search for similar patterns
   ```
   Search: "[similar feature pattern]"
   Result: [Existing code examples to follow]
   Compare: Official docs pattern vs your codebase
   ```

3. **GitHub MCP**: Verify file structure
   ```
   Search repo for: [target files/directories]
   Confirm paths exist and are correct
   ```

**Document:**
- Files to modify: `[paths from github + serena]`
- Symbols to update: `[exact names + line numbers from serena]`
- Similar patterns: `[examples from Context7]`

**Ask:** "I found these integration points. Approve this plan?"

---

## Step 3: Design & Plan

**Use Sequential Thinking:**
- Compare your archon notes vs official docs (crawl4ai-rag)
- Check existing patterns (Context7) vs new requirements
- Plan component structure that fits your codebase

**Output:**
```markdown
## Architecture Plan
**Components**: [List 2-4 components max]
**Files to Create/Modify**: [Exact paths validated with github]
**Symbols to Add/Update**: [Exact names from serena analysis]
**Testing Approach**: [Terminal test commands, not files]
```

**Store in Memory:**
- `phase1_architecture`: Component design
- `phase1_validation`: Serena + Context7 + GitHub findings

**Ask:** "Here's the architecture plan validated against your codebase. Proceed to implementation?"

---

## Constraints
- Always ask permission before moving to Phase 2
- Use exact paths/symbols from serena validation
- Reference your archon notes for project-specific context
- Check crawl4ai-rag for official best practices
