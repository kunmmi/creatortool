# 📱 Creator Publisher

A mobile application that helps content creators manage cross-platform video posts with platform-specific captions.

## 🎯 Project Overview

Creator Publisher allows content creators to:
- Upload a video once
- Write a single base caption
- Select multiple social media platforms
- Automatically generate platform-specific caption versions
- Save drafts and export captions for manual posting

## 🚀 Tech Stack

- **Frontend**: Expo (React Native) + TypeScript
- **Backend**: Supabase (Auth, Database, Storage)
- **Navigation**: Expo Router
- **State Management**: React Hooks

## 📋 MVP Features

- ✅ Email/password authentication
- ✅ Video upload to Supabase Storage
- ✅ Rule-based caption generation for:
  - Instagram
  - TikTok
  - YouTube Shorts
  - Facebook
- ✅ Draft management
- ✅ Copy/share captions

## 🚧 Out of Scope (MVP)

- ❌ Auto-posting to platforms
- ❌ AI caption generation
- ❌ Video editing/resizing
- ❌ Scheduling posts
- ❌ Web version

## 📁 Project Structure

```
creatortool/
├── app/              # Expo Router screens
├── components/       # Reusable UI components
├── lib/             # Supabase client & helpers
├── types/           # TypeScript type definitions
├── utils/           # Utility functions (caption engine, etc.)
└── docs/            # Project documentation
```

## 🛠️ Setup Instructions

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- Expo CLI
- Supabase account

### Installation

1. Install dependencies:
```bash
npm install
```

2. Set up environment variables:
```bash
cp .env.example .env
# Add your Supabase URL and anon key
```

3. Start the development server:
```bash
npx expo start
```

## 📚 Documentation

- [Project Requirements](./project_requirements.md)
- [Build Plan](./build_plan.md)
- [Development Checklist](./checklist.md)
- [Supabase Setup Guide](./supabase_setup.md)
- [Cursor Development Guide](./cursor_guide.md)

## 🔒 Security

- Row Level Security (RLS) enabled on all database tables
- Users can only access their own posts
- Authenticated uploads only

## 📝 License

Private project - All rights reserved

