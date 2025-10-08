---
mode: Research-Agent-code
tools: ['mcp_sequential-thinking', 'mcp_memory', 'mcp_serena', 'mcp_filesystem', 'github']
description: 'Phase 3: Make final decision using weighted criteria and create implementation plan with code examples'
---

# Phase 3: Implementation Decision

## Objective
Make final tool selection using decision matrix, generate implementation plan with integration checklist, and provide ready-to-use code examples.

---

## Step 1: Context Retrieval (Phase 2 Handoff)

### Task
Retrieve Phase 1 and Phase 2 findings from `mcp_memory` to understand full evaluation context.

### Required Data
- **`baseline_snapshot`**: Current project architecture
- **`phase2_evaluation`**: Technical assessments of finalists
- **`phase2_comparison_matrix`**: Weighted scores and rankings
- **`phase2_to_phase3_context`**: Top 2-3 finalists with decision criteria

### Success Criteria
- [ ] All previous phase data loaded
- [ ] Top 2-3 finalists confirmed
- [ ] Decision criteria understood

---

## Step 2: Decision Matrix Analysis

### Task
Use `mcp_sequential-thinking` to build weighted decision matrix and evaluate trade-offs.

### Thinking Process
1. **List Decision Factors**: Technical fit, maintenance risk, migration effort, performance impact
2. **Assign Weights**: Based on project priorities from instructions
3. **Score Each Finalist**: Use Phase 2 data
4. **Evaluate Trade-offs**: Consider edge cases and long-term implications
5. **Make Recommendation**: Select winner with clear rationale

### Output Requirements
```markdown
### Decision Matrix - Final Selection

| Criteria | Weight | [Finalist A] | [Finalist B] | [Finalist C] |
|----------|--------|--------------|--------------|--------------|
| **Technical Fit** |  |  |  |  |
| API Compatibility | 25% | [score] × 0.25 = [X] | [score] × 0.25 = [X] | [score] × 0.25 = [X] |
| Integration Complexity | 15% | [score] × 0.15 = [X] | [score] × 0.15 = [X] | [score] × 0.15 = [X] |
| **Maintenance** |  |  |  |  |
| Community Health | 20% | [score] × 0.20 = [X] | [score] × 0.20 = [X] | [score] × 0.20 = [X] |
| Long-term Support | 15% | [score] × 0.15 = [X] | [score] × 0.15 = [X] | [score] × 0.15 = [X] |
| **Implementation** |  |  |  |  |
| Migration Effort | 15% | [score] × 0.15 = [X] | [score] × 0.15 = [X] | [score] × 0.15 = [X] |
| Documentation | 10% | [score] × 0.10 = [X] | [score] × 0.10 = [X] | [score] × 0.10 = [X] |
| **WEIGHTED TOTAL** | 100% | **[X.XX]** | **[X.XX]** | **[X.XX]** |

### Recommendation: [Winner Name]
**Final Score**: [X.XX/10]

**Rationale** (3-5 sentences):
[Explain why this tool won based on weighted criteria, addressing any trade-offs made and how it aligns with project priorities]

**Runner-up**: [Second Place] - [1-2 sentences on when to consider alternative]
```

### Success Criteria
- [ ] Decision matrix completed with weighted scores
- [ ] Winner selected with clear justification
- [ ] Trade-offs documented

---

## Step 3: Implementation Planning

### Task
Use `mcp_serena` and `github` to create detailed implementation plan with integration points.

### Output Requirements
```markdown
## Implementation Plan: [Winning Tool]

### Prerequisites
- [ ] Node.js version: [min version]
- [ ] TypeScript version: [min version if applicable]
- [ ] Other dependencies: [list]

### Installation Steps
```bash
# Step 1: Install package
[installation command]

# Step 2: Install peer dependencies (if any)
[additional commands]

