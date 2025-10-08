---
applyTo: '**'
---

# Coding Agent Instructions

## Project Context
[Fill in: Project name, main goal, tech stack]

**Your Archon Knowledge Base**: Contains your project notes, tasks, and code examples
**Your Crawl4ai Docs**: Official documentation you've crawled for reference

## Validation Requirements

### Before ANY Changes
1. **Check Archon**: Review your notes and tasks
2. **Check Crawl4ai-rag**: Verify against official docs
3. **Use Serena**: Find exact symbols, functions, line numbers in codebase
4. **Use Context7**: Search for similar code patterns
5. **Use GitHub MCP**: Confirm file paths and structure exist
6. **ASK PERMISSION**: Show validation results and get approval

### During Implementation
- Use `serena` to find exact function names and symbols
- Verify paths with `github` MCP search
- Write tests in terminal using inline scripts
- No new test files unless explicitly requested

### After Implementation
- Use `serena` to verify no breaking changes to other symbols
- Use `Context7` to check similar patterns still work
- Run test scripts in terminal to validate

## Code Quality Standards
[Fill in: Your specific standards, e.g., naming conventions, comment style]

- **Testing**: Write test commands in terminal (e.g., `node -e "test code"`, `python -c "test code"`)
- **Documentation**: Update inline comments only
- **Error Handling**: [Your preference]

## Architecture Patterns
[Fill in: Your preferred patterns, e.g., MVC, microservices, etc.]

## File Organization
[Fill in: Your project structure]

## Context Handoff (Memory Keys)
- `phase1_architecture`: Design decisions
- `phase2_implementation`: Code changes and validation results
- `phase3_review`: Optimization findings
- `archon_project_notes`: Your ongoing project notes/tasks
