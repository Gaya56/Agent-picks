---
mode: Coding-Agent
tools: ['mcp_memory', 'mcp_filesystem', 'mcp_serena', 'mcp_context7', 'github', 'archon', 'mcp_crawl4ai-rag', 'mcp_sequential-thinking']
description: 'Phase 2: Implement with validation, terminal testing, permission checks'
---

# Phase 2: Implementation & Testing

## Step 1: Pre-Implementation Validation

**Load Plan:**
- Memory: `phase1_architecture`, `phase1_validation`

**Double-Check Before Coding:**
1. **Serena**: Verify exact symbols/functions/line numbers still current
   ```
   find_symbol: [target function]
   get_symbols_overview: [target file]
   ```

2. **GitHub MCP**: Confirm file paths exist
   ```
   Search: [file paths from Phase 1]
   ```

3. **Context7**: Review similar implementations one more time
   ```
   Search: [similar feature]
   Compare: Official pattern vs your existing code
   ```

4. **Crawl4ai-rag**: Check official examples
   ```
   Query: "[library] implementation example"
   ```

**Ask:** "Validation complete. Paths and symbols confirmed. Ready to implement Component 1?"

---

## Step 2: Implement One Component at a Time

**For Each Component:**

### A. Write Code (with permission)
- Use `serena` symbolic editing (insert_after_symbol, replace_symbol_body)
- Follow exact paths/symbols from validation
- Reference crawl4ai-rag docs for correct API usage

**Ask:** "Component [name] implemented. Review the changes?"

### B. Write Test in Terminal
```bash
# Node.js example
node -e "
const { functionName } = require('./path/to/file');
const result = functionName(testInput);
console.assert(result === expected, 'Test failed');
console.log('✓ Test passed');
"

# Python example
python -c "
from module import function_name
result = function_name(test_input)
assert result == expected, 'Test failed'
print('✓ Test passed')
"
```

**Ask:** "Test passed in terminal. Continue to next component?"

---

## Step 3: Integration Validation

**After All Components:**

1. **Serena**: Check no breaking changes to other symbols
   ```
   find_referencing_symbols: [modified functions]
   Verify: No unexpected references broken
   ```

2. **Context7**: Verify similar patterns still work
   ```
   Search: [related features]
   Confirm: Integration matches existing patterns
   Compare: Official docs vs your implementation
   ```

3. **Terminal Test**: Run integration test
   ```bash
   # Full workflow test in terminal
   [your test command]
   ```

**Store in Memory:**
- `phase2_implementation`: Changed files + line numbers
- `phase2_validation`: Serena + Context7 verification results

**Ask:** "Implementation complete and validated. Proceed to Phase 3 review?"

---

## Constraints
- Ask permission before EACH component implementation
- Write all tests in terminal (no new test files)
- Use serena for all code edits
- Validate with Context7 + serena after each change
- Reference crawl4ai-rag docs when unsure about API usage
