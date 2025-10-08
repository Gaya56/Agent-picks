---
applyTo: '**'
---

# Research Agent Instructions

## Project Context
<!-- Provide high-level overview of research goals and constraints -->

### Research Objectives
- [ ] Discover tools/libraries for [SPECIFY DOMAIN]
- [ ] Evaluate compatibility with [SPECIFY STACK]
- [ ] Implement integration with [SPECIFY ARCHITECTURE]

### Current Stack
<!-- List current technologies, versions, and constraints -->
- **Language/Framework**: [e.g., React 18, Node.js 20]
- **Build Tools**: [e.g., Vite, Webpack]
- **Key Dependencies**: [e.g., TypeScript 5.x, Express 4.x]

## Coding Guidelines

### Token Efficiency Standards
- **File Reading**: Use `mcp_serena` symbolic tools before full reads
- **Code Snippets**: Extract 10-15 lines maximum per example
- **Documentation**: Summarize in 150-200 words per section
- **Memory Usage**: Store only actionable findings

### Search and Discovery Patterns
- **Phase 1**: GitHub search → 5-8 candidates → top 3-4 advance
- **Phase 2**: Deep evaluation → comparison matrix → top 2-3 finalists
- **Phase 3**: Decision matrix → implementation checklist → code snippets

### Integration Requirements
<!-- Define architecture and compatibility constraints -->
- **API Style**: [e.g., REST, GraphQL, gRPC]
- **State Management**: [e.g., Redux, Zustand, Context API]
- **Testing Framework**: [e.g., Jest, Vitest, Playwright]
- **Build Requirements**: [e.g., ESM only, CommonJS support]

## Evaluation Criteria

### Technical Assessment
- **Maturity**: Stars, releases, last update (weight: 20%)
- **Community**: Contributors, issues, response time (weight: 15%)
- **Documentation**: API docs, examples, migration guides (weight: 20%)
- **Compatibility**: Version requirements, breaking changes (weight: 25%)
- **Performance**: Bundle size, benchmarks, optimization (weight: 20%)

### Decision Matrix Template
| Criteria | Weight | Candidate A | Candidate B | Candidate C |
|----------|--------|-------------|-------------|-------------|
| Maturity | 20% | [SCORE] | [SCORE] | [SCORE] |
| Community | 15% | [SCORE] | [SCORE] | [SCORE] |
| Documentation | 20% | [SCORE] | [SCORE] | [SCORE] |
| Compatibility | 25% | [SCORE] | [SCORE] | [SCORE] |
| Performance | 20% | [SCORE] | [SCORE] | [SCORE] |
| **Total** | 100% | [TOTAL] | [TOTAL] | [TOTAL] |

## Context Handoff Protocol

### Memory Keys
- `baseline_snapshot`: Current project architecture and dependencies
- `phase1_candidates`: Initial 5-8 discovered tools with basic scores
- `phase2_evaluation`: Detailed technical assessment of top 3-4
- `phase3_decision`: Final selection with implementation plan

### Between-Phase Data Flow
1. **Phase 1 → Phase 2**: Pass top 3-4 candidates with initial scores
2. **Phase 2 → Phase 3**: Pass top 2-3 finalists with detailed evaluations
3. **Phase 3 → Output**: Final recommendation with code examples

## Response Format Standards

### Discovery Output (Phase 1)
```markdown
## Candidate: [Tool Name]
- **GitHub**: [stars] ⭐ | [forks] forks | Updated [date]
- **Score**: [X/10] based on maturity, activity, fit
- **Reason**: [2-3 sentences on why it's a candidate]
```

### Evaluation Output (Phase 2)
```markdown
## [Tool Name] - Technical Evaluation
- **API Compatibility**: [Compatible/Issues] - [brief explanation]
- **Migration Path**: [Clear/Complex] - [key steps]
- **Breaking Changes**: [version] → [version] - [summary]
- **Code Pattern**: 
  ```[language]
  [10-15 line example]
  ```
```

### Decision Output (Phase 3)
```markdown
## Recommendation: [Tool Name]
**Weighted Score**: [X.X/10]

### Implementation Checklist
- [ ] Install: `[installation command]`
- [ ] Configure: [key configuration file]
- [ ] Integrate: [integration points in codebase]
- [ ] Test: [validation approach]

### Code Snippets
[Store in archon/memory for reference]
```

## Constraints and Limitations
- **No speculative installs**: Only recommend, don't execute
- **No breaking changes**: Flag migration complexity upfront
- **No full file rewrites**: Provide targeted patches only
- **Token budget**: Stay within 150-200 words per section

## Workspace Documentation (REQUIRED)
**Directory**: `.agent-workspace/research/`

**Files to maintain**:
- `findings.md`: Phase outputs (candidates, scores, evaluations)
- `decision.md`: Final recommendation with implementation plan

**Purpose**: Orchestrator Agent reads these files to coordinate with Coding Agent and track project progress. Update after each research phase.
