### 🎯 Essential Context (Read First)
- **Check `PLANNING.md`** for architecture, tech stack, and project goals
- **Check `TASK.md`** before starting - add new tasks with date if missing
- **Follow existing patterns** in codebase rather than introducing new paradigms
- **Never assume missing context** - ask questions if unclear

### 🏗️ Tech Stack & Architecture
- **Frontend**: Next.js 14 + TypeScript + Tailwind + Radix UI
- **Backend**: Express.js + tRPC (end-to-end type safety)
- **Database**: Neon PostgreSQL + Drizzle ORM
- **Auth**: Clerk (sync user data to local DB)
- **Payments**: Polar webhooks
- **Jobs**: BullMQ for background processing

### 📁 Code Standards
- **File limit**: 500 lines max - split into modules if exceeded
- **Imports**: External packages → internal modules → types
- **Naming**: `camelCase` functions, `PascalCase` components/types, `kebab-case` files
- **TypeScript**: Strict mode, explicit types for functions
- **Validation**: Zod schemas for all API inputs and DB operations

### 🧪 Testing Requirements
- **Required for all new features**: Jest/Vitest unit tests
- **Test structure**: `/tests` mirror app structure, `__tests__` next to components
- **Minimum coverage**: Expected behavior + edge case + error handling

### 🔌 Integration Patterns
#### Clerk Auth
- Sync user data to local DB via webhooks (`user.created/updated/deleted`)
- Use Clerk middleware for protected routes

#### Polar Billing
- Handle webhooks: `subscription.created/updated`, `invoice.paid`
- Check tier limits before allowing actions

#### Database
- Use transactions for multi-table operations
- Connection pooling with environment configs

### 🚀 Development Workflow
1. **Types/schemas first** (Zod + TypeScript interfaces)
2. **Database layer** (Drizzle queries + migrations)
3. **tRPC procedures** (API logic + error handling) 
4. **React components** (proper state management)
5. **Tests** (unit tests for each layer)

### ✅ Task Management
- **Mark completed tasks** in `TASK.md` immediately
- **Document new sub-tasks** under "Discovered During Work"
- **Update `README.md`** when adding features/dependencies

### 🔒 Security Essentials
- Never commit secrets (use `.env.local`)
- Implement API rate limiting
- Proper error handling with user-friendly messages
- Input validation on all endpoints

### 🧠 AI Assistant Rules
- **Never hallucinate** packages/APIs - verify before suggesting
- **Confirm file paths** exist before referencing
- **Consider full-stack impact** of changes
- **Ask questions** if project structure unclear