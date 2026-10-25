# Work with Onthing — Independent Admin/Worker Web App

This is a functional full-stack **development build**, not a production-certified deployment. It includes the approved visual homepage (`/`), account registration/login, role-based Admin and Worker dashboard (`/app`), persistent SQLite database, Socket.IO refresh events, tasks, multi-worker assignment, projects, submissions/approvals, work sessions, earnings summaries, payment records API, chat, notifications and audit records.

## Run

1. Install Node.js 22+ and run `npm install`.
2. Set `JWT_SECRET` to a random 32+ character secret. On PowerShell: `$env:JWT_SECRET = 'replace-this-with-a-unique-long-random-secret'`.
3. Run `npm start` and open `http://localhost:3000`.
4. Click sign in; the first visit prompts you to create an Admin account. Worker accounts register separately. **Only the first four enrolled workers are shown by default**, with View All for the rest.

Set `DB_PATH` to a persistent disk location before deploying to Render; otherwise SQLite data can be lost on redeploy. Configure HTTPS, a private secret, backups, rate limiting, secure operational access and a persistent disk. Never upload real credentials or session files from the original Timee ZIP.

## Important limitations

- **Timee timers are NOT connected.** The API `/api/timee/status` explicitly reports unconfigured. Timer cards show real sessions recorded in this independent app, not values fabricated from Timee. A secure server-to-server read-only Timee adapter must be added after checking Timee's actual API, permissions and worker mapping.
- Earnings are calculated from approved submissions and recorded payments; the payments API is available but a dedicated Admin payment entry UI is not yet wired.
- Worker and Admin chat supports messaging; unread counts, last-seen presence, and push notifications are not implemented.
- Worker accounts are separate from Timee and can be mapped using their Timee ID by an Admin.
- No payment processor is integrated; recorded payments are ledger entries, not money transfers.
- Security, accessibility, concurrency, integration and deployment require further testing before real production use. No end-to-end tests were run in this environment.

## Endpoints

`/api/auth/setup`, `/api/auth/register`, `/api/auth/login`, `/api/me`, `/api/overview`, `/api/workers`, `/api/projects`, `/api/tasks`, `/api/submissions`, `/api/sessions`, `/api/earnings`, `/api/payments`, `/api/messages/:workerId`, `/api/notifications`, `/api/audit`, `/api/timee/status`.
