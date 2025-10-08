---
mode: Research-Agent-code
tools: ['mcp_serena', 'mcp_context7', 'github', 'mcp_memory', 'mcp_filesystem']

description: 'Phase 2: Deep technical evaluation of top 3-4 finalists and narrow to top 2-3 for final decision'
---

# Phase 2: Evaluation Research

## Objective
Conduct deep technical evaluation of top 3-4 finalists from Phase 1, assess API compatibility, analyze code patterns, and narrow to top 2-3 for final implementation decision.

---

## Step 1: Context Retrieval (Phase 1 Handoff)

### Task
Retrieve Phase 1 findings from `mcp_memory` to understand baseline and candidate selection.

### Required Data
- **`baseline_snapshot`**: Current project architecture and constraints
- **`phase1_candidates`**: All discovered candidates with initial scores
- **`phase1_to_phase2_context`**: Top 3-4 finalists and evaluation questions

### Success Criteria
- [ ] Phase 1 context loaded and summarized
- [ ] Top 3-4 finalists confirmed
- [ ] Evaluation questions identified

---

## Step 2: API Compatibility Analysis

### Task
Use `mcp_context7` to fetch detailed API documentation and `mcp_serena` to check integration points.

### Output Requirements
For each finalist (3-4 tools):
```markdown
### [Tool Name] - API Compatibility

#### Installation & Setup
- **Package Manager**: [npm/pip/cargo command]
- **Version**: [recommended version]
- **Peer Dependencies**: [list if any]

#### Core API Surface
- **Primary API**: [10-15 line code example showing typical usage]
- **Configuration**: [key config options in 5-8 lines]
- **TypeScript Support**: [Built-in/DefinitelyTyped/None]

#### Integration with Current Stack
- **Compatible**: [Yes/Partial/No]
- **Integration Points**: [list 2-3 places in codebase]
- **Conflicts**: [any known issues with current dependencies]
- **Migration Effort**: [Low/Medium/High - 1-2 sentence explanation]
```

### Success Criteria
- [ ] API patterns documented for all finalists
- [ ] Compatibility assessed against baseline
- [ ] Code examples extracted (10-15 lines each)

---

## Step 3: Community & Maintenance Analysis

### Task
Use `github` tools to analyze repository health, issue handling, and release patterns.

### Output Requirements
For each finalist:
```markdown
### [Tool Name] - Community Health

#### Repository Metrics
- **Contributors**: [count] | **Active Maintainers**: [count]
- **Open Issues**: [count] | **Issue Response Time**: [avg time]
- **PRs Last Month**: [count merged/closed]

#### Release History
- **Latest Release**: [version] - [date]
- **Release Frequency**: [avg time between releases]
- **Breaking Changes**: [list major versions with breaking changes]

#### Community Signals
- **GitHub Discussions**: [active/moderate/low]
- **Stack Overflow**: [question count]
- **Notable Users**: [list 2-3 well-known projects using it]
```

### Success Criteria
- [ ] Maintenance activity assessed
- [ ] Issue response patterns documented
- [ ] Breaking change history analyzed

---

## Step 4: Advanced Code Pattern Analysis

### Task
Use `github` code search and `mcp_context7` to find advanced usage patterns and best practices.

### Output Requirements
For each finalist:
```markdown
### [Tool Name] - Advanced Patterns

#### Error Handling
```[language]
[5-10 line example of error handling pattern]
```

#### Performance Optimization
- **Key Optimization**: [describe in 2-3 sentences]
```[language]
[5-10 line example if applicable]
```

#### Testing Pattern
```[language]
[5-10 line example of typical test setup]
```

#### Common Pitfalls
- [Pitfall 1]: [1-2 sentence description]
- [Pitfall 2]: [1-2 sentence description]
```

### Success Criteria
- [ ] Advanced patterns documented
- [ ] Testing approaches identified
- [ ] Known pitfalls cataloged

---

## Step 5: Comparison Matrix & Finalist Selection

### Task
Build detailed comparison matrix using weighted criteria from instructions and select top 2-3 finalists.

### Comparison Matrix Template
| Criteria | Weight | [Tool A] | [Tool B] | [Tool C] | [Tool D] |
|----------|--------|----------|----------|----------|----------|
| **Technical** |  |  |  |  |  |
| API Compatibility | 25% | [score] | [score] | [score] | [score] |
| TypeScript Support | 10% | [score] | [score] | [score] | [score] |
| Bundle Size | 10% | [score] | [score] | [score] | [score] |
| **Maturity** |  |  |  |  |  |
| Release Stability | 15% | [score] | [score] | [score] | [score] |
| Breaking Changes | 10% | [score] | [score] | [score] | [score] |
| **Community** |  |  |  |  |  |
| Maintainer Activity | 10% | [score] | [score] | [score] | [score] |
| Issue Resolution | 10% | [score] | [score] | [score] | [score] |
| **Documentation** |  |  |  |  |  |
| API Docs Quality | 10% | [score] | [score] | [score] | [score] |
| **Total** | 100% | [X.X] | [X.X] | [X.X] | [X.X] |

### Output Requirements
- **Top 2-3 Finalists**: Ranked with weighted scores
- **Key Differentiators**: What sets top candidates apart (3-4 sentences each)
- **Concerns**: Any remaining technical concerns (1-2 sentences per tool)

### Success Criteria
- [ ] Comparison matrix completed with scores
- [ ] Top 2-3 finalists selected
- [ ] Technical assessment stored in `mcp_memory` as `phase2_evaluation`

---

## Phase 2 Deliverables

### Memory Artifacts
1. **`phase2_evaluation`**: Detailed technical assessment of all 3-4 candidates
2. **`phase2_comparison_matrix`**: Weighted scoring with rationale
3. **`phase2_to_phase3_context`**: Top 2-3 finalists + decision criteria

### Next Phase Handoff
Pass to Phase 3:
- Top 2-3 finalist names with scores
- Key technical considerations for final decision
- Implementation complexity estimates
- Code examples for each finalist

---

## Constraints & Guidelines
- **Token Budget**: 150-200 words per section per tool
- **Code Snippets**: 10-15 lines maximum per example
- **Search Scope**: Focus on official docs + top 3 community resources
- **No Full Clones**: Don't analyze entire repositories, use targeted searches
- **Memory Usage**: Store comparison data progressively
- **Context7 Usage**: Request targeted docs (API, migration, best practices)
