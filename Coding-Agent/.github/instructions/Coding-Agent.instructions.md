---
applyTo: '**'
# Use more specific patterns if needed, e.g., 'src/**/*.ts' for TypeScript in src/
---

# Coding Agent - Project Instructions

## Project Overview
<!-- Provide high-level context about this project -->

**Project Name**: [e.g., E-commerce API, React Dashboard, ML Pipeline]  
**Primary Goal**: [e.g., Build REST API for product catalog, Create admin dashboard, Train recommendation model]  
**Tech Stack**: [e.g., Node.js + Express + PostgreSQL, React + TypeScript + Tailwind, Python + PyTorch]

## Your Knowledge Sources
<!-- These are referenced by the coding agent for validation -->

**Archon Knowledge Base**: Your project notes, requirements, tasks, and reusable code examples  
**Crawl4ai Documentation**: Official docs you've crawled for libraries/frameworks in use  

> **Setup**: Populate archon with project-specific knowledge and use crawl4ai-rag to index relevant official documentation before starting development.

## Code Quality Standards

### Naming Conventions
**Example**: 
- Functions: `camelCase` (e.g., `getUserById`, `calculateTotal`)
- Classes: `PascalCase` (e.g., `UserController`, `DatabaseManager`)
- Constants: `UPPER_SNAKE_CASE` (e.g., `MAX_RETRIES`, `API_BASE_URL`)

**Your Project**:
- Functions: [Your convention]
- Classes: [Your convention]
- Constants: [Your convention]
- Files: [Your convention, e.g., kebab-case, PascalCase]

### Code Organization
**Example**:
```
src/
  ├── components/    # React components
  ├── services/      # Business logic
  ├── utils/         # Helper functions
  └── types/         # TypeScript definitions
```

**Your Project**:
```
[Your directory structure]
```

### Testing Strategy
**Example**: 
- Unit tests: Jest with 80%+ coverage
- Integration tests: Supertest for API endpoints
- Run tests in terminal: `npm test` or inline `node -e "..."`

**Your Project**:
- Unit tests: [Framework and coverage target]
- Integration tests: [Approach]
- Test commands: [How to run tests]

### Documentation Requirements
**Example**: 
- JSDoc for all exported functions
- Inline comments for complex logic (>10 lines)
- README updated for new features

**Your Project**:
- Function docs: [Your style, e.g., JSDoc, docstrings, none]
- Inline comments: [When required]
- README updates: [When needed]

## Architecture Patterns
<!-- Optional: Only fill if you have specific patterns to enforce -->

**Example**:
- Use Repository pattern for data access
- Controllers handle HTTP, Services handle business logic
- Dependency injection via constructor

**Your Project**:
[Your architectural patterns, or leave empty for flexibility]

## Constraints & Preferences

### Performance
**Example**: 
- API responses <200ms
- Bundle size <500KB
- Database queries use indexes

**Your Project**:
[Your performance requirements, if any]

### Security
**Example**:
- Validate all user inputs
- Use parameterized queries (prevent SQL injection)
- No sensitive data in logs

**Your Project**:
[Your security requirements]

### Dependencies
**Example**:
- Prefer built-in solutions over external libraries
- Keep dependency count low (<20 production deps)
- Use specific versions, not `^` or `~`

**Your Project**:
[Your dependency preferences]

## Context Handoff (Memory Keys)
<!-- Used by coding agent to store/retrieve state between phases -->

- `phase1_architecture`: Component designs from architecture phase
- `phase2_implementation`: Implementation details and validation results  
- `phase3_review`: Code review findings and optimizations
- `archon_project_notes`: Ongoing project notes and learnings

> **Note**: These memory keys enable the orchestrator to coordinate between Research Agent and Coding Agent across multiple sessions.

## Flexibility Notes
<!-- Guidance for agent on when to be flexible vs. strict -->

**Be Strict About**:
- [e.g., Test coverage requirements, naming conventions, permission before changes]

**Be Flexible About**:
- [e.g., Implementation approach, file organization details, comment verbosity]

---

## Quick Start for New Features

1. **Check archon** for relevant project notes and code examples
2. **Check crawl4ai-rag** for official documentation patterns
3. **Use serena** to find integration points in codebase
4. **Ask permission** before implementing
5. **Test in terminal** after each component
6. **Save learnings** back to archon for future reference

## Workspace Documentation (REQUIRED)
**Directory**: `.agent-workspace/coding/`

**Files to maintain**:
- `architecture.md`: Component designs, integration points, exact symbols
- `implementation.md`: File paths, line numbers, functions, imports, hooks, test results

**Format**: Reference exact code locations:
```
File: src/components/Button.tsx:45
Symbol: handleClick
Import: import { useCallback } from 'react'
Hook: useCallback(line 47)
```

**Purpose**: Orchestrator Agent reads these to compare with Research Agent and explain project status in simple English. Always include exact technical references.
