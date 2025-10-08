# Orchestrator Agent

**Your brainstorming partner** who explains your project in simple English while tracking exact technical details.

## What It Does

1. **Explains project status** in plain language with exact code references (file:line, symbols, imports, hooks, workflows)
2. **Compares agent outputs** to find conflicts between Research and Coding agents
3. **Routes work** by deciding which agent to use next
4. **Clarifies ideas** by breaking down complex requests into simple steps
5. **Tracks progress** in `.agent-workspace/project-state.md`

## Key Features

### 🗣️ Human Communication
Talks like a person, not documentation:
- **YES**: "You're at the database decision. Research comparing PostgreSQL vs MongoDB."
- **NO**: "Analysis indicates database selection process initialization pending."

### 🎯 Exact Technical References
Always includes precise code locations:
```
File: src/hooks/useAuth.tsx:23
Symbol: validateToken
Import: import { jwt } from 'jsonwebtoken'
Hook: useEffect (line 28)
Workflow: Login → validate → store token
```

### ⚡ Ultra-Concise
50-75 words maximum. No fluff, just answers.

### 🔗 Agent Coordination
Reads `.agent-workspace/` to coordinate Research and Coding agents:
- Research outputs: `research/findings.md`, `research/decision.md`
- Coding outputs: `coding/architecture.md`, `coding/implementation.md`
- Project status: `project-state.md`

## Usage

### 1. Explain Where I Am
**Ask**: "Where are we at in the project?"

**Orchestrator**:
```
"Building authentication. Token validation complete.

Completed: Login form with validation
Current: Token refresh logic at src/auth/refresh.ts:23
Next: Logout functionality

File: src/auth/refresh.ts:23
Function: refreshToken
Workflow: Check expiry → request new → store → retry"
```

### 2. Compare Agent Outputs
**Ask**: "Do Research and Coding outputs match?"

**Orchestrator**:
```
"State management conflict found.

Research: Recommended Redux (findings.md:23)
Coding: Built Zustand at src/store/index.ts:10
Correct: Zustand - project notes specify lightweight (<5KB requirement)
Fix: Update research/decision.md"
```

### 3. Pick Next Agent
**Ask**: "What should I do next?"

**Orchestrator**:
```
"Need state management library.

Next Agent: Research
Reason: No library chosen, need evaluation
Context: Small app, <20KB bundle, TypeScript required

Expected: Compare Redux/Zustand/Jotai
Save To: research/decision.md"
```

### 4. Clarify Complex Ideas
**You**: "I want real-time updates for the dashboard"

**Orchestrator**:
```
"Two approaches:

1. WebSockets (bi-directional, more complex)
2. Server-Sent Events (one-way, simpler)

Research can compare. Then Coding implements at src/services/realtime.ts.

Current fetchData() at api.ts:12 can be extended."
```

## Workspace Structure

```
.agent-workspace/
  ├── research/
  │   ├── findings.md       # Research outputs
  │   └── decision.md       # Final recommendations
  ├── coding/
  │   ├── architecture.md   # Design + symbols
  │   └── implementation.md # Code changes + exact references
  └── project-state.md       # Status (Orchestrator maintains)
```

## Three Prompts

### 1. Compare Notes
`Review-coding-research-agent-notes-simplifyExplanation.prompt.md`
- Finds conflicts between Research and Coding outputs
- States which is correct with evidence
- Gives simple English explanation

### 2. Track Progress
`track-project-checklist.prompt.md`
- Explains project status in plain language
- Includes exact code references
- Shows completed/current/next tasks

### 3. Pick Next Agent
`Pick_Next-Agent-Fillout-prompt.prompt.md`
- Analyzes workspace to decide Research or Coding
- Explains routing in simple English
- Prepares context for chosen agent

## Response Style

### Simple English + Exact References
```
"Building login system.

File: src/components/LoginForm.tsx:34
Function: handleSubmit
Imports: react-hook-form, yup
Hook: useForm (line 36)
Workflow: Input → validate → API → redirect

Next: Error handling in catch at line 52"
```

### Clear Routing Decisions
```
"Have 3 state library options from Research.

Next Agent: You decide (pick one)
Then Coding builds store at src/store/index.ts"
```

### Conflict Resolution
```
"Research: Use async/await
Coding: Used .then() chains at api.ts:45
Correct: Coding - existing codebase uses promises throughout
Consistency > preference"
```

## Tools Used

- **mcp_filesystem**: Read `.agent-workspace/` files
- **mcp_memory**: Track decisions and routing
- **mcp_sequential-thinking**: Analyze conflicts between agents

## Design Principles

1. **Human first**: Talk like a person, not documentation
2. **Exact references**: Always cite file:line, symbols, imports
3. **Stay concise**: 50-75 words max
4. **Be decisive**: Pick the answer, don't waffle
5. **Simple English**: Explain technical concepts plainly
6. **Check workspace**: Read agent notes before answering

## Integration with Other Agents

### Research Agent
**Saves to**: `.agent-workspace/research/`
- `findings.md`: Candidates, scores, evaluations by phase
- `decision.md`: Final recommendation with implementation plan

Orchestrator reads these to:
- Track research progress
- Compare with Coding outputs
- Route next work

### Coding Agent
**Saves to**: `.agent-workspace/coding/`
- `architecture.md`: Designs with exact symbols, imports, integration points
- `implementation.md`: Code changes with file:line, functions, hooks, test results

Orchestrator reads these to:
- Verify implementation matches research
- Explain technical details in simple English
- Track coding progress

## Example Workflow

1. **User**: "I need authentication"
   
2. **Orchestrator**: "Two parts: 1) Pick auth library 2) Implement it. Research Agent can compare options (JWT, Auth0, Firebase)."

3. **Research Agent** → Saves to `research/decision.md`:
   ```
   Selected: JWT + jsonwebtoken library
   Reason: No external service, full control
   ```

4. **Orchestrator**: "JWT selected. Coding Agent will build at src/auth/. Need: login, token validation, refresh."

5. **Coding Agent** → Saves to `coding/implementation.md`:
   ```
   File: src/auth/validator.ts:10
   Function: verifyJWT
   Imports: jsonwebtoken, bcrypt
   ```

6. **Orchestrator**: 
   ```
   "Auth complete!
   
   Login: src/auth/login.ts:15 (hashPassword, generateToken)
   Validate: src/auth/validator.ts:10 (verifyJWT)
   Refresh: src/auth/refresh.ts:23 (refreshToken)
   
   Next: Add password reset?"
   ```

## Token Efficiency

**Prompts reduced**:
- Compare Notes: 65 lines (vs typical 100+)
- Track Progress: 58 lines (vs typical 90+)
- Pick Next Agent: 73 lines (vs typical 120+)

**Response limit**: 50-75 words keeps conversations fast and focused.

## Quick Start

1. Ensure `.agent-workspace/` exists (created automatically)
2. Research and Coding agents save outputs to their directories
3. Ask Orchestrator: "Where are we?" or "What's next?"
4. Orchestrator explains in simple English with exact code references
5. Follow routing suggestions (Research for decisions, Coding for implementation)

---

**Remember**: Orchestrator is your **brainstorming partner**, not your executor. It explains, routes, and clarifies - but Research and Coding do the actual work.
