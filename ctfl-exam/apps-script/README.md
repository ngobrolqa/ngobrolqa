# Deploying the CTFL Exam backend

This Apps Script is the "backend" for the CTFL mock exam and the admin panel: it grades
submissions against a private answer key, stores registrations/results in a Google Sheet,
and runs the admin panel's article actions. It follows the same pattern as the site's
existing Assessment/Consult forms.

**The repo is public, so `Code.gs` holds no passwords and no answer key.** Both live
outside the repo (see "Secrets" and "Answer key tab" below).

## One-time setup

1. `Code.gs` defaults `SHEET_ID` to the same spreadsheet already used by the
   Assessment/Consult forms — it adds its own tabs there. If you'd rather use a
   separate spreadsheet, create one and replace `SHEET_ID` with its ID (the long string in
   its URL: `https://docs.google.com/spreadsheets/d/`**`THIS_PART`**`/edit`).
2. Go to [script.google.com](https://script.google.com) → **New project**.
3. Delete the default content and paste in this folder's `Code.gs`.
4. **Deploy → New deployment**:
   - Type: **Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Click **Deploy**, authorize when prompted, then copy the `.../exec` URL it gives you.
6. Paste that URL into `CTFL_Mock_Exam.html`, `Admin.html` and `Article.html` (`APPS_SCRIPT_URL`) and commit.
7. Set the secrets and create the answer key tab (next two sections).

The script auto-creates the `CTFL_Registrations`, `CTFL_Results` and `NgobrolQA_Articles`
tabs the first time each is used.

## Secrets (never in the repo)

In the Apps Script editor: **Project Settings** (gear icon) → **Script properties** →
**Add script property**:

| Property | Protects |
|---|---|
| `GATE_PASSWORD` | the exam page's team-preview password |
| `ADMIN_PASSWORD` | the admin panel (a different password on purpose) |

- Use long, random values (a password manager works well); the API is public, so anyone can
  keep guessing, and a short password will eventually fall.
- **Changing a value takes effect immediately, with no redeploy.** After rotating the exam
  password, tell the team the new one; browsers that saved the old one are asked again.
- The pages never contain a password. The visitor types it, the server checks it
  (`verifyGate` / `verifyAdmin`), and the browser keeps what was typed so later calls can send it.
- If a property is missing, every action that needs it refuses all requests (it fails
  closed instead of letting anyone in).

## Answer key tab

Create a tab named **`CTFL_AnswerKey`** in the spreadsheet. Row 1 is the header
`question_id`, `correct`, `points`; then one row per question (multi-answer questions use
`a,e`). If the tab is missing or empty, submissions are refused with a clear error rather
than being scored as zero.

To fill it, generate the rows from the question bank (in the local `ctfl-mock-exam` project):

```
cd ctfl-mock-exam
python3 scripts/export_for_ngobrolqa.py
```

This writes `answer-key.tsv`. Paste its whole contents into cell `A1` of the
`CTFL_AnswerKey` tab. Keep that file out of any public repo.

## Updating the questions later

If `data/questions.csv` changes (e.g. new exam sets), re-run the script above, paste the new
`answer-key.tsv` over the tab's contents, and copy the new
`public/data/questions-public.json` over `ctfl-exam/data/questions.json` in this repo.
The key is read from the sheet on every submission, so **no redeploy is needed** for key changes.

## Redeploying after a `Code.gs` change

**Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy.** The
`/exec` URL stays the same. Forgetting to pick "New version" silently keeps serving the old code.
