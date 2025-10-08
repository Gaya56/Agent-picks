# Research Agent Framework - Scaffold Summary

## Framework Overview
This directory contains a complete, token-efficient Research Agent framework for GitHub Copilot, designed to support multi-phase research across different projects.

## Component Structure

### 1. Chat Mode
**File**: `.github/chatmodes/Research-Agent-code.chatmode.md`
- **Purpose**: Defines agent behavior, response style, and available tools per phase
- **Tools**: `mcp_memory`, `mcp_filesystem`, `mcp_serena`, `github`, `mcp_context7`, `mcp_sequential-thinking`
- **Key Features**: 
  - Phase-specific tool allocation
  - Token efficiency constraints (150-200 words per section)
  - Progressive narrowing workflow (8 → 4 → 3 candidates)

### 2. Instructions
**File**: `.github/instructions/Research-Instructions.instructions.md`
- **Purpose**: Project context, coding guidelines, and evaluation criteria
- **Key Sections**:
  - Research objectives template
  - Current stack inventory
  - Token efficiency standards
  - Evaluation criteria with weights
  - Decision matrix template
  - Context handoff protocol
  - Response format standards

### 3. Prompts (3 Sequential Phases)

#### Phase 1: Discovery
**File**: `.github/prompts/Phase-1-Research.prompt.md`
- **Objective**: Discover 5-8 candidates → narrow to top 3-4
- **Steps**:
  1. Baseline analysis (current project state)
  2. Candidate discovery (GitHub search)
  3. Documentation preview (quick assessment)
  4. Narrowing to finalists (scoring matrix)
- **Deliverables**: `baseline_snapshot`, `phase1_candidates`, `phase1_to_phase2_context`

#### Phase 2: Evaluation
**File**: `.github/prompts/Phase-2-Research.prompt.md`
- **Objective**: Deep evaluation of 3-4 candidates → narrow to top 2-3
- **Steps**:
  1. Context retrieval (Phase 1 handoff)
  2. API compatibility analysis
  3. Community & maintenance analysis
  4. Advanced code pattern analysis
  5. Comparison matrix & finalist selection
- **Deliverables**: `phase2_evaluation`, `phase2_comparison_matrix`, `phase2_to_phase3_context`

#### Phase 3: Implementation
**File**: `.github/prompts/Phase-3-Research.prompt.md`
- **Objective**: Final decision + implementation plan with code
- **Steps**:
  1. Context retrieval (Phase 1 & 2 handoff)
  2. Decision matrix analysis (weighted scoring)
  3. Implementation planning (checklist + integration points)
  4. Code examples & snippets (ready-to-use)
  5. Risk assessment & validation
- **Deliverables**: `phase3_decision`, `phase3_implementation_plan`, `phase3_validation_criteria`

## Key Design Principles

### Token Efficiency
- **Summaries**: 150-200 words per section
- **Code Snippets**: 10-20 lines maximum
- **Symbolic Analysis**: Use `mcp_serena` before full file reads
- **Targeted Docs**: Request specific sections from `mcp_context7`

### Context Continuity
- **Memory Keys**: Standardized naming (`baseline_snapshot`, `phase1_candidates`, etc.)
- **Handoff Protocol**: Each phase passes top candidates + context to next
- **Progressive Storage**: Store findings incrementally in `mcp_memory`

### Modular Reusability
- **Customizable**: Instructions template for project-specific requirements
- **Tool Distribution**: Phase-specific tool allocation (<75 tools per phase)
- **Format Standards**: Consistent markdown templates across phases

## Usage Workflow

1. **Setup**: Customize `Research-Instructions.instructions.md` with project specifics
2. **Phase 1**: Run `Phase-1-Research.prompt.md` to discover candidates
3. **Phase 2**: Run `Phase-2-Research.prompt.md` to evaluate finalists
4. **Phase 3**: Run `Phase-3-Research.prompt.md` to decide and plan implementation

## Best Practices Alignment

✅ **VS Code Standards**:
- YAML front matter for metadata
- `applyTo: '**'` for universal instructions
- `mode:` specification in prompts
- `tools:` array in chat modes and prompts

✅ **Token Optimization**:
- Section-based organization
- Placeholder templates
- Targeted tool usage
- Progressive disclosure

✅ **GitHub Copilot Integration**:
- MCP tool references (`mcp_*`)
- Context variables (`#codebase`, `#file`)
- Memory-based state management
- Agent mode compatibility

## Next Steps

To use this framework:
1. Fill in project-specific details in `Research-Instructions.instructions.md`
2. Specify research objectives and current stack
3. Adjust evaluation criteria weights if needed
4. Run Phase 1 prompt to begin research workflow
5. Follow handoff protocol between phases
6. Store all findings in memory for future reference

---

**Framework Version**: 1.0  
**Last Updated**: 2025-10-08  
**Compatible With**: GitHub Copilot Chat (VS Code)
