# Coding Agent - Workspace

Save all coding outputs here for Orchestrator coordination.

## Files

### architecture.md
Component designs and integration points:
- Component structure
- **Exact symbols**: functions, classes, hooks
- **Exact imports**: with line numbers
- Integration points with existing code

### implementation.md
Actual code changes with exact references:
- **File paths with line numbers**
- **Symbols**: functions, variables, classes created/modified
- **Imports**: exact import statements
- **Hooks**: React hooks used (with lines)
- **Workflow**: Step-by-step execution flow
- **Test results**: Terminal test output

## Format Example

```markdown
## Authentication Token Refresh

### Architecture
Component: TokenRefreshService
Location: src/auth/refresh.ts
Symbols:
- refreshToken (async function)
- isTokenExpired (helper function)
- TOKEN_REFRESH_THRESHOLD (constant)

Integration:
- Called by src/api/interceptor.ts:34
- Uses src/storage/token.ts:12 (getToken, setToken)

### Implementation

**File: src/auth/refresh.ts**

Lines 1-5: Imports
```typescript
import { jwtDecode } from 'jwt-decode';
import { api } from '../api/client';
import { getToken, setToken } from '../storage/token';
```

Lines 10-25: refreshToken function
```typescript
export async function refreshToken(): Promise<string> {
  const token = getToken();
  if (!isTokenExpired(token)) return token;
  
  const response = await api.post('/auth/refresh');
  setToken(response.data.token);
  return response.data.token;
}
```

Lines 30-35: isTokenExpired helper
```typescript
function isTokenExpired(token: string): boolean {
  const decoded = jwtDecode(token);
  return decoded.exp < Date.now() / 1000;
}
```

**Workflow**:
1. API request fails (401) → interceptor.ts:34
2. Call refreshToken() → refresh.ts:10
3. Check expiry → refresh.ts:31
4. Request new token → refresh.ts:23
5. Store new token → storage/token.ts:12
6. Retry original request → interceptor.ts:40

**Test Results**:
```bash
$ node -e "const { refreshToken } = require('./dist/auth/refresh'); ..."
✓ Token refresh successful
✓ New token stored
✓ Original request retried
```

### Changes
- Created: src/auth/refresh.ts (35 lines)
- Modified: src/api/interceptor.ts:34 (added refresh call)
- Modified: src/types/auth.ts:8 (added TokenPayload interface)
```
