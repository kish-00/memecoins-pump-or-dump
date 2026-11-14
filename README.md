# Memecoins: Pump or Dump — Project Description

## Competition Overview
- **Platform:** Kaggle
- **URL:** https://kaggle.com/competitions/memecoins-pump-or-dump
- **Type:** Code competition / notebook submission
- **Entry deadline:** None stated (register anytime before freeze)
- **Submission freeze:** November 30, 2026, 23:59 UTC
- **Scoring period:** December 1–14, 2026 (14 days of real PnL)
- **Final score:** Sum of 14 daily PnLs on days that did not exist at freeze
- **Prizes:** 10 places + community awards
- **Solo/team:** Solo OK

## What to Build
You submit a **Jupyter notebook**, not a prediction CSV. The notebook:
1. Trains a model inside the Kaggle run on CPU, without internet access.
2. Is retrained daily by the competition bot on the last 30 days of data.
3. Outputs `submission.csv` — one number per token: the sell target (`tp`), or `0` for "do not buy."
4. Is scored on real on-chain PnL for Pump.fun launches on Solana.

## Eligibility Requirements
- Link your Kaggle account to the Telegram bot `@pumpfun_competition_bot` (`/link` command) **before** the freeze.
- Send at least one notebook to the bot before December 1, 00:00 UTC.
- Unlinked entries are scored anonymously but may not be prize-eligible.

## Constraints
- **No internet** during notebook execution on Kaggle.
- **CPU-only** runtime — perfect for Google Colab free tier development.
- No pre-existing leaderboard tuning helps; test tokens did not exist at freeze.

## Deliverables
1. Trained notebook (`.ipynb`) that outputs `submission.csv`.
2. Kaggle submission uploaded before Nov 30, 2026 23:59 UTC.
3. Telegram bot account linked before freeze.

## Colab Strategy
- Develop and prototype entirely in Google Colab (CPU runtime).
- Simulate the daily retrain loop locally: train on days N-30 to N, predict day N+1.
- Export notebook to Kaggle for final submission.
