# Research Agent Framework - Validation & Enhancement Plan

## Part 1: Validation Checklist

### ✅ Chat Mode Validation (`Research-Agent-code.chatmode.md`)

#### Required Fields (Official Standards)
- [x] **YAML Front Matter**: Present and properly formatted
- [x] **`description`**: Single-line summary of chat mode purpose
- [x] **`tools`**: Array of tool names (MCP server names)
- [x] **Body Content**: Markdown instructions below front matter

#### Tool Registration Verification
- [ ] **Core MCP Tools**: Verify all tools are valid MCP server names
  - `mcp_memory` → Validate: MCP Memory server installed
  - `mcp_filesystem` → Validate: MCP Filesystem server installed
  - `mcp_serena` → Validate: Serena server installed
  - `github` → Validate: GitHub MCP server installed
  - `mcp_context7` → Validate: Context7 server installed
  - `mcp_sequential-thinking` → Validate: Sequential Thinking server installed

#### Content Structure Review
- [x] **Purpose Section**: Clear definition of chat mode objectives
- [x] **Response Style**: Concise, structured, context-aware, progressive
- [x] **Phase-Specific Tools**: Tools organized by research phase
- [x] **Behavioral Constraints**: Token efficiency, no full file reads, context continuity
- [x] **Focus Areas**: 5 key research activities defined
- [x] **Mode-Specific Instructions**: Clear operational guidelines

#### Best Practices Compliance
- [x] **Token Efficiency**: 150-200 words per section constraint documented
- [x] **Tool Distribution**: <128 tools total (currently 6 base tools + extensions)
- [x] **Markdown Formatting**: Proper headings, lists, code blocks
- [ ] **Tool Invocation Examples**: Add usage examples for each phase

---

### ✅ Instructions Validation (`Research-Instructions.instructions.md`)

#### Required Fields (Official Standards)
- [x] **YAML Front Matter**: Present and properly formatted
- [x] **`applyTo`**: Pattern for file matching (`'**'` for all files)
- [x] **Body Content**: Markdown coding guidelines below front matter

#### Content Structure Review
- [x] **Project Context**: Template for research objectives
- [x] **Current Stack**: Placeholder for technology inventory
- [x] **Token Efficiency Standards**: File reading, code snippets, documentation, memory usage
- [x] **Search Patterns**: Phase-specific workflows (8→4→3 funnel)
- [x] **Integration Requirements**: API style, state management, testing, build
- [x] **Evaluation Criteria**: Weighted scoring (Maturity 20%, Community 15%, Docs 20%, Compatibility 25%, Performance 20%)
- [x] **Decision Matrix Template**: Structured comparison table
- [x] **Context Handoff Protocol**: Memory keys and data flow
- [x] **Response Format Standards**: Phase-specific output templates
- [x] **Constraints**: No installs, no breaking changes, targeted patches only

#### Best Practices Compliance
- [x] **Modular Sections**: Clear separation of concerns
- [x] **Placeholder Comments**: `<!-- -->` for user-fillable sections
- [x] **Concrete Examples**: Code block templates included
- [x] **Weight Distribution**: Totals to 100%
- [ ] **Variable Usage**: Add support for `${workspaceFolder}`, `${file}` variables

---

### ✅ Prompt Validation (Phase 1, 2, 3)

#### Required Fields (Official Standards)
All three prompts (`Phase-1-Research.prompt.md`, `Phase-2-Research.prompt.md`, `Phase-3-Research.prompt.md`):

- [x] **YAML Front Matter**: Present in all prompts
- [x] **`mode`**: References `Research-Agent-code` chat mode
- [x] **`tools`**: Phase-specific tool arrays
- [x] **`description`**: Single-line phase objective
- [x] **Body Content**: Markdown task instructions

#### Phase 1 (Discovery) - Specific Checks
- [x] **4-Step Structure**: Baseline → Discovery → Preview → Narrowing
- [x] **Success Criteria**: Checkboxes for each step
- [x] **Output Requirements**: Candidate template with scoring
- [x] **Memory Artifacts**: 3 deliverables defined
- [x] **Handoff Data**: Context prepared for Phase 2
- [x] **Constraints**: Token budget, search strategy, no code analysis

#### Phase 2 (Evaluation) - Specific Checks
- [x] **5-Step Structure**: Handoff → API Analysis → Community → Patterns → Matrix
- [x] **Context Retrieval**: Reads Phase 1 memory artifacts
- [x] **API Documentation**: 10-15 line code examples
- [x] **Comparison Matrix**: Weighted criteria table
- [x] **Memory Artifacts**: 3 deliverables defined
- [x] **Handoff Data**: Top 2-3 finalists to Phase 3

