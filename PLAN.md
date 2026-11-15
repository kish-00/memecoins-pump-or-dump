# Memecoins: Pump or Dump — Execution Plan

Public task list only. Strategy details live outside this repo.

## Timeline
- Phase 1: Setup & baseline
- Phase 2: Feature engineering & model
- Phase 3: Backtest simulation & notebook hardening
- Phase 4: Kaggle submission & operations

## Phase 1 — Setup & baseline
- [ ] Join competition on Kaggle, accept rules
- [ ] Link account to competition bot
- [ ] Create baseline notebook (CPU runtime)
- [ ] Download training data
- [ ] Implement placeholder strategy
- [ ] Verify CPU-only run, no internet, outputs submission.csv

## Phase 2 — Feature engineering & model
- [ ] Explore data
- [ ] Build features
- [ ] Train model
- [ ] Output sell target per token
- [ ] Save model artifacts inside notebook

## Phase 3 — Backtest simulation & notebook hardening
- [ ] Simulate daily retrain loop
- [ ] Compute daily metric locally
- [ ] Remove all internet calls from notebook
- [ ] Ensure runtime within limits
- [ ] Test notebook end-to-end

## Phase 4 — Kaggle submission & operations
- [ ] Upload notebook before freeze
- [ ] Verify Kaggle runs notebook successfully
- [ ] Confirm bot link active before scoring starts
- [ ] Record submission confirmation

## Success criteria
- Notebook runs cleanly on Kaggle CPU without internet
- submission.csv format matches spec
- Account linked before freeze
