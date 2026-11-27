# AI Free — Gemini Script Generator v0.3

This update adds real Google Gemini script generation through a Vercel serverless function. The Gemini API key is read only on the server from `process.env.GEMINI_API_KEY`; it is never embedded in `index.html` or returned to the browser.

## Deploy the update to the existing Vercel project

1. Download and extract this ZIP.
2. Open your GitHub repository: https://github.com/dilancreater3/ai-free
3. Upload/replace the extracted project files at the repository root. Keep `index.html` at the top level and include the `api` folder.
4. Commit the changes to the `main` branch.
5. Open Google AI Studio: https://aistudio.google.com/app/apikey
6. Create or copy a Gemini API key. Do not paste it into GitHub, `index.html`, or this chat.
7. In Vercel, open the existing `ai-free` project → Settings → Environment Variables.
8. Add:
   - Name: `GEMINI_API_KEY`
   - Value: your Gemini API key
   - Environments: Production, Preview, Development (at least Production)
9. Optionally add `GEMINI_MODEL` with value `gemini-3.8-flash`. If omitted, this is the default.
10. Save, then go to Deployments and redeploy the latest commit (or let the GitHub push trigger a deployment).
11. Test the website and then visit `/api/health`.

## Test

- Website: your Vercel production URL
- Health check: `https://YOUR-PROJECT.vercel.app/api/health`

Expected health response includes `"ok": true`, `"scriptProvider": "Google Gemini"`, and `"configured": true` after the key is saved.

In the website, enter a topic, select English, Sinhala, or English + Sinhala, choose video type/duration/style, then click **Generate project & script**. A successful response should include a full script with a hook, voiceover, scene plan, on-screen text, music suggestions and CTA.

## Security

- Never commit a real `.env` file or API key.
- Do not add `GEMINI_API_KEY` to frontend JavaScript or any `NEXT_PUBLIC_`/`VITE_` variable.
- The browser calls only `/api/project`; the Vercel function calls Gemini.
- If the key was ever exposed publicly, revoke it in Google AI Studio and create a replacement.
- Set usage limits/monitor usage in Google AI Studio. API quotas and pricing depend on your account and selected model.

## Troubleshooting

- `Gemini is not configured yet`: add `GEMINI_API_KEY` in Vercel and redeploy.
- `429`: rate limit or quota reached; check Google AI Studio usage/billing.
- `API key not valid`: verify the key and ensure it is enabled for Gemini API.
- `404 /api/project`: ensure the `api` folder is at the repository root and the Vercel project Root Directory points to the repository root.
- `404 /api/health`: same root-directory/API-folder check.

## Current scope

This update implements real AI script generation only. It does not yet generate voice audio, scene images, rendered video or MP4 files. Those are separate provider integrations and are not claimed as complete.
