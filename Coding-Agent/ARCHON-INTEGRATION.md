# Archon Integration Guide for Coding Agent

## Overview
[Archon](https://github.com/coleam00/Archon) is a knowledge engine for AI coding assistants that provides access to code patterns, best practices, and implementation examples. This guide shows how to integrate Archon with the Coding Agent framework.

## Installation
Archon is already installed in this environment (from `coleam00/Archon`, dev branch).

## Archon Capabilities

### Core Functions
1. **Pattern Retrieval**: Get code patterns for specific technologies
2. **Example Code**: Retrieve working implementation examples
3. **Best Practices**: Access curated best practices and conventions
4. **Common Pitfalls**: Learn about common mistakes and how to avoid them
5. **Optimization Techniques**: Discover performance optimization strategies

### Query Types
- **Design Patterns**: "React Context pattern", "Repository pattern Python"
- **Implementation Examples**: "Express middleware example", "Django serializer implementation"
- **Error Handling**: "JavaScript promise error handling", "Python exception best practices"
- **Optimization**: "React performance optimization", "SQL query optimization"
- **Testing**: "Jest mock example", "pytest fixture patterns"

## Integration Per Phase

### Phase 1: Architecture & Planning

#### Step 3: Knowledge Base Query
Use Archon to gather design patterns and architectural guidance.

**Example Queries**:
```markdown
### Design Patterns Query
**Query**: "React state management patterns"
**Expected Output**: Context API, Redux, Zustand patterns with trade-offs

**Query**: "Node.js service layer architecture"
**Expected Output**: Service/Repository pattern, dependency injection examples

**Query**: "Python async patterns"
**Expected Output**: asyncio patterns, event loops, coroutine examples
```

**Usage in Phase 1**:
```markdown
#### Knowledge Base Insights (from Archon)

**Query**: "[tool name] design patterns [language]"

**Results**:
1. **Pattern Name**: [Description from Archon]
   - **Use Case**: [When to use this pattern]
   - **Example**:
     ```[language]
     [10-15 line code example from Archon]
     ```

2. **Alternative Pattern**: [Description]
   - **Trade-offs**: [Comparison to first pattern]
```

**Integration Points**:
1. After loading Research Agent decision
2. Before designing component architecture
3. When evaluating alternative approaches

### Phase 2: Implementation & Testing

#### Step 3: Core Implementation
Use Archon for implementation guidance and code examples.

**Example Queries**:
```markdown
### Implementation Examples
**Query**: "[library] initialization example"
**Query**: "[framework] error handling pattern"
**Query**: "[tool] configuration best practices"
```

**Usage in Phase 2**:
```markdown
#### Component Implementation

**Archon Query**: "[tool name] [component type] implementation [language]"

**Retrieved Pattern**:
```[language]
// Pattern from Archon
[implementation example]
```

**Adapted for Project**:
```[language]
// Applied to our architecture
[customized implementation]
```
```

**Integration Points**:
1. Before implementing each component
2. When stuck on implementation details
3. For error handling patterns
4. For testing strategies

#### Step 4: Integration & Testing
Query Archon for testing patterns.

**Example Queries**:
```markdown
**Query**: "[testing framework] integration test example"
**Query**: "[library] mock example"
**Query**: "end-to-end test pattern [framework]"
```

### Phase 3: Review, Optimization & Validation

#### Step 3: Performance Analysis
Use Archon to identify optimization techniques.

**Example Queries**:
```markdown
### Optimization Queries
**Query**: "[language] performance optimization techniques"
**Query**: "[framework] rendering optimization"
**Query**: "[database] query optimization"
**Query**: "memory leak prevention [language]"
```

**Usage in Phase 3**:
```markdown
#### Optimization Opportunity

**Current Code**: [performance bottleneck]

**Archon Query**: "[tool/library] [optimization type]"

**Archon Suggestion**:
```[language]
// Optimized approach from Archon
[code example]
```

**Implementation**:
```[language]
// Applied optimization
[refactored code]
```

**Result**: [performance improvement metric]
```

**Integration Points**:
1. When analyzing performance bottlenecks
2. Before refactoring complex logic
3. For code quality improvements
4. When reviewing code patterns

## Real-World Workflow Example

### Scenario: Implementing User Authentication
Research Agent selected **Passport.js** for authentication.

#### Phase 1: Architecture (with Archon)

**Step 3: Knowledge Query**
```markdown
### Archon Queries

**Query 1**: "Passport.js strategy pattern"
**Result**: Strategy abstraction, local/OAuth examples

**Query 2**: "Express session management best practices"
**Result**: Session store options, security considerations

**Query 3**: "JWT authentication pattern Node.js"
**Result**: Token generation, refresh token strategy

### Architecture Decision (based on Archon)
- **Strategy**: Passport Local Strategy + JWT
- **Session Store**: Redis (from Archon recommendation)
- **Security**: bcrypt for passwords, httpOnly cookies for tokens
```

#### Phase 2: Implementation (with Archon)

**Step 3: Core Implementation**
```markdown
### Component 1: Passport Configuration

**Archon Query**: "Passport local strategy implementation"

**Archon Example**:
```javascript
const LocalStrategy = require('passport-local').Strategy;

passport.use(new LocalStrategy(
  function(username, password, done) {
    User.findOne({ username: username }, function (err, user) {
      if (err) { return done(err); }
      if (!user) { return done(null, false); }
      if (!user.verifyPassword(password)) { return done(null, false); }
      return done(null, user);
    });
  }
));
```

**Applied to Project**:
```javascript
// config/passport.js
const LocalStrategy = require('passport-local').Strategy;
const bcrypt = require('bcrypt');
const User = require('../models/User');

module.exports = (passport) => {
  passport.use(new LocalStrategy(
    { usernameField: 'email' }, // Our project uses email
    async (email, password, done) => {
      try {
        const user = await User.findOne({ email });
        if (!user) {
          return done(null, false, { message: 'User not found' });
        }
        
        const isMatch = await bcrypt.compare(password, user.password);
        if (!isMatch) {
          return done(null, false, { message: 'Invalid credentials' });
        }
        
        return done(null, user);
      } catch (error) {
        return done(error);
      }
    }
  ));
};
```
```

**Additional Query for Error Handling**:
```markdown
**Archon Query**: "Express async error handling middleware"

**Applied Pattern**:
```javascript
// middleware/errorHandler.js
// Pattern from Archon adapted for authentication errors
module.exports = (err, req, res, next) => {
  if (err.name === 'AuthenticationError') {
    return res.status(401).json({ error: 'Authentication failed' });
  }
  // ... other error handling
};
```
```

#### Phase 3: Review & Optimization (with Archon)

**Step 3: Performance Analysis**
```markdown
### Optimization: Session Store Performance

**Archon Query**: "Redis session optimization Node.js"

**Archon Recommendation**:
- Use connection pooling
- Implement session TTL
- Enable Redis pipelining for bulk operations

**Applied Optimization**:
```javascript
// config/redis.js
const redis = require('redis');
const RedisStore = require('connect-redis')(session);

const redisClient = redis.createClient({
  host: process.env.REDIS_HOST,
  port: process.env.REDIS_PORT,
  enable_offline_queue: false, // From Archon recommendation
  retry_strategy: (options) => {
    if (options.total_retry_time > 1000 * 60 * 60) {
      return new Error('Redis retry time exhausted');
    }
    return Math.min(options.attempt * 100, 3000);
  }
});

const store = new RedisStore({
  client: redisClient,
  ttl: 86400, // 24 hours, from Archon suggestion
  prefix: 'sess:',
});
```

**Result**: 40% reduction in session lookup time
```

## Query Best Practices

### ✅ Good Queries (Specific)
- "React useEffect cleanup pattern"
- "Express JWT middleware implementation"
- "Django REST serializer validation"
- "Node.js stream backpressure handling"
- "Python asyncio error handling"

### ❌ Bad Queries (Too Broad)
- "React best practices" (too general)
- "JavaScript patterns" (not specific enough)
- "How to code" (no context)
- "Web development" (too vague)

### Query Construction Template
```
"[Technology/Library] [Specific Pattern/Feature] [Implementation/Example]"

Examples:
- "Vue 3 Composition API reactive pattern"
- "FastAPI dependency injection example"
- "PostgreSQL JSON query optimization"
```

## Archon Response Handling

### Typical Response Format
Archon returns:
1. **Pattern Description**: Text explanation of the pattern
2. **Code Example**: Working implementation
3. **Context**: When to use, trade-offs
4. **Related Patterns**: Alternative approaches

### Adapting Archon Output
Always adapt Archon examples to your project:

```markdown
**Archon Example** (generic):
```javascript
// Generic implementation
function example() { ... }
```

**Project Adaptation**:
```javascript
// Adapted to our codebase structure
// Follows our naming conventions
// Includes our error handling
function ourImplementation() { ... }
```
```

## Integration with Other Tools

### Archon + Serena
1. Use **Archon** to get implementation pattern
2. Use **Serena** to find where to integrate it in codebase
3. Apply pattern using symbolic editing

**Example**:
```markdown
1. Archon query: "Express error handling middleware"
2. Serena: Find `app.js` and existing middleware
3. Serena: Insert new middleware in correct order
```

### Archon + Memory
Store Archon patterns in memory for reuse:

```markdown
**Memory Key**: `archon_pattern_[pattern_name]`
**Content**: Archon response + our adaptation + lessons learned
```

### Archon + Sequential Thinking
Use sequential thinking to evaluate Archon suggestions:

```markdown
1. **Archon suggests**: Pattern A
2. **Think**: Does Pattern A fit our architecture?
3. **Analyze**: Trade-offs vs. our current approach
4. **Decide**: Use Pattern A or adapt/reject
5. **Document**: Decision rationale in memory
```

## Common Patterns by Technology

### React
- State management patterns
- Hook patterns (custom hooks, useEffect cleanup)
- Context API usage
- Performance optimization (memo, useMemo, useCallback)
- Error boundaries

### Node.js/Express
- Middleware patterns
- Error handling
- Async/await patterns
- Stream handling
- Database connection pooling

### Python
- Async patterns (asyncio, async/await)
- Context managers
- Decorators
- Generator patterns
- Type hints

### Database
- Query optimization
- Index strategies
- Migration patterns
- Connection pooling
- Transaction handling

## Troubleshooting

### Issue: Archon returns no results
**Solutions**:
1. Make query more specific (add library version if relevant)
2. Try alternative phrasing
3. Break down into smaller queries
4. Check if technology is supported in Archon knowledge base

### Issue: Archon example doesn't fit project
**Solutions**:
1. Extract core pattern from example
2. Adapt to project conventions
3. Use sequential thinking to plan adaptation
4. Query for alternative patterns

### Issue: Multiple conflicting patterns from Archon
**Solutions**:
1. Use sequential thinking to evaluate trade-offs
2. Consider project constraints
3. Query for comparison: "[pattern A] vs [pattern B]"
4. Document decision in memory

### Issue: Archon pattern is outdated
**Solutions**:
1. Check library version compatibility
2. Query for newer version: "[library] v[X] [pattern]"
3. Verify with library documentation
4. Update pattern and store in memory

## Advanced Usage

### Pattern Library Building
Store commonly used patterns for quick access:

```markdown
# Memory: archon_pattern_library

## Authentication Patterns
- JWT: [stored pattern]
- OAuth: [stored pattern]

## Error Handling
- Express: [stored pattern]
- React: [stored pattern]

## Testing
- Jest mocks: [stored pattern]
- Integration: [stored pattern]
```

### Team Sharing
Document Archon-retrieved patterns in project:

```
project/
├── docs/
│   └── patterns/
│       ├── authentication.md   # Archon patterns we use
│       ├── error-handling.md
│       └── testing.md
```

### Continuous Learning
After each phase, document successful Archon queries:

```markdown
# Memory: archon_successful_queries

## Phase 1: Architecture
- "Passport.js strategy pattern" → Used for auth design

## Phase 2: Implementation  
- "Express async error handler" → Applied to middleware

## Phase 3: Optimization
- "Redis session optimization" → 40% performance gain
```

## Next Steps

1. **Run Test Query**: Try querying Archon for a pattern you need
2. **Integrate in Phase 1**: Use Archon during next architecture phase
3. **Build Pattern Library**: Store successful patterns in memory
4. **Share Knowledge**: Document patterns team will reuse

## Additional Resources

- **Archon Repository**: https://github.com/coleam00/Archon
- **Dev Branch**: Latest features and patterns
- **Integration Examples**: See Phase 1-3 prompt files
- **Validation**: Use `VALIDATION-CHECKLIST.md` to verify Archon integration
