# Slackoff

A Slack-style team chat app built with Next.js and Convex. Convex provides the database, real-time queries and authentication, so messages appear for every member without a separate WebSocket server.

## Features

- **Auth:** email and password, GitHub or Google sign-in via Convex Auth
- **Workspaces:** create, rename and delete; invite people with a join code that admins can regenerate
- **Roles:** admin and member per workspace
- **Channels:** create, rename and delete channels inside a workspace
- **Messages:** rich-text editor (Quill) with emoji picker and image uploads to Convex storage

Threads, direct messages and reactions are modelled in `convex/schema.ts` but do not have UI yet.

## Stack

Next.js 14 · TypeScript · Convex · Convex Auth · Jotai · Tailwind CSS · shadcn/ui

## Getting started

Requires Node.js 18+ and a free [Convex](https://convex.dev) account.

```bash
npm install
npx convex dev   # creates a deployment and writes NEXT_PUBLIC_CONVEX_URL to .env.local
npm run dev      # in a second terminal
```

Open http://localhost:3000.

To enable GitHub and Google sign-in, follow the [Convex Auth OAuth setup](https://labs.convex.dev/auth/config/oauth) and set `AUTH_GITHUB_ID`, `AUTH_GITHUB_SECRET`, `AUTH_GOOGLE_ID` and `AUTH_GOOGLE_SECRET` on the Convex deployment.

## Project structure

```
convex/        schema, queries, mutations and auth config
src/app/       routes: auth, join/[workspaceId], workspace/[workspaceId]/channel/[channelId]
src/features/  feature modules (auth, workspaces, channels, members, messages, upload)
```
