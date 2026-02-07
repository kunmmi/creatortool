# CURSOR DEVELOPMENT GUIDE — Creator Publisher MVP

## Purpose
This guide ensures Cursor stays within scope and builds the project step by step without assumptions.

---

## Core Rules
1. Follow PROJECT_REQUIREMENTS.md strictly.
2. Follow BUILD_PLAN.md in order.
3. Do NOT add features not listed.
4. Do NOT implement auto-posting.
5. Do NOT implement AI rewriting.
6. Do NOT introduce web version.
7. Do NOT introduce subscription logic.

---

## Implementation Rules
- Use TypeScript only.
- Use functional React components.
- Use Expo Router.
- Use Supabase only (no custom backend).
- No Redux or external state managers.

---

## Development Flow
Before writing code:
1. Identify current milestone.
2. Identify current task.
3. Only implement that task.
4. Confirm "Done when" criteria.
5. Stop and wait for next instruction.

---

## Code Quality Rules
- No unused variables.
- No console.log in production code.
- Proper error handling for async calls.
- Clean separation: components/, lib/, utils/, types/.

---

## Safety Constraints
If a request introduces features outside MVP scope, refuse and reference PROJECT_REQUIREMENTS.md.

---

## Completion Criteria
Only consider MVP complete when all milestones in BUILD_PLAN.md are finished and QA checklist passes.

