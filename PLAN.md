# Memecoins: Pump or Dump — Execution Plan

## Timeline (as of Nov 14, 2026)
- **Phase 1:** Setup & baseline (Nov 14–16)
- **Phase 2:** Feature engineering & model (Nov 17–23)
- **Phase 3:** Backtest simulation & notebook hardening (Nov 24–28)
- **Phase 4:** Kaggle submission + Telegram linking (Nov 29–30)

## Phase 1 — Setup & Baseline
- [ ] Join competition on Kaggle, accept rules
- [ ] Create Telegram account, message `@pumpfun_competition_bot`, run `/link`
- [ ] Create Colab notebook `baseline.ipynb` (CPU runtime)
- [ ] Download training data from Kaggle data page to Colab
- [ ] Implement dummy strategy: buy all tokens, sell at fixed +10% tp
- [ ] Verify notebook runs CPU-only, no internet, outputs `submission.csv`

## Phase 2 — Feature Engineering & Model
- [ ] Explore data: token launch time, initial liquidity, social signals, price trajectory
- [ ] Build features: volume spikes, holder concentration, early buyer behavior, time-of-day
- [ ] Train simple model (XGBoost/LightGBM/linear) to predict pump vs dump
- [ ] Output sell target `tp` per token (or 0 to skip)
- [ ] Save best model weights/artifacts inside notebook for reproducibility

## Phase 3 — Backtest Simulation & Notebook Hardening
- [ ] Simulate daily retrain loop: train on trailing 30 days, score on holdout day
- [ ] Compute daily PnL metric locally to match competition scoring
- [ ] Remove all internet calls (no requests, no external APIs) from notebook
- [ ] Ensure runtime < Kaggle limits (CPU, memory, time)
- [ ] Test notebook end-to-end: fresh runtime → outputs valid `submission.csv`

## Phase 4 — Kaggle Submission & Telegram Linking
- [ ] Upload notebook to Kaggle competition before Nov 30, 23:59 UTC
- [ ] Verify Kaggle runs notebook successfully (no errors, valid CSV)
- [ ] Confirm Telegram bot link active before Dec 1, 00:00 UTC
- [ ] Save submission confirmation link in `notes/submission.txt`

## Colab Notes
- Use `runtime_type = CPU` (free tier is sufficient)
- Do not mount Drive inside the final Kaggle-bound notebook (Kaggle sandbox has no Drive)
- Keep all data loading self-contained (download from Kaggle API or bundle small CSVs)
- Document random seeds for reproducibility

## Success Criteria
- Notebook runs cleanly on Kaggle CPU without internet
- `submission.csv` format matches spec (one `tp` value per token, 0 = skip)
- Telegram account linked before freeze
