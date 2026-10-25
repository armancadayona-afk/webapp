# Work with Onthing — Render Web Service

Upload the **contents** of this folder to a GitHub repository, then create a Render **Blueprint** from `render.yaml`, or manually create a Node Web Service.

Manual Render settings:
- Build: `npm ci || npm install`
- Start: `npm start`
- Health check: `/health`
- Node.js: 22 or newer
- Environment: `NODE_ENV=production`, `JWT_SECRET` (32+ random characters), `DB_PATH=/var/data/onth.db`
- Attach a **persistent disk** mounted at `/var/data` (requires a Render plan supporting disks).

The Render Blueprint specifies a paid Starter plan and persistent disk. This is important: without the disk, SQLite records may disappear on redeploy. Render persistent disks cannot be shared between multiple service instances; keep a single instance for this SQLite version. For scaling, migrate to managed PostgreSQL.

Open `/` for homepage and `/app` for Admin/Worker sign-in. On first run, `/app` offers first Admin setup. Register worker accounts after that.

**Not production certified:** Existing Timee live timers are NOT integrated. No worker data is imported from Timee. Payment processor, unread counts and presence are not implemented. This is a deployable development build, not a completed production system. Do not deploy for real payments without additional security review and end-to-end tests.
