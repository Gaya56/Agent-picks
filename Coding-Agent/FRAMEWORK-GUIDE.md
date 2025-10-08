# Coding Agent Framework Guide

## Overview
The Coding Agent is a multi-phase development assistant that transforms research findings into production-ready code. It follows a structured workflow: Architecture → Implementation → Review.

## Framework Structure

```
Coding-Agent/
├── .github/
│   ├── chatmodes/
│   │   └── Coding-Agent.chatmode.md          # Agent behavior & tools
│   ├── instructions/
│   │   └── Coding-Agent.instructions.md      # Development standards
│   └── prompts/
│       ├── Coding-Agent-1.prompt.md          # Phase 1: Architecture
│       ├── Coding-Agent-2.prompt.md          # Phase 2: Implementation
│       └── Coding-Agent-3.prompt.md          # Phase 3: Review
├── FRAMEWORK-GUIDE.md                         # This file
├── VALIDATION-CHECKLIST.md                    # Validation guide
├── ARCHON-INTEGRATION.md                      # Archon tool guide
└── README.md                                  # Quick start guide
```

## Component Descriptions

### 1. Chat Mode (`Coding-Agent.chatmode.md`)
**Purpose**: Defines agent behavior, response style, and available tools.

**Key Features**:
- 6 MCP tools: memory, filesystem, serena (symbolic code), github, archon (knowledge), sequential-thinking
- Concise, executable responses (150-200 words)
- Validation before execution
- Phase-specific focus areas

**When to Use**: Active throughout all phases

### 2. Instructions (`Coding-Agent.instructions.md`)
**Purpose**: Project-specific development standards and workflow templates.

**Key Sections**:
- Development Objectives: Fill in project goals
- Current Stack: Document technologies
- Architecture Standards: Design patterns, code organization
- Implementation Guidelines: Testing strategy, development workflow
- Code Quality: Testing, error handling, documentation standards
- Review Criteria: Quality gates
- Context Handoff Protocol: Memory keys for orchestrator

**When to Update**: At project start and when standards evolve

### 3. Phase 1: Architecture & Planning (`Coding-Agent-1.prompt.md`)
**Purpose**: Analyze codebase, integrate research findings, design components.

**Workflow**:
1. **Context Retrieval**: Load Research Agent findings from memory
2. **Codebase Analysis**: Use serena to map existing architecture
3. **Knowledge Query**: Use archon for design patterns/best practices
4. **Architecture Design**: Design components with sequential thinking
5. **Implementation Plan**: Create ordered task list for Phase 2

**Outputs**:
- Component specifications with interfaces
- File structure plan
- Implementation task checklist
- Testing strategy

**Memory Keys**: `phase1_architecture`, `phase1_implementation_tasks`, `phase1_to_phase2_context`

### 4. Phase 2: Implementation & Testing (`Coding-Agent-2.prompt.md`)
**Purpose**: Execute architecture plan, write production code with tests.

**Workflow**:
1. **Context Handoff**: Load Phase 1 architecture and tasks
2. **Environment Setup**: Install dependencies, configure tools
3. **Core Implementation**: Implement components one at a time
4. **Integration & Testing**: Connect components, write integration tests inside the terminal 
5. **Code Quality**: Ensure coverage, documentation, linting
6. **Validation**: Final checks before commit

**Outputs**:
- Production code (≥80% test coverage)
- Unit and integration tests
- Updated documentation
- Git commit(s)

**Memory Keys**: `phase2_implementation`, `phase2_test_results`, `phase2_to_phase3_context`

### 5. Phase 3: Review, Optimization & Validation (`Coding-Agent-3.prompt.md`)
**Purpose**: Review implementation, optimize, ensure production readiness.

**Workflow**:
1. **Context Handoff**: Load Phase 2 implementation and results
2. **Code Review**: Verify alignment with Phase 1 architecture
3. **Performance Analysis**: Identify optimization opportunities
4. **Refactoring**: Implement high-priority optimizations
5. **Final Validation**: Production readiness checklist
6. **Summary & Handoff**: Comprehensive session summary

**Outputs**:
- Optimized code
- Performance improvements
- Production readiness report
- Session summary for orchestrator

**Memory Keys**: `phase3_review_summary`, `phase3_optimizations`, `coding_session_summary`, `production_checklist`

## Key Features

### 🔗 Memory-Based Handoffs
- Each phase stores outputs in `mcp_memory` for next phase
- Orchestrator can retrieve `coding_session_summary` to alternate with Research Agent
- Enables long-running, multi-session workflows

