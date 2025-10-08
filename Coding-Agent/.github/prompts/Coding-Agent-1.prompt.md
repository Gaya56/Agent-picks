---
mode: Coding-Agent
tools: ['mcp_serena', 'mcp_filesystem', 'mcp_memory', 'archon', 'mcp_sequential-thinking']
description: 'Phase 1: Analyze architecture, design components, and create implementation plan'
---

# Phase 1: Architecture & Planning

## Objective
Analyze current codebase, integrate Research Agent findings, design architecture, and create detailed implementation plan.

---

## Step 1: Context Retrieval (Research Agent Handoff)

### Task
Retrieve Research Agent outputs from `mcp_memory` to understand tool selection and requirements.

### Required Data
- **`research_decision`**: Selected tool/library with rationale
- **`implementation_plan`**: Installation steps and integration points
- **`code_snippets`**: Example patterns from research

### Success Criteria
- [ ] Research findings loaded and summarized
- [ ] Tool selection confirmed
- [ ] Integration requirements identified

---

## Step 2: Codebase Analysis (Current State)

### Task
Use `mcp_serena` and `mcp_filesystem` to analyze existing architecture and identify integration points.

### Output Requirements
```markdown
### Current Architecture
- **Project Structure**: [directory tree of relevant areas]
- **Key Files**: [list 3-5 main files to modify]
- **Existing Patterns**: [architectural patterns in use]
- **Dependencies**: [relevant current dependencies]

### Integration Points
- **Where to Integrate**: [specific files/modules]
- **Affected Components**: [list components that will change]
- **Dependencies to Add**: [new packages from research]
- **Breaking Changes**: [potential compatibility issues]
```

### Success Criteria
- [ ] Project structure documented
- [ ] Integration points identified in codebase
- [ ] Potential conflicts flagged

---

## Step 3: Knowledge Base Query (Archon Integration)

### Task
Use `archon` to retrieve relevant patterns, examples, and best practices for the selected tool.

### Output Requirements
For the tool from Research Agent:
```markdown
### Knowledge Base Insights

#### Design Patterns (from Archon)
**Query**: "[tool name] design patterns"
- **Pattern 1**: [name] - [1-2 sentence description]
- **Pattern 2**: [name] - [1-2 sentence description]

#### Implementation Examples (from Archon)
**Query**: "[tool name] integration example [language]"
```[language]
[10-15 line code example from Archon]
```

#### Common Pitfalls (from Archon)
**Query**: "[tool name] common mistakes"
- **Pitfall 1**: [description] - **Solution**: [approach]
- **Pitfall 2**: [description] - **Solution**: [approach]
```

### Success Criteria
- [ ] Design patterns retrieved from Archon
- [ ] Code examples identified
- [ ] Pitfalls documented

---

## Step 4: Architecture Design (Component Breakdown)

### Task
Use `mcp_sequential-thinking` to design component architecture and data flow.

### Thinking Process
1. **Break down feature**: Identify sub-components needed
2. **Define interfaces**: Specify APIs between components
3. **Plan data flow**: Map how data moves through system
4. **Consider edge cases**: Error handling, loading states, validation
5. **Optimize for testability**: Ensure components are unit-testable

### Output Requirements
```markdown
### Component Architecture

#### Component 1: [Name]
- **Purpose**: [1-2 sentences]
- **Location**: `[file path]`
- **Dependencies**: [list external and internal deps]
- **Public API**:
  ```[language]
  [Function/class signatures with JSDoc/docstrings]
  ```
- **Testing Strategy**: [unit tests focus area]

#### Component 2: [Name]
[Same structure...]

### Data Flow
```
[ASCII diagram or mermaid showing component interactions]
User → Component A → Component B → API/State
```

### File Changes
- **New Files**:
  - `[path]`: [purpose]
- **Modified Files**:
  - `[path]`: [changes summary]
- **Test Files**:
  - `[path]`: [tests to create]
```

### Success Criteria
- [ ] All components defined with clear responsibilities
- [ ] Interfaces specified
- [ ] Data flow documented
- [ ] Testing strategy outlined

---

## Step 5: Implementation Plan (Task Breakdown)

### Task
Create detailed, ordered task list for Phase 2 implementation.

### Output Requirements
```markdown
### Implementation Tasks

#### Task 1: Setup & Dependencies
- [ ] Install package: `[command]`
- [ ] Update `package.json`/`requirements.txt`
- [ ] Configure tool in `[config file]`
- **Estimated Time**: [X minutes]

#### Task 2: Create [Component Name]
- [ ] Create file: `[path]`
- [ ] Implement: [specific functionality]
- [ ] Add error handling for [scenarios]
- [ ] Write unit tests: [test file path]
- **Estimated Time**: [X minutes]

#### Task 3: Integrate with [Existing System]
- [ ] Modify `[file]`: [specific changes]
- [ ] Update types/interfaces in `[file]`
- [ ] Add integration test
- **Estimated Time**: [X minutes]

[Continue for all tasks...]

### Success Metrics
- **Code Coverage**: Target 80%+ for new code
- **Performance**: [Specific metric, e.g., "<100ms response time"]
- **Bundle Size**: [If web, e.g., "+10KB max increase"]
```

### Success Criteria
- [ ] Tasks ordered by dependency
- [ ] Each task has clear acceptance criteria
- [ ] Time estimates provided
- [ ] Success metrics defined

---

## Phase 1 Deliverables

### Memory Artifacts
1. **`phase1_architecture`**: Complete component design with file structure
2. **`phase1_implementation_tasks`**: Ordered task list for Phase 2
3. **`phase1_to_phase2_context`**: Integration points and dependencies

### Next Phase Handoff
Pass to Phase 2:
- Component specifications with file paths
- Implementation task checklist
- Code examples from Archon
- Testing strategy and success metrics

---

## Constraints & Guidelines
- **Symbolic Analysis**: Use `mcp_serena` to explore codebase, don't read full files
- **Archon Queries**: Targeted queries for specific patterns, not broad searches
- **Incremental Design**: Break complex features into small, testable components
- **Documentation**: Document all architecture decisions for future reference
- **Memory Usage**: Store all design decisions for Phase 2 and orchestrator
