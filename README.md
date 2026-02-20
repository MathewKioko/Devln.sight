# DevInsight

DevInsight is an AI-powered GitHub Repository Engineering Intelligence platform that analyzes repositories and provides structured engineering insights including architecture summaries, security scores, and maintainability assessments.

## Features

- GitHub OAuth Authentication
- Repository Management - Connect and select repositories for analysis
- Asynchronous Scanning - Background processing with BullMQ
- AI-Powered Analysis - Static code analysis with structured output
- Real-time Dashboard - View scan history and results
- Usage Tracking - Free and Pro plan support

## Tech Stack

- **Frontend**: Next.js 14 (App Router), TypeScript, Tailwind CSS, ShadCN UI
- **Backend**: Next.js API Routes, PostgreSQL (Supabase)
- **Queue**: BullMQ with Redis (Upstash)
- **AI**: OpenAI API with structured JSON responses

## Project Structure

```
/app                 # Next.js App Router pages and API routes
/components          # React components
/config              # Configuration files
/db                  # Database schemas and repositories
/middleware          # Authentication and rate limiting
/queue               # BullMQ queue configuration
/services            # Business logic (AI, GitHub, Auth, Scan)
/types               # TypeScript type definitions
/utils               # Utilities (encryption, validation, logging)
/worker              # Background worker processes
```

## Getting Started

### Prerequisites

- Node.js 18+
- Supabase account
- Redis (Upstash) account
- GitHub OAuth app
- OpenAI API key (optional)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/MathewKioko/Devlnsight.git
cd Devlnsight
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env.local
```

4. Configure your `.env.local`:
```
# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# GitHub OAuth
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret

# Redis (Upstash)
REDIS_URL=your_upstash_redis_url

# Authentication
JWT_SECRET=your_jwt_secret

# OpenAI (optional - uses static analysis if not provided)
OPENAI_API_KEY=your_openai_api_key
```

5. Set up the database:
- Create a Supabase project
- Run the SQL in `db/schema.sql` to create tables

6. Run the development server:
```bash
npm run dev
```

7. Open http://localhost:3000

## Database Schema

The application uses PostgreSQL with the following tables:

- **users** - User accounts with GitHub tokens
- **repositories** - Connected GitHub repositories
- **scans** - Scan records with status and scores
- **scan_results** - Detailed analysis results
- **usage_tracking** - Monthly usage limits

## API Endpoints

- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user
- `GET /api/repositories` - List user repositories
- `POST /api/scans` - Initiate new scan
- `GET /api/scans` - Get scan history

## Deployment

### Vercel (Recommended)

1. Import the repository on Vercel
2. Add environment variables
3. Deploy

### Docker

```bash
docker-compose up
```

## License

MIT