# Step 3: Update configuration
[config file updates]
```

### Integration Checklist
- [ ] **Configuration** - Update `[config file]`:
  ```[language]
  [5-10 lines of config example]
  ```

- [ ] **Setup** - Initialize in `[file path]`:
  ```[language]
  [10-15 lines of initialization code]
  ```

- [ ] **Usage** - Integrate at `[integration point 1]`:
  ```[language]
  [10-15 lines showing typical usage]
  ```

- [ ] **Error Handling** - Add to `[file path]`:
  ```[language]
  [5-10 lines of error handling pattern]
  ```

- [ ] **Testing** - Create test in `[test file]`:
  ```[language]
  [10-15 lines of test example]
  ```

### Migration Considerations
- **Breaking Changes**: [list any breaking changes from current approach]
- **Deprecation Warnings**: [list any features to update]
- **Rollback Plan**: [1-2 sentences on reverting if needed]
```

### Success Criteria
- [ ] Installation steps documented
- [ ] Integration points identified with code
- [ ] Testing approach defined
- [ ] Migration considerations noted

---

## Step 4: Code Examples & Snippets

### Task
Extract and organize ready-to-use code examples from Phase 2 analysis and official docs.

### Output Requirements
```markdown
## Ready-to-Use Code Snippets

### Basic Setup
```[language]
// File: [file path]
[15-20 lines of complete, working setup code]
```

### Common Use Case #1: [Description]
```[language]
// File: [file path]
[15-20 lines of working example]
```

### Common Use Case #2: [Description]
```[language]
// File: [file path]
[15-20 lines of working example]
```

### Advanced Pattern: [Description]
```[language]
// File: [file path]
[15-20 lines of advanced usage]
```

### Testing Example
```[language]
// File: [test file path]
[15-20 lines of test code]
```
```

### Success Criteria
- [ ] 4-5 code examples provided
- [ ] Examples are complete and executable
- [ ] File paths specified for each snippet
- [ ] Comments explain key concepts

---

## Step 5: Risk Assessment & Validation

### Task
Document risks, validation steps, and success metrics for implementation.

### Output Requirements
```markdown
## Risk Assessment

### Technical Risks
| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| [Risk 1] | [Low/Med/High] | [Low/Med/High] | [mitigation strategy] |
| [Risk 2] | [Low/Med/High] | [Low/Med/High] | [mitigation strategy] |

### Validation Steps
- [ ] **Unit Tests**: Ensure [X]% test coverage for new integration
- [ ] **Integration Tests**: Validate [specific integration points]
- [ ] **Performance**: Benchmark [specific metrics]
- [ ] **Build**: Confirm successful build with new dependency

### Success Metrics
- **Bundle Size**: Target [X KB] increase maximum
- **Performance**: [specific metric] within [X]% of baseline
- **Test Coverage**: Maintain [X]% minimum
- **Build Time**: Increase no more than [X] seconds
```

### Success Criteria
- [ ] Risks identified and mitigated
- [ ] Validation steps defined
- [ ] Success metrics established

---

## Phase 3 Deliverables

### Memory Artifacts
1. **`phase3_decision`**: Final selection with weighted score and rationale
2. **`phase3_implementation_plan`**: Complete checklist with code examples
3. **`phase3_validation_criteria`**: Success metrics and testing approach

### Final Output Summary
```markdown
# Research Complete: [Winning Tool] Selected

## Executive Summary
[3-4 sentences summarizing the entire research process and final recommendation]

## Quick Start
1. Install: `[command]`
2. Configure: Update `[file]`
3. Integrate: Follow implementation checklist above
4. Validate: Run tests and performance benchmarks

## Key Resources
- **Documentation**: [official docs URL]
- **GitHub**: [repo URL]
- **Migration Guide**: [URL if applicable]
- **Community**: [Discord/Slack/Forum URL]

## Next Steps
- [ ] Review implementation plan with team
- [ ] Schedule implementation sprint
- [ ] Set up monitoring for success metrics
- [ ] Plan rollback strategy if needed
```

---

## Constraints & Guidelines
- **Token Budget**: 150-200 words per section
- **Code Snippets**: 15-20 lines for implementation examples
- **Decision Rationale**: Must reference weighted matrix scores
- **Validation**: Must include measurable success criteria
- **Memory Usage**: Store final decision and plan
- **Sequential Thinking**: Use for complex trade-off analysis
