# KetanXYZ Drive

Private personal cloud storage. Upload files from one device, sign in from another, and download them.

## What you can do

- Create an account (email + password, Google, or X)
- Upload images, video, PDFs, documents, and zip files
- Organize with folders, search, rename, sort, and delete
- Download on iPhone Safari (Save to Files / share sheet), Android, Windows, and Mac
- Light and dark mode, storage meter, account settings

Files are stored on the server (Postgres), not in the browser. Each account can only see its own files.

## Stack

- TanStack Start (React) frontend + API
- Better Auth (hashed passwords, sessions)
- Postgres (Neon in production, embedded Postgres in preview)
- File bytes stored as authenticated blobs in the database

Maximum upload size is 8 MB per file. Each account has a 1 GB quota.

## Deployed on this platform

When this app is published:

1. A Postgres database is provisioned automatically.
2. Auth secrets are injected — do not put keys in the frontend.
3. You get a public URL. Open it from any phone or computer, sign in, and your files are there.

## Use from another phone

1. Open the public website URL.
2. Sign in with the same account.
3. Tap a file → Download. On iPhone, use **Share / Save to Files** if Safari previews the file instead of saving it.

## Self-host notes

You need:

- A Node 22 host (Vercel is the build target)
- A Postgres database (`DATABASE_URL`)
- Auth is already wired; the platform injects credentials on deploy

Schema lives in `migrations/`. Never put secrets in client code.
