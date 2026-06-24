**CONFIGURATION:**
- Chosen Database: [PostgreSQL / MongoDB / Other]
- Primary Language: TypeScript

You are an expert full-stack + DevOps engineer.

**Inputs:**
- Problem Summary: [paste problem_summary.md]
- Design Decisions: [paste design_decisions.md]

**Task:**
Create a complete database setup using Docker with smart package manager integration.

**Step 1: Detect Package Manager**
- Check if the project already uses npm, pnpm, or yarn (look for package-lock.json, pnpm-lock.yaml, or yarn.lock).
- If no lockfile exists, default to **pnpm**.

**Deliverables:**

1. `docker-compose.yml` – Properly configured with volumes, healthcheck, and secure defaults.

2. Update `package.json` with these scripts (using the detected package manager):
   - `"db:start"`
   - `"db:stop"`
   - `"db:restart"`
   - `"db:check"`
   - `"db:logs"`

3. `scripts/check-db-connection.ts` – Robust TypeScript connection test script.

4. `.env.example` – With all required database variables.

5. Update `README.md` – Add or expand a section called `## Development Setup` that includes:
   - Technical requirements
   - Technologies & tools used
   - Instructions for starting the database (`pnpm run db:start` or equivalent)
   - How to check connection
   - How to stop the database

**Output Flow:**
- First, tell me which package manager was detected (or that pnpm will be used).
- Then, show the full content of every file you will create or update.
- Finally, create / update all files in the project.

Make the setup clean, secure, and developer-friendly.