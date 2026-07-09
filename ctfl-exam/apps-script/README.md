# Deploying the CTFL Exam backend

This Apps Script is the "backend" for the CTFL mock exam pages — it holds the private
answer key, grades submissions, and stores registrations/results in a Google Sheet.
It follows the same pattern as the site's existing Assessment/Consult forms.

## One-time setup

1. `Code.gs` defaults `SHEET_ID` to the same spreadsheet already used by the
   Assessment/Consult forms — it'll just add two new tabs there. If you'd rather use a
   separate spreadsheet, create one and replace `SHEET_ID` with its ID (the long string in
   its URL: `https://docs.google.com/spreadsheets/d/`**`THIS_PART`**`/edit`).
2. Go to [script.google.com](https://script.google.com) → **New project**.
3. Delete the default content and paste in this folder's `Code.gs`.
4. **Deploy → New deployment**:
   - Type: **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy**, authorize when prompted, then copy the `.../exec` URL it gives you.
6. Paste that URL into `CTFL_Mock_Exam.html`'s `APPS_SCRIPT_URL` constant and commit.

The script auto-creates two tabs the first time each is used: `CTFL_Registrations` and
`CTFL_Results`. No manual header setup needed.

## Updating the answer key later

If `data/questions.csv` changes in the `ctfl-mock-exam` project (e.g. new exam sets added),
regenerate and re-paste the key:

```
cd ctfl-mock-exam
python3 scripts/export_for_ngobrolqa.py
```

This rewrites `answer-key.gs.txt` — copy its one line into `Code.gs`'s `ANSWER_KEY` constant
(replacing the old one), then also copy the new `public/data/questions-public.json` over
`ctfl-exam/data/questions.json` in this repo. Redeploy the Apps Script (**Deploy → Manage
deployments → Edit → New version**) for the answer key change to take effect.
