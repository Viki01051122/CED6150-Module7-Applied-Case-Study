# CED6150 — Module 7 Applied Case Study

**Predicting Market Volatility Risk Using Liquidity Indicators and Machine Learning**  
**Contributor:** Vic Yang  
**Course:** CED6150  

## Project overview

This individual applied case study examines whether market liquidity proxies and volatility indicators help identify next-trading-day high-volatility events. The analysis uses SPY and QQQ daily OHLCV data and the VIX index for 2018–2025. The target is whether SPY's next-day absolute daily return exceeds 1.5%. It compares a regularized logistic GLM with a random forest, uses time-aware validation, explores market regimes with K-means, and checks sensitivity to liquidity features.

## Files

- `notebook/` — Google Colab analysis notebook with supplemental chronological parameter tuning
- `data/` — ETF-date panel, model dataset, and variable codebook
- `outputs/` — validation windows, comparison/sensitivity results, figures and model configuration
- `report/` — written analysis in PDF and editable Word formats
- `presentation/` — eight-slide PDF and editable PowerPoint
- `CONTRIBUTIONS.md` — individual contribution record and AI assistance statement

## Reproduce in Google Colab

1. Open `notebook/CED6150_Module7_Analysis_TUNED.ipynb` in Google Colab.
2. Use **Runtime → Run all** (internet is needed to download financial market data via `yfinance`).
3. Find generated analysis files in the notebook's `module7_outputs` directory.
4. Compare the generated results against `outputs/`. Source data can be revised by its provider; reproduced values may change if historical data is amended.
5. The supplemental tuning section is separately labeled; **baseline cost threshold and held-out metrics refer to the original model**, not the tuned model.

The notebook uses `yfinance`, `pandas`, `numpy`, `matplotlib` and `scikit-learn`. The training / validation periods precede the held-out 2025 test. Review all implementation details before treating the analysis as leakage-free.

## Main findings

- Baseline time-aware mean ROC-AUC: GLM ≈ 0.772, random forest ≈ 0.758.
- Baseline held-out 2025 ROC-AUC ≈ 0.804; recall for high-risk days at the selected decision threshold is low (9 of 33).
- Feature removal showed no improvement from liquidity measures under the chosen specification.
- Supplementary chronological tuning selected GLM `C=0.03`; its 2025 test ROC-AUC was approximately 0.800.

## Data and limitations

Historical SPY, QQQ and VIX data were obtained using Yahoo Finance via `yfinance`. Corwin–Schultz is a high-low **estimated** spread, not an observed quoted/effective bid–ask spread; Amihud is a daily proxy. VIX is a market-risk data stream, not a liquidity metric. Cost-matrix figures are illustrative, not investment advice.

## Submission note

The coursework requests a repository link and a contribution matrix. This project has been prepared as an individual contribution because no team was assigned. Confirm with the instructor if a team-only submission mechanism applies.