#### Phase 3 (Implementation) - Specific Checks
- [x] **5-Step Structure**: Handoff → Decision → Planning → Code → Validation
- [x] **Sequential Thinking**: Uses `mcp_sequential-thinking` tool
- [x] **Decision Matrix**: Weighted scoring with rationale
- [x] **Implementation Checklist**: Prerequisites, install, config, integration, testing
- [x] **Code Examples**: 15-20 line snippets
- [x] **Risk Assessment**: Technical risks, validation, success metrics

#### Best Practices Compliance (All Prompts)
- [x] **Consistent Formatting**: Markdown structure matches across phases
- [x] **Clear Objectives**: Each phase has explicit goals
- [x] **Progressive Narrowing**: 8→4→3 candidate reduction
- [ ] **Variable Support**: Add `${workspaceFolder}`, `${selection}` where appropriate
- [x] **Tool Alignment**: Tools match phase requirements

---

## Part 2: Enhancement Opportunities

### 🔧 Flexibility Improvements

#### 1. Dynamic Tool Selection
**Current State**: Fixed tool arrays in YAML front matter  
**Enhancement**: Support conditional tool loading based on project type

```yaml
---
mode: Research-Agent-code
tools: ['mcp_memory', 'mcp_filesystem', 'mcp_serena', 'github', 'mcp_context7']
conditionalTools:
  webScrapin: ['crawl4ai-rag-mcp']  # Add when researching web scraping tools
  python: ['python-ast-mcp']         # Add when researching Python libraries
  javascript: ['npm-registry-mcp']   # Add when researching npm packages
description: 'Phase 1: Discovery with dynamic tool loading'
---
```

#### 2. Alternate Workflow Patterns
**Current State**: Linear 3-phase workflow (Discovery → Evaluation → Implementation)  
**Enhancement**: Support flexible workflow modes

**Proposed Workflow Variants**:
- **Quick Research Mode**: Single-phase condensed workflow (30min research)
- **Deep Dive Mode**: 5-phase extended workflow (add "Architecture Review" + "Migration Planning")
- **Comparative Analysis Mode**: Side-by-side evaluation of 2-3 pre-selected tools
- **Trend Analysis Mode**: Focus on ecosystem evolution and future-proofing

**Implementation**:
```yaml
---
mode: Research-Agent-code
workflow: 'quick'  # Options: 'standard', 'quick', 'deep', 'comparative', 'trend'
tools: ['mcp_memory', 'github', 'mcp_context7']
---
```

#### 3. Metadata Extensions for Future Phases
**Current State**: Basic metadata (mode, tools, description)  
**Enhancement**: Rich metadata for phase tracking and automation

```yaml
---
mode: Research-Agent-code
tools: ['mcp_memory', 'mcp_filesystem', 'mcp_serena', 'github']
description: 'Phase 1: Discovery'
# Extended metadata
phase: 1
dependsOn: []
produces: ['baseline_snapshot', 'phase1_candidates']
consumes: []
estimatedTime: '30-45 minutes'
complexity: 'low'
tags: ['discovery', 'search', 'initial-scoring']
version: '1.0'
---
```

#### 4. Template Variables for Reusability
**Current State**: Hardcoded placeholders requiring manual editing  
**Enhancement**: VS Code variable substitution

**Add to Instructions**:
```markdown
### Current Stack
- **Project Path**: ${workspaceFolder}
- **Active File**: ${file}
- **Language**: ${fileExtname}
- **Framework**: ${input:framework:Enter framework name}
```

**Add to Prompts**:
```markdown
## Step 1: Baseline Analysis

### Task
Analyze project at `${workspaceFolder}` and create baseline snapshot.

### Current Context
- **Active File**: ${file}
- **Selection**: ${selection}
- **User Input**: ${input:researchGoal:What are you researching?}
```

---

### 🚀 crawl4ai-rag-mcp Integration

#### Tool Capabilities (from `coleam00/mcp-crawl4ai-rag`)
Based on repository analysis, this MCP server provides:

**Core Tools**:
1. **`crawl_single_page`**: Crawl single URL and store in vector DB
2. **`smart_crawl_url`**: Intelligent crawling (sitemap, llms.txt, recursive)
3. **`get_available_sources`**: List all crawled domains in database
4. **`perform_rag_query`**: Semantic search with optional source filtering

