# AI Free — Vercel Deployment Starter

A bilingual (English/Sinhala) static web app with Vercel serverless API routes. This is a deployable starter MVP, not yet a full AI video-rendering service.

## Deploy to Vercel (free subdomain)

1. Download and unzip `ai-free-vercel.zip`.
2. Create a GitHub account if you do not already have one.
3. On GitHub, create a **new private repository** named `ai-free`.
4. Upload the files and folders inside the extracted ZIP directly to the repository root. Make sure `index.html`, `api/`, `vercel.json`, and `package.json` are visible at the top level. Do not upload an extra enclosing folder. Commit the files.
5. Sign in at https://vercel.com/ using GitHub.
6. Choose **Add New → Project**, import the `ai-free` repository, and click **Deploy**.
7. No build command or environment variables are required for this starter. Vercel will provide a URL similar to `https://ai-free-yourname.vercel.app`.
8. Open the URL and test the project generator. Test the API at `https://YOUR-URL/api/health`.

## Local development (optional)

Requires Node.js 20+ and a Vercel account/CLI:

```bash
npm install -g vercel
npm install
vercel dev
```

Open the local URL shown by Vercel CLI.

## Included

- Responsive AI Free dashboard
- English, Sinhala and bilingual script templates
- Video format, type, duration and visual-style settings
- Project script generation endpoint (`POST /api/project`)
- Health endpoint (`GET /api/health`)
- Copy/download script and browser speech preview
- Vercel serverless functions and basic security headers

## Important limitations

This deployment creates a working website and draft-script workflow. It does **not** yet generate real AI voice files, AI images, rendered videos or downloadable MP4s. Those require external AI providers, secure server-side API credentials, job processing, storage, and usually usage-based billing. Login, database, payment processing and user project persistence are also not included yet.

Do not put API secrets in `index.html` or commit them to GitHub. Add secrets in Vercel → Project → Settings → Environment Variables after the provider integrations are implemented.
