# BUILD PLAN — Creator Publisher (MVP v1.0)

## Global Rules
- Mobile only (Expo + React Native + TypeScript)
- Supabase for Auth, Database, Storage
- Follow PROJECT_REQUIREMENTS.md strictly
- No features outside MVP scope

---

# Milestone 0 — Project Setup

## Task 0.1 Create Expo App
- Initialize Expo project
- Install required dependencies
- Configure Expo Router
- Confirm app runs in Expo Go

Done when: App launches successfully on device.

## Task 0.2 Project Structure
Create folders:
- app/
- components/
- lib/
- types/
- utils/

Add:
- PROJECT_REQUIREMENTS.md
- BUILD_PLAN.md
- .env.example

Done when: Clean structure and app still runs.

---

# Milestone 1 — Supabase Setup

## Task 1.1 Create Supabase Project
- Create project
- Add URL + anon key to .env
- Restart Expo

Done when: Supabase client initializes without errors.

## Task 1.2 Create posts Table
Columns:
- id uuid primary key
- user_id uuid
- caption_original text
- caption_instagram text
- caption_tiktok text
- caption_youtube text
- caption_facebook text
- platforms_selected text[]
- media_url text
- created_at timestamp default now()

Done when: Table visible in dashboard.

## Task 1.3 Enable RLS
Policies:
- SELECT auth.uid() = user_id
- INSERT auth.uid() = user_id
- DELETE auth.uid() = user_id

Done when: Users only see their own data.

## Task 1.4 Storage Bucket
- Create bucket: media
- Enable authenticated upload
- Allow public read

Done when: Upload + retrieve test file works.

---

# Milestone 2 — App Infrastructure

## Task 2.1 Supabase Client
- Create lib/supabase.ts
- Configure AsyncStorage

Done when: auth.getSession() works.

## Task 2.2 Navigation
Create routes:
- index
- sign-in
- sign-up
- create-post
- drafts/index
- drafts/[id]

Done when: All routes accessible.

## Task 2.3 UI Base Components
Create reusable:
- Button
- Input
- Screen wrapper
- Card

Done when: Consistent UI components available.

---

# Milestone 3 — Authentication

## Task 3.1 Sign Up
- Email + password inputs
- Validation
- supabase.auth.signUp

## Task 3.2 Sign In
- Email + password
- supabase.auth.signInWithPassword

## Task 3.3 Auth Guard
- Redirect unauthenticated users
- Implement logout

Done when: Auth flow works end-to-end.

---

# Milestone 4 — Data Layer

## Task 4.1 Types
- Define Post interface
- Define Platform union type

## Task 4.2 CRUD Helpers
Create lib/posts.ts:
- createPostDraft
- listMyDrafts
- getDraftById
- deleteDraft

Done when: CRUD operations function correctly.

---

# Milestone 5 — Media Upload

## Task 5.1 Video Picker
- Install expo-image-picker
- Request permission
- Select video

## Task 5.2 Upload Logic
- Convert URI to blob
- Upload to Supabase Storage
- Return public URL

Done when: Video uploads successfully.

---

# Milestone 6 — Caption Engine

Create utils/captionEngine.ts:
- generateCaptions(baseCaption, platforms)
- Deterministic rules per platform

Done when: Same input → same formatted output.

---

# Milestone 7 — Create Post Screen

- Video picker
- Caption input
- Platform checkboxes
- Generate preview
- Save draft

Done when: Draft saved to database.

---

# Milestone 8 — Drafts List

- Fetch drafts
- Sort newest first
- Delete draft

Done when: List fully functional.

---

# Milestone 9 — Draft Detail

- Load draft by ID
- Display captions per platform
- Copy to clipboard
- Share sheet

Done when: Export works.

---

# Milestone 10 — QA + Polish

- Loading states
- Error handling
- Manual test checklist

Done when: No crashes or blocking errors.

---

# Milestone 11 — Documentation

- Add CURSOR_GUIDE.md
- Add CHECKLIST.md

Done when: Clear dev guardrails exist.