### 🎯 Token Efficiency
- Uses `mcp_serena` for symbolic code analysis (read only what's needed)
- Structured outputs (150-200 words per section)
- Progressive disclosure (don't read full files unnecessarily)

### 🧠 Knowledge Integration
- **Archon**: Query for design patterns, implementation examples, common pitfalls
- **Sequential Thinking**: Multi-step reasoning for complex decisions
- **GitHub**: Access to repository context

### 🔄 Iterative Workflow
- Phase 1 → design → Phase 2 → implement → Phase 3 → optimize
- Each phase validates previous phase outputs
- Can loop back if issues found

### 📊 Quality Gates
- 80%+ test coverage requirement
- Production readiness checklist
- Performance benchmarks
- Security validation

## Usage Instructions

### Initial Setup
1. **Fill out `Coding-Agent.instructions.md`**:
   - Add project name, goals, constraints
   - Document tech stack (languages, frameworks, libraries)
   - Define code quality standards
   - Set architecture patterns

2. **Activate Coding-Agent Mode**:
   - In VS Code Copilot Chat: Select "Coding-Agent" mode
   - Or: Reference `@workspace /Coding-Agent` in prompt

### Phase 1: Architecture
```
@workspace Use Coding-Agent-1.prompt.md to design architecture for [feature]
```

**Expects**: Research Agent has already selected tool/library in memory
**Produces**: Component design, implementation plan

### Phase 2: Implementation
```
@workspace Use Coding-Agent-2.prompt.md to implement the architecture
```

**Expects**: Phase 1 architecture in memory
**Produces**: Production code with tests

### Phase 3: Review
```
@workspace Use Coding-Agent-3.prompt.md to review and optimize
```

**Expects**: Phase 2 implementation in memory
**Produces**: Optimized code, production report

### Orchestrator Integration
The orchestrator alternates between Research Agent and Coding Agent:

```
Research Agent → finds best tool → stores decision in memory
     ↓
Coding Agent Phase 1 → retrieves decision → designs architecture
     ↓
Coding Agent Phase 2 → implements code
     ↓
Coding Agent Phase 3 → optimizes and validates
     ↓
(Next cycle if needed)
```

## MCP Tools Reference

### Core Tools (Used in All Phases)
- **`mcp_memory`**: Store/retrieve context between phases and agents
- **`mcp_filesystem`**: Create, read, write files
- **`mcp_serena`**: Symbolic code analysis (find_symbol, find_referencing_symbols, etc.)
- **`mcp_sequential-thinking`**: Multi-step reasoning for complex decisions

### Specialized Tools
- **`archon`**: Query knowledge base for code patterns, examples, best practices
  - Phase 1: Design patterns, architecture examples
  - Phase 2: Implementation examples, error handling patterns
  - Phase 3: Optimization techniques, refactoring patterns

- **`github`**: Repository operations
  - Access PR context
  - Retrieve file history
  - Check CI/CD status

## Best Practices

### 1. Always Start with Context
- Load memory artifacts from previous phases
- Review Research Agent decision before architecture
- Understand existing codebase before implementation

### 2. Use Symbolic Analysis
- Use `mcp_serena` to explore code symbolically
- Don't read full files unless necessary
- Find symbols, analyze references, then read targeted sections

### 3. Query Archon Strategically
- Specific queries: "React useEffect cleanup pattern"
- Not broad queries: "React best practices"
- Use for unfamiliar patterns or optimization techniques

### 4. Incremental Implementation
- Implement one component at a time
- Test after each component
- Don't move to next component until current one works

### 5. Store Everything in Memory
- Save all design decisions
- Store performance benchmarks
- Document trade-offs for future reference

### 6. Quality Over Speed
- Don't skip tests
- Ensure ≥80% coverage
- Complete production checklist

## Troubleshooting

### Issue: Phase can't find previous phase outputs
**Solution**: Check memory keys in previous phase. Ensure memory artifacts were stored.

### Issue: Archon queries return no results
**Solution**: Make queries more specific. Include tool/library name and specific technique.

### Issue: Serena symbolic analysis fails
**Solution**: Ensure files exist, use `list_dir` first, check file paths are absolute.

### Issue: Tests failing after optimization
**Solution**: Revert optimization, verify tests pass, then re-apply incrementally.

### Issue: Implementation diverges from architecture
**Solution**: Return to Phase 1, update architecture, then continue Phase 2 with new plan.

## Advanced Usage

### Custom Phases
You can create custom phases for specific workflows:
- `Coding-Agent-Refactor.prompt.md`: Pure refactoring workflow
- `Coding-Agent-Debug.prompt.md`: Debugging and bug fixing
- `Coding-Agent-Migration.prompt.md`: Code migration tasks

### Multi-Agent Workflows
Combine with other agents:
1. Research Agent → finds tool
2. Coding Agent → implements tool
3. Testing Agent → comprehensive testing
4. Documentation Agent → writes docs

### Memory Snapshots
Create memory snapshots at key milestones:
```markdown
# Store milestone
mcp_memory.create_entities([
  {
    name: "milestone_v1_complete",
    entityType: "milestone",
    observations: ["All Phase 3 validation passed", "Ready for deployment"]
  }
])
```

## Next Steps

1. **Validate Framework**: Use `VALIDATION-CHECKLIST.md`
2. **Integrate Archon**: Follow `ARCHON-INTEGRATION.md`
3. **Run First Workflow**: Use Research Agent → Coding Agent flow
4. **Iterate**: Refine instructions based on project needs
