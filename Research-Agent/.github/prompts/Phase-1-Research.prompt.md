---
mode: Research-Agent-code
tools: ['mcp_serena', 'mcp_filesystem', 'github', 'mcp_context7', 'mcp_memory']

description: 'Phase 1: Discover 5-8 candidate tools/libraries and narrow to top 3-4 for deep evaluation'
---

# Phase 1: Discovery Research

## Objective
Analyze current project baseline, discover candidate tools matching requirements, and identify top 3-4 finalists for Phase 2 evaluation.

---

## Step 1: Baseline Analysis (Current State)

### Task
Use `mcp_serena` and `mcp_filesystem` to analyze the current project architecture and create a baseline snapshot.

### Output Requirements
- **Current Dependencies**: List key libraries with versions
- **Architecture Pattern**: [e.g., monorepo, microservices, SSR/CSR]
- **Integration Points**: Where new tool will connect
- **Constraints**: Version requirements, compatibility needs

### Success Criteria
- [ ] Baseline stored in `mcp_memory` as `baseline_snapshot`
- [ ] Key integration points identified
- [ ] Compatibility constraints documented

---

## Step 2: Candidate Discovery (Search & Filter)

### Task
Use `github` search tools to discover 5-8 candidate tools matching criteria from instructions.

### Search Criteria
- **Stars**: [e.g., >1000 stars]
- **Activity**: [e.g., updated within 6 months]
- **Language**: [e.g., TypeScript, Python]
- **License**: [e.g., MIT, Apache 2.0]
- **Keywords**: [SPECIFY: e.g., "state management", "data fetching", "testing"]

### Output Requirements
For each candidate (5-8 total):
```markdown
### Candidate: [Tool Name]
- **GitHub**: [repo URL]
- **Stars**: [count] ⭐ | **Forks**: [count] | **Updated**: [date]
- **License**: [type]
- **Initial Score**: [X/10]
- **Key Features**: [3-5 bullet points, 1 line each]
- **Potential Fit**: [2-3 sentences on alignment with project needs]
```

### Success Criteria
- [ ] 5-8 candidates identified and documented
- [ ] Initial scores assigned (maturity + activity + fit)
- [ ] Candidates stored in `mcp_memory` as `phase1_candidates`

---

## Step 3: Documentation Preview (Quick Assessment)

### Task
Use `mcp_context7` to fetch README/quick-start documentation for each candidate.

### Output Requirements
For each candidate:
- **Installation Method**: [e.g., npm, pip, cargo]
- **Quick Start Complexity**: [Simple/Moderate/Complex]
- **API Style**: [e.g., hooks-based, class-based, functional]
- **Documentation Quality**: [Excellent/Good/Fair/Poor]

### Success Criteria
- [ ] Documentation quality assessed for all candidates
- [ ] Quick-start patterns documented
- [ ] Red flags identified (if any)

---

## Step 4: Narrowing to Finalists (Top 3-4 Selection)

### Task
Rank candidates using scoring matrix and select top 3-4 for Phase 2 deep evaluation.

### Scoring Matrix Template
| Candidate | Stars | Activity | Docs | Fit | Total |
|-----------|-------|----------|------|-----|-------|
| [Tool A] | [X/2] | [X/2] | [X/3] | [X/3] | [X/10] |
| [Tool B] | [X/2] | [X/2] | [X/3] | [X/3] | [X/10] |
| ... | ... | ... | ... | ... | ... |

### Output Requirements
- **Top 3-4 Finalists**: List with justification (2-3 sentences each)
- **Eliminated Candidates**: Brief reason for exclusion (1 sentence each)
- **Handoff Data**: Prepare context for Phase 2

### Success Criteria
- [ ] Top 3-4 candidates selected with clear scores
- [ ] Rationale documented for selections and eliminations
- [ ] Handoff data prepared: `phase1_to_phase2_context`

---

## Phase 1 Deliverables

### Memory Artifacts
1. **`baseline_snapshot`**: Current project state and constraints
2. **`phase1_candidates`**: All 5-8 discovered candidates with scores
3. **`phase1_to_phase2_context`**: Top 3-4 finalists + key evaluation questions

### Next Phase Handoff
Pass to Phase 2:
- Top 3-4 candidate names and repo URLs
- Initial compatibility concerns
- Specific evaluation questions to answer
- Integration points to validate

---

## Constraints & Guidelines
- **Token Budget**: 150-200 words per candidate summary
- **Search Strategy**: Prioritize stars + recent activity + language match
- **Documentation Depth**: README overview only (deep-dive in Phase 2)
- **No Code Analysis**: Save detailed code patterns for Phase 2
- **Memory Usage**: Store all findings progressively
