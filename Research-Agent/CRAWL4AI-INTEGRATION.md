# Crawl4AI-RAG-MCP Integration Guide

## Quick Reference

### What is crawl4ai-rag-mcp?
A Model Context Protocol (MCP) server that combines [Crawl4AI](https://crawl4ai.com) web scraping with Supabase vector storage for RAG capabilities. Perfect for the Research Agent to scrape live documentation, extract code examples, and perform semantic searches.

**Repository**: `coleam00/mcp-crawl4ai-rag`  
**Author**: Cole Medin (Archon creator)

---

## Installation

### Step 1: Install the MCP Server

```bash
# Clone the repository
git clone https://github.com/coleam00/mcp-crawl4ai-rag.git
cd mcp-crawl4ai-rag

# Install dependencies
pip install uv
uv pip install -e .
crawl4ai-setup
```

### Step 2: Configure Environment Variables

Create `.env` file:

```bash
# Required: Supabase Configuration
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-service-role-key

# Feature Flags (recommended for Research Agent)
USE_AGENTIC_RAG=true        # Enable code example extraction
USE_HYBRID_SEARCH=true      # Better search accuracy
USE_RERANKING=true          # Improve result relevance

# Optional: Knowledge Graph (advanced)
USE_KNOWLEDGE_GRAPH=false
```

### Step 3: Setup Supabase Database

Run the SQL schema from repository:

```bash
# Execute crawled_pages.sql in your Supabase SQL editor
# Creates tables: crawled_pages, sources, code_examples
```

### Step 4: Register with VS Code

Add to `.vscode/mcp-config.json`:

```json
{
  "mcpServers": {
    "crawl4ai-rag": {
      "command": "python",
      "args": ["/path/to/mcp-crawl4ai-rag/src/crawl4ai_mcp.py"],
      "env": {
        "TRANSPORT": "sse",
        "HOST": "0.0.0.0",
        "PORT": "8051"
      }
    }
  }
}
```

---

## Available Tools

### Core Tools (Always Available)

#### 1. `crawl_single_page(url: str)`
Crawl a single web page and store in vector DB.

**Use Case**: Quick documentation scraping for a specific page  
**Research Agent Phase**: Phase 1 (Discovery)  
**Example**:
```
Crawl the React documentation page: https://react.dev/learn/installation
```

#### 2. `smart_crawl_url(url: str, max_depth: int = 3, max_concurrent: int = 10, chunk_size: int = 5000)`
Intelligently crawl based on URL type (sitemap, llms.txt, or recursive).

**Use Case**: Scrape entire documentation sites  
**Research Agent Phase**: Phase 1 (Discovery)  
**Example**:
```
Crawl the FastAPI documentation site with sitemap: https://fastapi.tiangolo.com/sitemap.xml
```

#### 3. `get_available_sources()`
List all crawled domains in the database.

**Use Case**: Check what documentation is available before RAG queries  
**Research Agent Phase**: Phase 1 & 2  
**Example**:
```
Show me all available documentation sources in the database
```

#### 4. `perform_rag_query(query: str, source: str = None, match_count: int = 5)`
Semantic search on crawled content with optional source filtering.

**Use Case**: Find relevant documentation sections  
**Research Agent Phase**: Phase 2 (Evaluation)  
**Example**:
```
Search for "error handling patterns" in react.dev documentation
```

### Advanced Tools

#### 5. `search_code_examples(query: str, source_id: str = None, match_count: int = 5)`
**Requires**: `USE_AGENTIC_RAG=true`

Search specifically for code examples with AI-generated summaries.

**Use Case**: Extract executable code patterns  
**Research Agent Phase**: Phase 2 (Evaluation)  
**Example**:
```
Find code examples for "async/await patterns" from fastapi.tiangolo.com
```

#### 6. `query_knowledge_graph(command: str)`
**Requires**: `USE_KNOWLEDGE_GRAPH=true`

Query Neo4j knowledge graph of parsed repositories.

**Use Case**: Validate AI-generated code, explore class relationships  
**Research Agent Phase**: Phase 3 (Implementation - validation)  
**Example Commands**:
```
repos                           # List all repositories
explore fastapi                 # Repository overview
class APIRouter                 # Explore specific class
method __init__ APIRouter       # Find method in class
```

#### 7. `parse_github_repository(repo_url: str)`
**Requires**: `USE_KNOWLEDGE_GRAPH=true`

Parse GitHub repository into Neo4j knowledge graph.

**Use Case**: Build knowledge graph for hallucination detection  
**Research Agent Phase**: Phase 3 (Implementation)  
**Example**:
```
Parse repository: https://github.com/fastapi/fastapi
```

#### 8. `check_ai_script_hallucinations(script_path: str)`
**Requires**: `USE_KNOWLEDGE_GRAPH=true`

Validate AI-generated Python code against knowledge graph.

**Use Case**: Verify implementation code before committing  
**Research Agent Phase**: Phase 3 (Implementation - validation)  
**Example**:
```
Check for hallucinations in: /workspace/agent-code/implementation.py
```

---

## Integration with Research Agent Phases

### Phase 1: Discovery

**Goal**: Scrape candidate documentation sites

**Workflow**:
1. Use `smart_crawl_url` to scrape each candidate's docs
2. Store in vector DB for Phase 2 retrieval
3. Use `get_available_sources` to verify storage

**Example Prompt Addition**:
```markdown
## Step 3.5: Documentation Scraping

For candidates lacking Context7 entries:

1. Identify documentation URL (check candidate README)
2. Run: `smart_crawl_url(url="https://docs.example.com", max_depth=2)`
3. Verify: `get_available_sources()` shows "docs.example.com"
4. Note source_id for Phase 2 RAG queries
```

### Phase 2: Evaluation

**Goal**: Extract advanced patterns and code examples via RAG

**Workflow**:
1. Use `get_available_sources` to list scraped docs
2. Use `perform_rag_query` for advanced patterns
3. Use `search_code_examples` for executable snippets
4. Compare across finalists

**Example Prompt Addition**:
```markdown
## Step 4.5: RAG Pattern Discovery

For each finalist:

1. Query advanced patterns:
   - `perform_rag_query(query="production setup", source="docs.candidate.com")`
   - `perform_rag_query(query="error handling", source="docs.candidate.com")`

2. Extract code examples:
   - `search_code_examples(query="async patterns", source_id="docs.candidate.com", match_count=5)`

3. Document findings in comparison matrix
```

### Phase 3: Implementation (Optional)

**Goal**: Validate AI-generated code

**Workflow** (if knowledge graph enabled):
1. Parse finalist's GitHub repo: `parse_github_repository(repo_url)`
2. Generate implementation code with Copilot
3. Validate: `check_ai_script_hallucinations(script_path)`
4. Review hallucination report

**Example Prompt Addition**:
```markdown
## Step 5.5: Code Validation (Optional)

If USE_KNOWLEDGE_GRAPH enabled:

1. Parse winning tool's repository
2. Generate implementation code
3. Run hallucination check
4. Review and fix any detected issues
```

---

## Configuration Recommendations

### For Research Agent Use Case

**Recommended Settings**:
```bash
USE_AGENTIC_RAG=true        # Essential for code example extraction
USE_HYBRID_SEARCH=true      # Better accuracy (vector + keyword)
USE_RERANKING=true          # Improve top-k results
USE_KNOWLEDGE_GRAPH=false   # Optional, only if validating code
```

### Performance Tuning

**For Fast Discovery** (Phase 1):
```python
smart_crawl_url(
    url="https://docs.example.com",
    max_depth=2,              # Limit depth for speed
    max_concurrent=10,        # Parallel crawling
    chunk_size=5000           # Default chunking
)
```

**For Comprehensive Evaluation** (Phase 2):
```python
perform_rag_query(
    query="advanced usage patterns",
    source="docs.example.com",
    match_count=10            # Get more results
)
```

---

## Workflow Example: Research React State Management

### Phase 1: Discovery

```markdown
1. Candidates identified: Zustand, Jotai, Valtio

2. Scrape documentation:
   - Zustand: `smart_crawl_url("https://docs.pmnd.rs/zustand/getting-started/introduction")`
   - Jotai: `smart_crawl_url("https://jotai.org/docs/introduction")`
   - Valtio: `smart_crawl_url("https://valtio.pmnd.rs/docs/introduction/getting-started")`

3. Verify storage:
   - `get_available_sources()`
   - Expected: docs.pmnd.rs, jotai.org, valtio.pmnd.rs

4. Store source IDs in memory for Phase 2
```

### Phase 2: Evaluation

```markdown
1. RAG queries for each candidate:
   
   **Zustand**:
   - `perform_rag_query(query="async actions", source="docs.pmnd.rs")`
   - `search_code_examples(query="middleware patterns", source_id="docs.pmnd.rs")`
   
   **Jotai**:
   - `perform_rag_query(query="async atoms", source="jotai.org")`
   - `search_code_examples(query="atom patterns", source_id="jotai.org")`
   
   **Valtio**:
   - `perform_rag_query(query="proxy patterns", source="valtio.pmnd.rs")`
   - `search_code_examples(query="mutation tracking", source_id="valtio.pmnd.rs")`

2. Document findings in comparison matrix

3. Narrow to top 2 based on RAG-discovered patterns
```

### Phase 3: Implementation (Optional)

```markdown
1. Winner: Zustand

2. Parse repository (if knowledge graph enabled):
   - `parse_github_repository("https://github.com/pmndrs/zustand")`

3. Generate implementation code with Copilot

4. Validate (if knowledge graph enabled):
   - `check_ai_script_hallucinations("/workspace/store-implementation.ts")`

5. Review hallucination report and fix
```

---

## Troubleshooting

### Common Issues

**Issue**: "Code example extraction is disabled"  
**Solution**: Set `USE_AGENTIC_RAG=true` in `.env`

**Issue**: "Knowledge graph functionality is disabled"  
**Solution**: Set `USE_KNOWLEDGE_GRAPH=true` and configure Neo4j

**Issue**: No results from `perform_rag_query`  
**Solution**: 
1. Run `get_available_sources()` to check if docs were crawled
2. Verify `source` parameter matches source_id exactly
3. Try broader query terms

**Issue**: Crawling is slow  
**Solution**:
1. Reduce `max_depth` parameter
2. Increase `max_concurrent` for parallel crawling
3. Use sitemap URLs when available (`/sitemap.xml`)

---

## Best Practices

### 1. Always Check Available Sources First
```
Before RAG queries: get_available_sources() → note source_ids → use in queries
```

### 2. Use Appropriate Crawl Methods
- **Single page**: `crawl_single_page` (fast, specific)
- **Documentation site**: `smart_crawl_url` with sitemap
- **Blog/tutorial**: `smart_crawl_url` with depth=2

### 3. Optimize Query Specificity
- **Too broad**: "React" → Too many results
- **Too narrow**: "React useState with TypeScript generics" → No results
- **Just right**: "useState TypeScript" → Relevant results

### 4. Leverage Hybrid Search
With `USE_HYBRID_SEARCH=true`, queries match both semantically and via keywords, improving accuracy for technical terms.

### 5. Token Management
- Crawl sites progressively (don't crawl all at once)
- Use source filtering in RAG queries
- Set `match_count` appropriately (5-10 typically sufficient)

---

## Next Steps

1. **Install crawl4ai-rag-mcp**: Follow installation steps above
2. **Update Research Agent files**: Add tool to chat mode and prompts
3. **Test with sample research**: Try React state management example
4. **Iterate on prompts**: Refine based on real usage
5. **Enable advanced features**: Try knowledge graph for code validation

---

**Last Updated**: 2025-10-08  
**Compatible With**: Research Agent Framework v1.0  
**Repository**: https://github.com/coleam00/mcp-crawl4ai-rag
