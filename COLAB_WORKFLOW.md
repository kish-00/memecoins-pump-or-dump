# Memecoins: Pump or Dump — Colab + GitHub + Drive Workflow

Same pattern as your Zindi/Opencode sessions: **author in a Colab notebook, persist to Google Drive, version code on GitHub**, no copy-pasting from chat.

## Prerequisites (one-time)
- Google account with Colab + Drive
- GitHub account (`kish-00`) + `gh` CLI or git configured
- Kaggle account + API token (`kaggle.json` from kaggle.com → Account → API → Create New API Token)
- Telegram linked to `@pumpfun_competition_bot` (done: `kinuthiawachira`)

## Step 0 — Create the GitHub repo
```bash
cd /home/kish/Documents/projects/kaggle/memecoins-pump-or-dump
git init
git add -A
git commit -m "Initial: Colab workflow skeleton for Memecoins"
git branch -M main
gh repo create kish-00/memecoins-pump-or-dump --public --source=. --remote=origin --push
```

## Step 1 — Open the notebook in Colab
1. Go to https://colab.research.google.com/
2. **File → Upload notebook** → select `notebooks/01_setup_and_baseline.ipynb`
3. Rename it (e.g. `memecoins-baseline-YYYYMMDD`)
4. **Runtime → Change runtime type → CPU** (free tier is fine; no GPU needed)

## Step 2 — Mount Google Drive
Run the first cell in the notebook. It will:
- Mount `/content/drive`
- Create a project folder on Drive: `/content/drive/MyDrive/kaggle/memecoins-pump-or-dump/`
- Symlink the workspace so outputs persist even if Colab disconnects

## Step 3 — Kaggle API auth
In Colab, upload your `kaggle.json` to the files sidebar (left folder icon), then run the auth cell:
```python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
!kaggle competitions download -c memecoins-pump-or-dump -p /content/data
!unzip -o memecoins-pump-or-dump.zip -d /content/data
```

## Step 4 — Develop in the notebook
- Explore data (`/content/data/`)
- Engineer features
- Train baseline model (CPU)
- Write `submission.csv` (one `tp` value per token, 0 = skip)

## Step 5 — Save outputs to Drive
The notebook automatically copies:
- `submission.csv` → Drive project folder
- The notebook itself → Drive project folder
- Logs/metrics → Drive project folder

This persists across Colab sessions.

## Step 6 — Push code to GitHub
```bash
cd /home/kish/Documents/projects/kaggle/memecoins-pump-or-dump
git add notebooks/ requirements.txt README.md COLAB_WORKFLOW.md
git commit -m "Add Colab baseline notebook and workflow"
git push origin main
```
**Do not commit** `data/`, `outputs/`, or `kaggle.json` (they're in `.gitignore`).

## Step 7 — Submit to Kaggle
1. Download `submission.csv` from Colab (files sidebar → right-click → Download) or from your Drive folder
2. Go to https://www.kaggle.com/competitions/memecoins-pump-or-dump/submit
3. Upload `submission.csv`
4. Submission description: your real approach (not the Telegram code — that was only for account linking)

## Daily loop (before Dec 1, 00:00 UTC freeze)
- Retrain on latest 30 days → new `submission.csv`
- Upload to Kaggle (max 5 submissions/day)
- Optionally send notebook to `@pumpfun_competition_bot` for faster scoring

## Deadlines
- **Kaggle freeze:** Nov 30, 2026, 23:59 UTC
- **Last bot upload that counts:** Dec 1, 2026, 00:00 UTC
- **Scoring:** Dec 1–14, 2026
