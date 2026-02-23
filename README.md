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
- **Database**: PostgreSQL with Prisma ORM
- **Deployment**: Vercel

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- PostgreSQL database (local or cloud)

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

Edit `.env` and add:
- `DATABASE_URL`: Your PostgreSQL connection string (e.g., `postgresql://user:password@localhost:5432/jobtracker?schema=public`)
- `NEXTAUTH_SECRET`: Generate one with `openssl rand -base64 32`
- `NEXTAUTH_URL`: `http://localhost:3000` for local development

4. Set up the database:
```bash
npx prisma generate
npx prisma migrate dev --name init
```

**Important**: Make sure to commit and push the migration files created in `prisma/migrations/` to your repository before deploying to Vercel.

5. Run the development server:
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Local PostgreSQL Setup Options

**Option 1: Docker (Recommended)**
```bash
docker run --name jobtracker-postgres -e POSTGRES_PASSWORD=password -e POSTGRES_DB=jobtracker -p 5432:5432 -d postgres
```

**Option 2: Install PostgreSQL locally**
- Install PostgreSQL from [postgresql.org](https://www.postgresql.org/download/)
- Create a database: `createdb jobtracker`
- Use connection string: `postgresql://your_username:your_password@localhost:5432/jobtracker?schema=public`

## Deployment to Vercel

1. Push your code to GitHub

2. Import your repository in Vercel

3. **Add Vercel Postgres Database:**
   - In your Vercel project dashboard, go to the "Storage" tab
   - Click "Create Database" and select "Postgres"
   - This will automatically add the `DATABASE_URL` environment variable

4. **Add other environment variables in Vercel dashboard:**
   - `NEXTAUTH_URL`: Your Vercel deployment URL (e.g., `https://your-app.vercel.app`)
   - `NEXTAUTH_SECRET`: A secure random string (generate with `openssl rand -base64 32`)

5. **Deploy!** The build will automatically:
   - Generate Prisma Client
   - Run database migrations
   - Build your Next.js app

**Note**: The `DATABASE_URL` from Vercel Postgres is automatically provided and includes SSL, so no additional configuration is needed.

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
