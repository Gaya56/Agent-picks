# Coding Agent Framework Validation Checklist

## Part 1: File-by-File Validation

### 1. Chat Mode File (`.github/chatmodes/Coding-Agent.chatmode.md`)

#### ✅ YAML Front Matter
- [ ] `description` field present and clear
- [ ] `tools` array contains all required MCP tools:
  - [ ] `mcp_memory` (context handoffs)
  - [ ] `mcp_filesystem` (file operations)
  - [ ] `mcp_serena` (symbolic code analysis)
  - [ ] `github` (repository access)
  - [ ] `archon` (knowledge engine)
  - [ ] `mcp_sequential-thinking` (reasoning)
- [ ] Tools array has ≤128 tools
- [ ] YAML properly formatted (no syntax errors)

#### ✅ Content Structure
- [ ] **Response Style** section (150-200 words)
  - [ ] Concise, executable guidance
  - [ ] Structured sections (not prose)
  - [ ] Clear action items
- [ ] **Behavioral Constraints** section
  - [ ] Validation before execution
  - [ ] Symbolic analysis first (don't read full files)
  - [ ] Memory storage requirements
  - [ ] Error handling expectations
- [ ] **Phase-Specific Focus** section
  - [ ] Phase 1: Architecture and planning
  - [ ] Phase 2: Implementation and testing
  - [ ] Phase 3: Review and optimization

#### ✅ Token Efficiency
- [ ] Response style emphasizes brevity
- [ ] Instructs to use serena for symbolic analysis
- [ ] Discourages reading full files
- [ ] Emphasizes progressive disclosure

### 2. Instructions File (`.github/instructions/Coding-Agent.instructions.md`)

#### ✅ YAML Front Matter
- [ ] `applyTo: '**'` directive present
- [ ] YAML properly formatted

#### ✅ Section: Development Objectives
- [ ] Project name placeholder: `[Project Name]`
- [ ] Goals placeholder: `[Key objectives]`
- [ ] Constraints placeholder: `[Limitations, dependencies]`
- [ ] Clear fill-in structure

#### ✅ Section: Current Stack
- [ ] Languages placeholder: `[e.g., TypeScript, Python]`
- [ ] Frameworks placeholder: `[e.g., React, Django]`
- [ ] Libraries placeholder: `[Key dependencies]`
- [ ] Build Tools placeholder: `[e.g., Webpack, npm]`
- [ ] Testing placeholder: `[Jest, pytest, etc.]`

#### ✅ Section: Architecture Standards
- [ ] Design patterns placeholder
- [ ] Code organization structure
- [ ] Dependency management guidelines
- [ ] Module boundaries description

#### ✅ Section: Implementation Guidelines
- [ ] Development workflow defined
- [ ] Testing strategy outlined
- [ ] Code review process mentioned

#### ✅ Section: Code Quality
- [ ] Testing standards (≥80% coverage)
- [ ] Error handling patterns
- [ ] Documentation standards
- [ ] Code style guidelines

#### ✅ Section: Review Criteria
- [ ] Functionality checklist
- [ ] Performance benchmarks
- [ ] Security considerations
- [ ] Documentation completeness

#### ✅ Section: Context Handoff Protocol
- [ ] Memory key definitions:
  - [ ] `phase1_*` keys for architecture
  - [ ] `phase2_*` keys for implementation
  - [ ] `phase3_*` keys for review
  - [ ] `coding_session_summary` for orchestrator
- [ ] Handoff format templates

### 3. Phase 1 Prompt (`.github/prompts/Coding-Agent-1.prompt.md`)

#### ✅ YAML Front Matter
- [ ] `mode: Coding-Agent`
- [ ] `tools` array present with Phase 1 tools:
  - [ ] `mcp_serena`
  - [ ] `mcp_filesystem`
  - [ ] `mcp_memory`
  - [ ] `archon`
  - [ ] `mcp_sequential-thinking`
- [ ] `description` field clear: Architecture phase

#### ✅ Step 1: Context Retrieval
- [ ] Retrieves Research Agent memory keys
- [ ] Lists required data (research_decision, implementation_plan, code_snippets)
- [ ] Success criteria defined

#### ✅ Step 2: Codebase Analysis
- [ ] Uses serena for symbolic analysis
- [ ] Output requirements specified (architecture, integration points)
- [ ] Success criteria defined

#### ✅ Step 3: Knowledge Base Query
- [ ] Uses archon for patterns
- [ ] Query templates provided
- [ ] Output format specified (design patterns, examples, pitfalls)
- [ ] Success criteria defined

#### ✅ Step 4: Architecture Design
- [ ] Uses sequential thinking
- [ ] Thinking process outlined (5 steps)
- [ ] Output requirements specified (components, data flow, file changes)
- [ ] Success criteria defined

#### ✅ Step 5: Implementation Plan
- [ ] Creates ordered task list
- [ ] Output requirements specified (tasks with estimates)
- [ ] Success metrics defined (coverage, performance, bundle size)
- [ ] Success criteria defined

#### ✅ Phase 1 Deliverables
- [ ] Memory artifacts listed (3 keys)
- [ ] Next phase handoff described

#### ✅ Constraints & Guidelines
- [ ] Symbolic analysis emphasized
- [ ] Archon usage guidelines
- [ ] Incremental design approach
- [ ] Documentation requirements
- [ ] Memory storage requirements

### 4. Phase 2 Prompt (`.github/prompts/Coding-Agent-2.prompt.md`)

#### ✅ YAML Front Matter
- [ ] `mode: Coding-Agent`
- [ ] `tools` array with Phase 2 tools:
  - [ ] `mcp_serena`
  - [ ] `mcp_filesystem`
  - [ ] `mcp_memory`
  - [ ] `github`
  - [ ] `archon`
  - [ ] `mcp_sequential-thinking`
- [ ] `description` field clear: Implementation phase

#### ✅ Step 1: Context Handoff
- [ ] Retrieves Phase 1 memory keys
- [ ] Lists required data (architecture, tasks, context)
- [ ] Success criteria defined

#### ✅ Step 2: Environment Setup
- [ ] Installation checklist
- [ ] Configuration checklist
- [ ] Documentation checklist
- [ ] Success criteria defined

#### ✅ Step 3: Core Implementation
- [ ] Component-by-component approach
- [ ] Archon query templates for implementation
- [ ] Code templates provided
- [ ] Error handling patterns included
- [ ] Unit test templates provided
- [ ] Implementation order checklist
- [ ] Success criteria defined

#### ✅ Step 4: Integration & Testing
- [ ] Integration checklist
- [ ] Integration test templates
- [ ] Manual testing checklist
- [ ] Success criteria defined

#### ✅ Step 5: Code Quality
- [ ] Code review checklist (type safety, error handling, comments, naming, DRY, SOLID)
- [ ] Test coverage requirements (≥80%)
- [ ] Documentation checklist
- [ ] Linting & formatting checklist
- [ ] Success criteria defined

#### ✅ Step 6: Validation & Pre-Commit
- [ ] Build & test validation
- [ ] Regression testing checklist
- [ ] Git preparation steps
- [ ] Commit message template
- [ ] Success criteria defined

#### ✅ Phase 2 Deliverables
- [ ] Memory artifacts listed (3 keys)
- [ ] Code artifacts listed
- [ ] Next phase handoff described

#### ✅ Constraints & Guidelines
- [ ] Incremental implementation
- [ ] Test-driven approach
- [ ] Archon usage guidelines
- [ ] Symbolic editing emphasis
- [ ] Memory storage requirements
- [ ] Quality over speed principle

### 5. Phase 3 Prompt (`.github/prompts/Coding-Agent-3.prompt.md`)

#### ✅ YAML Front Matter
- [ ] `mode: Coding-Agent`
- [ ] `tools` array with Phase 3 tools (same as Phase 2)
- [ ] `description` field clear: Review phase

#### ✅ Step 1: Context Handoff
- [ ] Retrieves Phase 2 memory keys
- [ ] Lists required data (implementation, test results, context, architecture)
- [ ] Success criteria defined

#### ✅ Step 2: Code Review
- [ ] Architecture alignment checklist
- [ ] Code quality analysis template (per component)
- [ ] Cross-cutting concerns checklist (error handling, logging, security, performance)
- [ ] Success criteria defined

#### ✅ Step 3: Performance Analysis
- [ ] Sequential thinking process (5 steps)
- [ ] Performance review template
- [ ] Optimization opportunity template (name, state, impact, solution, trade-offs, archon query)
- [ ] Prioritization framework (high/medium/low)
- [ ] Success criteria defined

#### ✅ Step 4: Refactoring & Optimization
- [ ] Pre-refactor validation steps
- [ ] Archon query template for optimizations
- [ ] Refactoring template (before/after)
- [ ] Post-refactor validation steps
- [ ] Refactoring checklist
- [ ] Success criteria defined

#### ✅ Step 5: Final Validation
- [ ] Production readiness checklist:
  - [ ] Functionality (requirements, acceptance criteria, bugs, edge cases)
  - [ ] Testing (coverage, integration, manual, regression)
  - [ ] Code quality (linting, formatting, type safety, review)
  - [ ] Documentation (README, API docs, config, examples)
  - [ ] Performance (metrics, no regressions, optimizations)
  - [ ] Security (validation, no sensitive data, no vulnerabilities, safe errors)
  - [ ] Deployment readiness (build, env vars, migration, rollback)
- [ ] Success criteria defined

#### ✅ Step 6: Summary & Handoff
- [ ] Summary report template with:
  - [ ] Overview section
  - [ ] Components implemented
  - [ ] Files changed
  - [ ] Quality metrics
  - [ ] Key decisions
  - [ ] Optimizations applied
  - [ ] Known limitations
  - [ ] Technical debt
  - [ ] Future enhancements
  - [ ] Usage example
  - [ ] Next steps
- [ ] Success criteria defined

#### ✅ Phase 3 Deliverables
- [ ] Memory artifacts listed (4 keys)
- [ ] Code artifacts listed
- [ ] Orchestrator handoff described

#### ✅ Constraints & Guidelines
- [ ] No premature optimization
- [ ] Preserve tests requirement
- [ ] Document trade-offs
- [ ] Archon usage for optimizations
- [ ] Memory storage for handoff
- [ ] Production focus principle

---

## Part 2: Cross-File Validation

### Memory Key Consistency
- [ ] Phase 1 outputs match Phase 2 inputs
- [ ] Phase 2 outputs match Phase 3 inputs
- [ ] All memory keys follow naming convention: `phase[N]_[descriptor]`
- [ ] Orchestrator handoff keys documented consistently

### Tool Usage Consistency
- [ ] All phases reference same MCP tool names
- [ ] Tool usage matches tool capabilities
- [ ] No reference to undefined tools

### Workflow Coherence
- [ ] Phase 1 → Phase 2 handoff is clear
- [ ] Phase 2 → Phase 3 handoff is clear
- [ ] Phase 3 → Orchestrator handoff is clear
- [ ] Each phase can resume from memory

### Output Format Consistency
- [ ] All phases use similar output templates
- [ ] Checklists follow same format
- [ ] Success criteria consistently defined
- [ ] Memory artifacts consistently structured

### Documentation Accuracy
- [ ] Instructions match chat mode capabilities
- [ ] Prompts reference correct memory keys
- [ ] FRAMEWORK-GUIDE.md describes actual structure
- [ ] ARCHON-INTEGRATION.md matches prompt usage

---

## Part 3: Enhancement Opportunities

### Dynamic Tool Selection
Consider implementing:
- [ ] Conditional tool loading based on project type
- [ ] Language-specific tool sets
- [ ] Optional tools for advanced workflows

### Additional Workflows
Consider creating:
- [ ] `Coding-Agent-Refactor.prompt.md` for pure refactoring
- [ ] `Coding-Agent-Debug.prompt.md` for debugging
- [ ] `Coding-Agent-Migration.prompt.md` for code migrations
- [ ] `Coding-Agent-Hotfix.prompt.md` for urgent fixes

### Enhanced Metadata
Consider adding:
- [ ] `estimatedTime` field per phase
- [ ] `complexity` levels (simple/medium/complex)
- [ ] `requiredSkills` field
- [ ] `prerequisites` field

### Quality Improvements
- [ ] Add performance benchmarking templates
- [ ] Include security scanning checklists
- [ ] Add accessibility validation (if web)
- [ ] Include dependency vulnerability checks

### Collaboration Features
- [ ] Team handoff templates
- [ ] PR description generators
- [ ] Code review checklist exports
- [ ] Documentation auto-generation

---

## Part 4: Integration Testing

### Test 1: Research → Coding Agent Handoff
- [ ] Research Agent stores decision in memory
- [ ] Coding Agent Phase 1 retrieves decision
- [ ] All required fields present
- [ ] Handoff successful

### Test 2: Phase 1 → Phase 2 Handoff
- [ ] Phase 1 stores architecture in memory
- [ ] Phase 2 retrieves architecture
- [ ] All required fields present (components, tasks, context)
- [ ] Handoff successful

### Test 3: Phase 2 → Phase 3 Handoff
- [ ] Phase 2 stores implementation in memory
- [ ] Phase 3 retrieves implementation
- [ ] All required fields present (code, tests, context)
- [ ] Handoff successful

### Test 4: Phase 3 → Orchestrator Handoff
- [ ] Phase 3 stores session summary in memory
- [ ] Orchestrator can retrieve summary
- [ ] Summary contains all required sections
- [ ] Handoff successful

### Test 5: Archon Integration
- [ ] Phase 1 can query Archon for design patterns
- [ ] Phase 2 can query Archon for implementation examples
- [ ] Phase 3 can query Archon for optimization techniques
- [ ] Archon responses are properly formatted and usable

### Test 6: Serena Integration
- [ ] Can use `find_symbol` to locate code
- [ ] Can use `find_referencing_symbols` to map dependencies
- [ ] Can use symbolic editing tools
- [ ] Symbolic analysis is token-efficient

### Test 7: End-to-End Workflow
- [ ] Complete Phase 1: Architecture generated
- [ ] Complete Phase 2: Code implemented with tests
- [ ] Complete Phase 3: Code reviewed and optimized
- [ ] Production checklist passes
- [ ] Final summary generated

---

## Part 5: Validation Commands

### File Existence Check
```bash
# Check all required files exist
ls -la /workspaces/Agent-picks/Coding-Agent/.github/chatmodes/Coding-Agent.chatmode.md
ls -la /workspaces/Agent-picks/Coding-Agent/.github/instructions/Coding-Agent.instructions.md
ls -la /workspaces/Agent-picks/Coding-Agent/.github/prompts/Coding-Agent-1.prompt.md
ls -la /workspaces/Agent-picks/Coding-Agent/.github/prompts/Coding-Agent-2.prompt.md
ls -la /workspaces/Agent-picks/Coding-Agent/.github/prompts/Coding-Agent-3.prompt.md
ls -la /workspaces/Agent-picks/Coding-Agent/FRAMEWORK-GUIDE.md
ls -la /workspaces/Agent-picks/Coding-Agent/ARCHON-INTEGRATION.md
ls -la /workspaces/Agent-picks/Coding-Agent/VALIDATION-CHECKLIST.md
ls -la /workspaces/Agent-picks/Coding-Agent/README.md
```

### YAML Validation
```bash
# Install yamllint if not present
# pip install yamllint

# Validate YAML front matter
yamllint /workspaces/Agent-picks/Coding-Agent/.github/chatmodes/Coding-Agent.chatmode.md
yamllint /workspaces/Agent-picks/Coding-Agent/.github/instructions/Coding-Agent.instructions.md
yamllint /workspaces/Agent-picks/Coding-Agent/.github/prompts/*.prompt.md
```

### Markdown Validation
```bash
# Install markdownlint if not present
# npm install -g markdownlint-cli

# Validate markdown formatting
markdownlint /workspaces/Agent-picks/Coding-Agent/**/*.md
```

### Word Count Validation
```bash
# Check section sizes (should be 150-200 words per section)
# This is manual - review each section in files

# Check total file sizes (should be reasonable)
wc -w /workspaces/Agent-picks/Coding-Agent/.github/chatmodes/Coding-Agent.chatmode.md
wc -w /workspaces/Agent-picks/Coding-Agent/.github/instructions/Coding-Agent.instructions.md
wc -w /workspaces/Agent-picks/Coding-Agent/.github/prompts/*.prompt.md
```

### Memory Key Search
```bash
# Find all memory key references
grep -r "phase1_" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "phase2_" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "phase3_" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "coding_session_summary" /workspaces/Agent-picks/Coding-Agent/.github/
```

### Tool Reference Search
```bash
# Find all tool references
grep -r "mcp_memory" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "mcp_filesystem" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "mcp_serena" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "archon" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "github" /workspaces/Agent-picks/Coding-Agent/.github/
grep -r "mcp_sequential-thinking" /workspaces/Agent-picks/Coding-Agent/.github/
```

---

## Priority Action Items

### 🔴 Critical (Do Before Using Framework)
1. [ ] Fill out `Coding-Agent.instructions.md` with project specifics
2. [ ] Verify Archon is installed and accessible
3. [ ] Test Research → Coding Agent memory handoff
4. [ ] Run Phase 1 on simple feature to validate

### 🟡 Important (Do Within First Week)
1. [ ] Complete all validation checklist items above
2. [ ] Run full 3-phase workflow on real feature
3. [ ] Document project-specific patterns in memory
4. [ ] Create team onboarding guide

### 🟢 Enhancement (Do When Established)
1. [ ] Create custom workflow prompts (refactor, debug, etc.)
2. [ ] Build pattern library from Archon queries
3. [ ] Implement dynamic tool selection
4. [ ] Add project-specific quality gates

---

## Validation Sign-Off

- [ ] **Part 1 Complete**: All individual files validated
- [ ] **Part 2 Complete**: Cross-file consistency verified
- [ ] **Part 3 Complete**: Enhancement opportunities identified
- [ ] **Part 4 Complete**: Integration tests passed
- [ ] **Part 5 Complete**: Validation commands executed
- [ ] **Framework Ready**: Signed off for production use

**Validated By**: _______________  
**Date**: _______________  
**Notes**: _______________
