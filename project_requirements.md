# 📱 Creator Publisher
## Project Requirements Document (PRD)
### Version 1.0 — MVP Scope

---

# 1. Project Overview

Creator Publisher is a mobile application that allows content creators to:

- Upload a video once
- Write a single base caption
- Select multiple social media platforms
- Automatically generate platform-specific caption versions
- Save drafts
- Export captions for manual posting

⚠️ This MVP does NOT include auto-posting to social media platforms.

The goal of this version is validation and usability.

---

# 2. Product Vision

Create a mobile-first tool that simplifies cross-platform posting for short-form video creators by reducing repetitive formatting work.

The app must:
- Be simple
- Be fast
- Be mobile-native
- Focus on creators, not enterprise teams

---

# 3. MVP Scope (Strict Boundaries)

## 3.1 Included Features

### Authentication
- Email + password sign up
- Email + password sign in
- Persistent session
- Logout
- Supabase Auth only

---

### Create Post
User can:
- Select video from device gallery
- Enter base caption
- Select platforms:
  - Instagram
  - TikTok
  - YouTube Shorts
  - Facebook
- Tap "Generate"
- App generates caption versions
- Tap "Save Draft"

---

### Caption Adaptation Engine (Rule-Based Only)

Caption transformation must follow deterministic rules (no AI).

#### Instagram Rules
- Keep full caption
- Add 8–15 hashtags
- Add line breaks every 2–3 sentences
- Allow longer format

#### TikTok Rules
- Shorten caption
- First line acts as hook
- 3–6 hashtags maximum
- Casual formatting

#### YouTube Shorts Rules
- First line becomes title-style
- 2–5 hashtags
- Add CTA such as "Subscribe for more"

#### Facebook Rules
- Conversational tone
- 3–5 hashtags
- Minimal line breaks

---

### Draft Management
User can:
- View all saved drafts
- See:
  - Video thumbnail
  - Created date
  - Platforms selected
- Tap to open draft
- Copy caption per platform
- Delete draft

Drafts must be sorted by newest first.

---

### Video Handling
- User selects video from gallery
- Video uploads to Supabase Storage
- Store public URL in database
- No video editing in MVP
- No resizing
- No compression
- No subtitle generation

---

### Export Functionality
User must be able to:
- Copy caption to clipboard
- Share caption using native share sheet
- Optionally download caption as .txt file

---

# 4. Explicitly Out of Scope (Do NOT Implement)

- Auto-posting to platforms
- OAuth account connections
- Video resizing
- AI caption generation
- Scheduling posts
- Analytics
- Subscription billing
- Admin dashboard
- Web version
- Push notifications
- Trend detection
- Hashtag research engine

If not listed in Included Features, it must NOT be implemented.

---

# 5. Technical Stack Requirements

## Frontend (Mobile)
- Expo (React Native)
- TypeScript
- Expo Router
- Functional components
- React Hooks only

## Backend
- Supabase

Supabase is used for:
- Authentication
- Database
- Storage

No custom backend server allowed.

---

# 6. Database Schema

## Table: posts

| Column Name | Type | Notes |
|-------------|------|-------|
| id | uuid | Primary key |
| user_id | uuid | Foreign key (auth.users) |
| caption_original | text | Base caption |
| caption_instagram | text | Generated |
| caption_tiktok | text | Generated |
| caption_youtube | text | Generated |
| caption_facebook | text | Generated |
| platforms_selected | text[] | Array of platform names |
| media_url | text | Supabase storage URL |
| created_at | timestamp | Default now() |

---

# 7. Storage Configuration

Bucket Name: `media`

Permissions:
- Authenticated users can upload
- Public read allowed for MVP

File naming format:
```
{user_id}/{timestamp}-{filename}
```

---

# 8. Application Screens

## 8.1 Auth Screens
- Sign Up
- Sign In

## 8.2 Home Screen
- Button: Create New Post
- Button: View Drafts
- Logout button

## 8.3 Create Post Screen
- Video picker
- Caption input
- Platform checkboxes
- Generate button
- Save Draft button

## 8.4 Drafts Screen
- FlatList of drafts
- Tap to view
- Delete option

## 8.5 Draft Detail Screen
- Video preview (optional)
- Caption per platform
- Copy buttons
- Back navigation

---

# 9. State Management

- Use React Hooks
- Supabase queries directly
- No Redux
- No Zustand

Keep state minimal and local.

---

# 10. Security Requirements

- Supabase Row Level Security (RLS) must be enabled.
- Users can only access their own posts.

Required RLS policy:
```
auth.uid() = user_id
```

Must apply for:
- SELECT
- INSERT
- DELETE

---

# 11. UI Requirements

- Clean minimal UI
- No heavy animations
- Consistent spacing and padding
- Rounded buttons
- No clutter
- Dark mode optional

---

# 12. Error Handling Requirements

App must handle:
- Upload failure
- Network issues
- Authentication errors
- Empty caption
- No platform selected
- No video selected

Display clear, friendly error messages.

---

# 13. Performance Requirements

- Draft save under 3 seconds
- Show upload progress indicator
- Non-blocking UI during uploads
- Loading states for all async operations

---

# 14. Code Standards

- TypeScript only
- No unused variables
- No console.log in production
- Folder structure:
  - components/
  - lib/
  - app/

Reusable logic must be extracted into helper files.

---

# 15. Future Roadmap (Not Part of MVP)

## Phase 2
- AI caption rewriting
- Auto-posting
- Scheduling
- Video resizing
- Analytics

## Phase 3
- Monetization
- Subscriptions
- Agency accounts
- Web dashboard

---

# 16. Success Criteria

The MVP is complete when:

A user can:
- Sign up
- Upload video
- Write caption
- Select platforms
- Generate platform versions
- Save draft
- View drafts
- Copy captions

And:
- No crashes
- No major UI bugs
- RLS working correctly

---

# 17. Non-Functional Constraints

- Must work on iOS and Android
- Must run in Expo Go during development
- Must be deployable via Expo build later
- No native modules requiring ejection

---

# 18. Developer Constraints for Cursor

Cursor must:
- Follow this document strictly
- Not introduce extra features
- Not assume auto-posting
- Not assume OAuth integration
- Not introduce web version
- Not add paid features
- Not implement features outside MVP scope

---

# 19. Versioning

Current Version: MVP v1.0  
Status: Development Phase  
Goal: Validate product-market fit

---

**End of Document**

