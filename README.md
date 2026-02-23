# Job Application Tracker

A modern web application for tracking job applications and their status, built with Next.js, TypeScript, and Tailwind CSS.

## Features

- 🔐 User authentication (sign up/sign in)
- 📊 Dashboard with application statistics
- ➕ Add, edit, and delete job applications
- 📱 Responsive design
- 🎨 Modern UI with Tailwind CSS

## Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Authentication**: NextAuth.js
- **Database**: SQLite with Prisma ORM
- **Deployment**: Vercel

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd job-app-tracker
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
```

Edit `.env` and add your `NEXTAUTH_SECRET` (you can generate one with `openssl rand -base64 32`).

4. Set up the database:
```bash
npx prisma generate
npx prisma migrate dev --name init
```

5. Run the development server:
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Deployment to Vercel

1. Push your code to GitHub
2. Import your repository in Vercel
3. Add environment variables in Vercel dashboard:
   - `DATABASE_URL`: For production, use a PostgreSQL database (Vercel Postgres recommended)
   - `NEXTAUTH_URL`: Your Vercel deployment URL
   - `NEXTAUTH_SECRET`: A secure random string
4. Deploy!

**Note**: For production, you'll need to update the Prisma schema to use PostgreSQL instead of SQLite. Update `datasource db` in `prisma/schema.prisma` to:
```prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

Then run migrations in production.

## Project Structure

```
job-app-tracker/
├── app/
│   ├── api/          # API routes
│   ├── globals.css   # Global styles
│   ├── layout.tsx    # Root layout
│   └── page.tsx      # Home page
├── components/       # React components
├── prisma/          # Prisma schema and migrations
└── public/          # Static assets
```

## License

MIT
