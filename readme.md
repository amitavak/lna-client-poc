# LNA Client

A single HTML page that tries to fetch from your local machine. When hosted on GitHub Pages (a public HTTPS origin), the browser treats it as a `public` site and enforces **Local Network Access (LNA)** rules on the fetch.

## Files

- `index.html` — the test page (no build step, no dependencies)

## How to deploy to GitHub Pages

1. Create a new GitHub repo (e.g., `lna-poc`).
2. Copy `index.html` into the repo root and push.
3. In the repo, go to **Settings → Pages**.
4. Under **Source**, pick branch `main` and folder `/ (root)`. Save.
5. Wait ~1 minute. Your page will be live at:
   `https://<your-username>.github.io/<repo-name>/`

## How to use

1. Start the local server (see `../lna_server/readme.md`).
2. Open your GitHub Pages URL in **Chrome** or **Edge**.
3. Leave the target URL as `http://localhost:8080/api`.
4. Click **GET**.

## What you'll see

- **Server running without LNA header** → request is **blocked**. The result box turns red and says `BLOCKED / FAILED`. Open DevTools → **Issues** for the LNA explanation.
- **Server running with LNA header on** → request **succeeds**. The result box turns green and shows the JSON response.

## Tips

- Use a fresh **Incognito** window when toggling the server's LNA mode — Chrome caches preflight results for ~5 minutes.
- LNA is enforced in **Chrome and Edge** only. Firefox and Safari will let the request through regardless.
- `localhost` is exempt from mixed-content blocking, so HTTPS → `http://localhost` works. Targeting a private IP like `192.168.1.50` over HTTP will be blocked as mixed content before LNA even fires.
