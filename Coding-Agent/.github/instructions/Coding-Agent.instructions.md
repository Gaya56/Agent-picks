---
applyTo: '**'
---

# Coding Agent Instructions

## Project Context
<!-- Provide high-level overview of coding goals and constraints -->

### Development Objectives
- [ ] Implement features from [SPECIFY SOURCE: Research Agent findings]
- [ ] Maintain code quality standards for [SPECIFY CODEBASE]
- [ ] Integrate with existing architecture at [SPECIFY INTEGRATION POINTS]

### Current Codebase
<!-- List current technologies, structure, and patterns -->
- **Language/Framework**: [e.g., TypeScript/React, Python/FastAPI]
- **Architecture**: [e.g., MVC, microservices, monorepo]
- **Testing**: [e.g., Jest, Pytest, Playwright]
- **Key Patterns**: [e.g., dependency injection, factory pattern]

## Coding Guidelines

### Code Quality Standards
- **Readability**: Use `mcp_serena` symbolic tools for precise edits
- **Testing**: Write tests inside the terminal alongside implementation (TDD when possible)
- **Documentation**: Inline comments for complex logic, README for setup
- **Error Handling**: Try-catch blocks, proper logging, user-friendly messages

### Development Workflow
- **Phase 1**: Architecture → Design decisions → Component breakdown
- **Phase 2**: Implementation → Unit tests → Integration tests  
- **Phase 3**: Code review → Optimization → Documentation

### Integration with Research Agent
<!-- Define how to consume Research Agent outputs -->
- **Memory Keys**: `research_decision`, `implementation_plan`, `code_snippets`
- **Archon Integration**: Query knowledge base for patterns from researched tools
- **Handoff Protocol**: Retrieve tool selection → Apply patterns → Store results

## Architecture Patterns

### Component Design
- **Modularity**: Single responsibility, loose coupling
- **Reusability**: Extract common patterns to utilities
- **Testability**: Dependency injection, pure functions
- **Scalability**: Consider performance implications

### File Organization Template
```
src/
  components/     # UI components (if applicable)
  services/       # Business logic
  utils/          # Helper functions
  types/          # Type definitions
  tests/          # Test files (mirror src structure)
  config/         # Configuration files
```

## Testing Requirements

### Test Coverage
- **Unit Tests**: 80% minimum coverage for business logic
- **Integration Tests**: API endpoints, component interactions
- **E2E Tests**: Critical user flows (optional)

### Test Structure Template
```[language]
describe('[Component/Function Name]', () => {
  it('should [expected behavior]', () => {
    // Arrange: Setup
    // Act: Execute
    // Assert: Verify
  });
});
```

## Error Handling Standards

### Defensive Programming
```[language]
try {
  // Primary logic
  validateInput(data);
  const result = await processData(data);
  return result;
} catch (error) {
  logger.error('Process failed', { error, context: data });
  throw new CustomError('User-friendly message', error);
}
```

### Logging Levels
- **DEBUG**: Development details
- **INFO**: Business events
- **WARN**: Recoverable issues
- **ERROR**: Failures requiring attention

## Context Handoff Protocol

### Memory Keys (Phase-to-Phase)
- `phase1_architecture`: Design decisions and component structure
- `phase2_implementation`: Code changes and test results
- `phase3_review`: Optimization suggestions and final code

### Memory Keys (Orchestrator Integration)
- `research_to_coding`: Tool selection, implementation checklist from Research Agent
- `coding_to_orchestrator`: Implementation status, next actions

### Between-Phase Data Flow
1. **Phase 1 → Phase 2**: Architecture design → Implementation tasks
2. **Phase 2 → Phase 3**: Implementation → Review checklist
3. **Phase 3 → Orchestrator**: Final code → Deployment readiness

## Response Format Standards

### Architecture Output (Phase 1)
```markdown
## Component: [Name]
- **Purpose**: [1-2 sentences]
- **Dependencies**: [list]
- **API Surface**: [key methods/props]
- **Testing Strategy**: [approach]
```

### Implementation Output (Phase 2)
```markdown
## File: [path]
```[language]
[Complete, working code with comments]
```

## Test: [path]
```[language]
[Test code covering main scenarios]
```
```

### Review Output (Phase 3)
```markdown
## Optimization: [Area]
- **Current**: [issue description]
- **Improvement**: [suggested change]
- **Impact**: [performance/readability/maintainability]
- **Priority**: [High/Medium/Low]
```

## Archon Knowledge Base Usage

### Query Patterns
- **Design Patterns**: "factory pattern implementation in [language]"
- **Best Practices**: "[framework] error handling patterns"
- **Code Examples**: "[library] async/await usage"

### Storage Patterns
- Store architecture decisions with context
- Save reusable code snippets with tags
- Document integration patterns for future reference

## Constraints and Limitations
- **No breaking changes**: Flag compatibility issues upfront
- **Incremental development**: Small, testable changes
- **Documentation required**: Update README for new features
- **Performance consideration**: Profile before optimizing