**Advanced Tools** (conditional on env vars):
5. **`search_code_examples`**: Search code snippets from documentation (requires `USE_AGENTIC_RAG=true`)
6. **`query_knowledge_graph`**: Explore Neo4j knowledge graph of repositories (requires `USE_KNOWLEDGE_GRAPH=true`)
7. **`parse_github_repository`**: Parse GitHub repos into knowledge graph (requires `USE_KNOWLEDGE_GRAPH=true`)
8. **`check_ai_script_hallucinations`**: Validate AI-generated code (requires `USE_KNOWLEDGE_GRAPH=true`)

**Advanced Features**:
- Hybrid search (vector + keyword)
- Reranking with cross-encoder models
- Contextual embeddings
- Knowledge graph validation

#### Integration Plan

##### Step 1: Add to Chat Mode Tools Array
```yaml
---
description: 'Multi-phase research assistant with web scraping and RAG'
tools: [
  'mcp_memory', 
  'mcp_filesystem', 
  'mcp_serena', 
  'github', 
  'mcp_context7', 
  'mcp_sequential-thinking',
  'crawl4ai-rag-mcp'  # NEW
]
---
```

##### Step 2: Update Phase-Specific Tool Allocation

**Phase 1 (Discovery) - Add to Tools**:
```yaml
tools: [
  'mcp_serena', 
  'mcp_filesystem', 
  'github', 
  'mcp_context7', 
  'mcp_memory',
  'crawl4ai-rag-mcp'  # For scraping documentation sites
]
```

**Phase 2 (Evaluation) - Add to Tools**:
```yaml
tools: [
  'mcp_serena', 
  'mcp_context7', 
  'github', 
  'mcp_memory', 
  'mcp_filesystem',
  'crawl4ai-rag-mcp'  # For code examples and patterns
]
```

##### Step 3: Add New Step to Phase 1 Prompt

Insert after Step 3 (Documentation Preview):

```markdown
---

## Step 3.5: Live Documentation Scraping (Enhanced)

### Task
Use `crawl4ai-rag-mcp` to scrape live documentation sites for candidates without official docs on Context7.

### When to Use
- Candidate has no Context7 library entry
- Documentation is primarily on custom site (not GitHub README)
- Need to extract code examples from tutorials/guides

### Output Requirements
For each candidate requiring scraping:
```markdown
### Candidate: [Tool Name] - Scraped Documentation

#### Source
- **URL**: [documentation URL]
- **Pages Crawled**: [count]
- **Content Stored**: [chunks stored]

#### Code Examples Found
```[language]
[10-15 line example from docs]
```

#### Quick Start Pattern
- **Installation**: [from scraped content]
- **Basic Setup**: [from scraped content]
- **API Style**: [identified from examples]
```

### Crawl4AI Tools to Use
1. **`smart_crawl_url`**: Crawl full documentation site
   - Use sitemap if available (e.g., `/sitemap.xml`)
   - Set `max_depth=2` for doc sites
2. **`search_code_examples`**: Extract code snippets
   - Query: "[tool name] setup example"
   - Filter by `source_id` for targeted search
3. **`get_available_sources`**: Verify crawled content stored

### Success Criteria
- [ ] Documentation sites crawled and stored in vector DB
- [ ] Code examples extracted for 3-5 candidates
- [ ] Quick-start patterns identified from live content
- [ ] Source IDs noted for Phase 2 RAG queries

---
```

##### Step 4: Add New Step to Phase 2 Prompt

Insert after Step 4 (Advanced Code Pattern Analysis):

```markdown
---

## Step 4.5: RAG-Enhanced Pattern Discovery

### Task
Use `crawl4ai-rag-mcp` to perform RAG queries on previously crawled documentation for advanced patterns.

### Output Requirements
For each finalist:
```markdown
### [Tool Name] - RAG-Discovered Patterns

#### Advanced Use Cases (from RAG)
**Query**: "[tool name] advanced usage"
```[language]
[10-15 line advanced pattern from RAG results]
```

#### Production Patterns (from RAG)
**Query**: "[tool name] production setup"
```[language]
[10-15 line production config from RAG results]
```

#### Troubleshooting Insights (from RAG)
**Query**: "[tool name] common errors"
- **Issue 1**: [from RAG] - [solution]
- **Issue 2**: [from RAG] - [solution]
```

### Crawl4AI Tools to Use
1. **`get_available_sources`**: List available documentation sources
2. **`perform_rag_query`**: Semantic search on crawled content
   - Query variations: "setup", "configuration", "production", "troubleshooting"
   - Use `source` filter for targeted retrieval
3. **`search_code_examples`**: Get executable code snippets
   - Filter by finalist's source_id
   - Match_count: 3-5 per query

### Success Criteria
- [ ] RAG queries performed for all finalists
- [ ] Advanced patterns extracted beyond basic docs
- [ ] Production-ready examples identified
- [ ] Troubleshooting insights cataloged

---
```

