# SUPABASE SETUP GUIDE — Creator Publisher MVP

## 1. Create Project
- Go to Supabase dashboard
- Create new project
- Copy Project URL
- Copy Anon Public Key

Add to .env:
EXPO_PUBLIC_SUPABASE_URL=
EXPO_PUBLIC_SUPABASE_ANON_KEY=

Restart Expo after adding.

---

## 2. Create posts Table (SQL)

```sql
create table public.posts (
  id uuid primary key default gen_random_uuid(),
  user_id uuid not null references auth.users(id) on delete cascade,
  caption_original text not null,
  caption_instagram text,
  caption_tiktok text,
  caption_youtube text,
  caption_facebook text,
  platforms_selected text[] not null default '{}',
  media_url text not null,
  created_at timestamp with time zone default now()
);
```

---

## 3. Enable RLS

```sql
alter table public.posts enable row level security;
```

---

## 4. RLS Policies

SELECT:
```sql
create policy "Users can view own posts"
on public.posts for select
using (auth.uid() = user_id);
```

INSERT:
```sql
create policy "Users can insert own posts"
on public.posts for insert
with check (auth.uid() = user_id);
```

DELETE:
```sql
create policy "Users can delete own posts"
on public.posts for delete
using (auth.uid() = user_id);
```

---

## 5. Storage Bucket
- Create bucket: media
- Public read enabled
- Authenticated upload allowed

File path format:
{user_id}/{timestamp}-{filename}

---

## 6. Test Checklist
- Insert test row manually
- Confirm RLS blocks other users
- Upload file and retrieve public URL

Done when all tests pass.

