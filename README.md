# Treasury Notes

A standalone showcase page for daily treasury LinkedIn posts by **The Happy Analyst**.
It is a single, self-contained `index.html` — all styles, fonts, and scripts are inlined.
No build step, no dependencies, no framework.

---

## Deploy (GitHub → Vercel)

1. Push this folder's contents to a new GitHub repo (e.g. `treasury-notes`).
   `index.html` must be at the **root** of the repo.
2. In Vercel: **Add New → Project → Import** the repo.
3. Framework Preset: **Other** (static). Leave Build Command and Output Directory **empty**.
4. **Deploy.** It goes live at `your-project.vercel.app`.

### Custom subdomain
Vercel → Project → **Settings → Domains** → add `notes.yourdomain.com`
and create the DNS record Vercel shows you.

### Link from the main Next.js site
It's a separate deployment, so use a plain anchor (not `next/link` routing):

```jsx
<a href="https://notes.yourdomain.com" target="_blank" rel="noopener">
  Treasury Notes
</a>
```

---

## Updating the page

This is a static file, so updates are one commit:

1. Replace `index.html` with the newly generated version.
2. `git commit -m "Update posts" && git push`
3. Vercel auto-deploys the new version.

`vercel.json` sets `Cache-Control: must-revalidate` on `index.html`,
so visitors always get the latest version after a redeploy.

---

## How the content & review workflow works

- **The 20 posts baked into `index.html` are what every visitor sees** —
  6 marked **Live** (linked to the real LinkedIn posts) and 14 marked **Exclusive**.
- **Review mode** (type `review` on the page, or press `Esc` to exit) is a private,
  client-side tool: add a post, then approve it as **Publish to LinkedIn**
  (opens LinkedIn's composer pre-filled) or **Keep exclusive**.
- Posts you add and decisions you make in review mode are saved in **your browser only**
  (localStorage). They do **not** appear for visitors.
- To make a new post permanent for everyone: have it baked into `index.html`,
  then redeploy (commit + push).

---

## Files

| File           | Purpose                                            |
|----------------|----------------------------------------------------|
| `index.html`   | The entire page (self-contained).                  |
| `vercel.json`  | Static hosting config + cache headers.             |
| `README.md`    | This file.                                         |