##### Step 5: Update Instructions with Crawl4AI Guidelines

Add to **Token Efficiency Standards** section:

```markdown
### Web Scraping Strategy
- **Documentation Crawling**: Use `smart_crawl_url` for full site coverage
- **Targeted Retrieval**: Use `perform_rag_query` for specific topics
- **Code Extraction**: Use `search_code_examples` when USE_AGENTIC_RAG enabled
- **Source Management**: Always call `get_available_sources` before RAG queries
```

Add to **Search and Discovery Patterns**:

```markdown
- **Phase 1 Enhancement**: Scrape docs → Store in vector DB → Reference in Phase 2
- **Phase 2 Enhancement**: RAG queries → Extract advanced patterns → Validate with serena
```

##### Step 6: Environment Configuration Document

Create reference for enabling advanced features:

```markdown
## Crawl4AI Configuration

### Required Environment Variables
```bash
# Supabase Configuration
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key

# Feature Flags
USE_AGENTIC_RAG=true        # Enable code example extraction
USE_HYBRID_SEARCH=true      # Combine vector + keyword search
USE_RERANKING=true          # Enable cross-encoder reranking
USE_KNOWLEDGE_GRAPH=false   # Optional: Enable Neo4j knowledge graph
```

### Optional: Knowledge Graph (Advanced)
```bash
USE_KNOWLEDGE_GRAPH=true
NEO4J_URI=bolt://localhost:7687
NEO4J_USER=neo4j
NEO4J_PASSWORD=your-password
```
```

---

### 📊 Enhanced Tool Distribution Summary

**Original Tool Count per Phase**:
- Phase 1: 5 tools (memory, filesystem, serena, github, context7)
- Phase 2: 5 tools (serena, context7, github, memory, filesystem)
- Phase 3: 5 tools (sequential-thinking, memory, serena, filesystem, github)

**Enhanced Tool Count with Crawl4AI**:
- Phase 1: 6 tools (+crawl4ai-rag-mcp for doc scraping)
- Phase 2: 6 tools (+crawl4ai-rag-mcp for RAG queries)
- Phase 3: 5 tools (unchanged)

**Total Tool Count**: Still well under 128-tool limit per phase ✅

---

## Part 3: Priority Action Items

### High Priority (Implement Now)
1. [ ] **Validate Tool Installations**: Confirm all MCP servers installed in VS Code
2. [ ] **Add crawl4ai-rag-mcp**: Update chat mode and prompts with integration steps
3. [ ] **Test Phase Handoffs**: Verify memory artifacts pass correctly between phases
4. [ ] **Add Variable Support**: Include `${workspaceFolder}` and `${input:*}` in prompts
5. [ ] **Create Example Workflow**: Document end-to-end usage with sample project

### Medium Priority (Next Iteration)
6. [ ] **Implement Workflow Variants**: Add 'quick' and 'deep' workflow modes
7. [ ] **Add Tool Examples**: Include usage examples in chat mode for each tool
8. [ ] **Enhance Metadata**: Add version, complexity, estimatedTime to prompts
9. [ ] **Create Validation Script**: Automate YAML and structure validation
10. [ ] **Build Template Library**: Pre-filled instructions for common tech stacks

### Low Priority (Future Enhancement)
11. [ ] **Conditional Tool Loading**: Implement project-type-based tool selection
12. [ ] **Phase Dependencies**: Add automatic phase sequencing validation
13. [ ] **Progress Dashboard**: Create UI for tracking research progress
14. [ ] **Export Formats**: Support markdown, PDF, JSON report generation
15. [ ] **Integration Tests**: Automated testing of phase handoffs

---

## Part 4: Validation Commands

### Manual Validation Steps
```bash
# 1. Check YAML syntax
yamllint Research-Agent/.github/**/*.md

# 2. Verify tool installations
code --list-extensions | grep -E "(memory|serena|context7|github|crawl4ai)"

# 3. Test memory artifacts
# (Run Phase 1 prompt and check memory tool for stored artifacts)

# 4. Validate file structure
tree Research-Agent/.github/
```

### VS Code Settings Check
```json
{
  "chat.instructionsFilesLocations": {
    ".github/instructions": true
  },
  "chat.promptFilesLocations": {
    ".github/prompts": true
  },
  "chat.modeFilesLocations": {
    ".github/chatmodes": true
  }
}
```

---

**Framework Validation Status**: ✅ Structure complete, ready for enhancement  
**Next Steps**: Integrate crawl4ai-rag-mcp and validate tool installations  
**Last Updated**: 2025-10-08
