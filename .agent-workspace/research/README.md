# Research Agent - Workspace

Save all research outputs here for Orchestrator coordination.

## Files

### findings.md
Phase-by-phase research results:
- **Phase 1**: Candidate list with scores
- **Phase 2**: Detailed evaluations
- **Phase 3**: Comparison matrix

### decision.md
Final recommendation:
- Selected tool/library
- Implementation checklist
- Code snippets/examples
- Integration points

## Format Example

```markdown
## State Management Decision

**Selected**: Zustand v4.5.0

**Reasons**:
- Lightweight: 12KB (vs Redux 45KB)
- Simple API: No boilerplate
- TypeScript native
- Active maintenance (updated 2 weeks ago)

**Installation**:
npm install zustand@4.5.0

**Integration Points**:
- Create store at src/store/index.ts
- Import in src/App.tsx
- Use hooks in components

**Code Example**:
[10-15 line example]
```
