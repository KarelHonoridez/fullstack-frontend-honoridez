# AI Assistant Prompt: Angular 21 Full-Stack Integration & Deployment

Copy and paste the entire prompt below into your AI coding assistant to automatically configure your Angular 21 frontend for Stage A (Fake Backend) and Stage B (Remote Backend) integration.

***

```text
You are an expert Angular 21 developer helping me configure, verify, and build my frontend project for my Final Examination deployment. 

The backend has already been fully updated, secured, and connected to my remote MySQL database. It supports dynamic CORS, environment-driven secrets, and testable Swagger documentation.

Please guide me through configuring the Angular frontend to satisfy the following four examination requirements:
1. GitHub Repository Audit (Two distinct repositories, no hardcoded secrets, clean README.md).
2. Dynamic Switching between Stage A (Fake Backend) and Stage B (Remote MySQL API).
3. Production Compilation using Angular CLI.
4. Deep-linking Routing Fix (Redirects/Rewrites) on deployment platforms (e.g., Render).

Please perform the following tasks:

### Task 1: Update Environment Files
Configure the environments to support a `useFakeBackend` toggle and set the dynamic API URL:

1. In "src/environments/environment.ts" (Development):
   - Set "production" to false.
   - Set "apiUrl" to "http://localhost:4000".
   - Add "useFakeBackend" set to true (for Stage A testing) or false (for local integration testing).

2. In "src/environments/environment.prod.ts" (Production):
   - Set "production" to true.
   - Set "apiUrl" to the deployed backend URL (e.g. "https://your-backend-api.onrender.com").
   - Add "useFakeBackend" set to false.

### Task 2: Dynamically Toggle the Fake Backend Provider
In "src/app/app.module.ts", import the environment config and dynamically configure the "fakeBackendProvider" in the "providers" array so that we can easily toggle between mock testing and integration testing without breaking the code:

Instead of:
```typescript
providers: [
    fakeBackendProvider
]
```

Modify it to:
```typescript
import { environment } from '../environments/environment';
...
providers: [
    // Dynamically inject the fake backend interceptor ONLY if useFakeBackend is enabled in environments
    ...(environment.useFakeBackend ? [fakeBackendProvider] : [])
]
```

### Task 3: Implement Render Redirects/Rewrites Rule
Explain to me how to configure the SPA redirect rules in Render/Netlify/Vercel so that deep links (like email verification URLs "/accounts/verify-email?token=...") do not return a 404 error when users refresh or visit them directly.

### Task 4: Provide an Step-by-Step Testing & Verification Plan
Detail the two stages of evaluation (Stage A: Fake Backend and Stage B: Remote Backend integration) and how I should verify:
1. Registration & Verification Mock Email Alerts.
2. Logging in and verifying that the JWT Token is in-memory and the Refresh Token is stored as an HttpOnly cookie.
3. Role-Based Access Control (RBAC) ensuring Admin accounts can view the management page but normal Users are redirected or restricted.

Let's do this sequentially and step-by-step. Let me know when you are ready to begin!
```
