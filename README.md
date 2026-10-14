# ClearPaper (pilot build)

Static site + one Netlify Function that calls the Claude API.

## Deploy
1. Put this folder in a GitHub repo and connect it to Netlify, or run `netlify deploy --prod` with the Netlify CLI.
   (Plain drag-and-drop of the folder may not deploy the function.)
2. Netlify > Site settings > Environment variables:
   - `ANTHROPIC_API_KEY`  your key (never put it in the HTML)
   - `ACCESS_CODE`        a code you give participants. Without it anyone who finds the URL can spend your API credit.
   - `CLAUDE_MODEL`       optional, default `claude-sonnet-5-5`. Use `claude-haiku-5-5` if requests time out.
3. Redeploy after setting variables.

If you see timeouts: Netlify synchronous functions default to 10 s. Raise the function timeout in Netlify's site settings (up to 26 s on most plans), or switch to the Haiku model.

## Before the pilot
1. Open `https://YOUR-SITE/#researcher`, enter the access code, press "Generate all".
2. Preview every output. Have someone who knows these offices check them for wrong or invented content.
3. Download `frozen.json`, replace `public/frozen.json`, redeploy. Now everybody sees identical explanations.
4. Replace the grey consent placeholder in the Study tab with your ethics-approved text.
5. Send participants: `https://YOUR-SITE/?tab=study&code=YOURCODE`
   Optional: `&pair=AC` forces the two conditions (A, B or C) for that link, to balance arms.

## Conditions
- A: original notice only (control)
- B: original + faithful plain translation (changes language, not the task)
- C: original + action-first explanation (steps, deadlines, documents, uncertainty flags, source quotes)

## Data
Responses go to Netlify Forms (form `pilot-results`): Site > Forms > Export CSV. The `payload` column is JSON
(demographics, per-question answers, correctness, times, confidence, outside help, preference).
Free plans cap the number of submissions per month; check your plan.
Each participant does two different notices under two different conditions (within-subject).

## Real documents
The "Understand a notice" tab sends real uploads to the AI service. Do not use it with study participants' real documents unless your ethics approval covers it.
