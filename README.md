# Quant-LLM-Training

Quant LLM Training Corpus (V1)

This repository contains the initial training corpus used to fine-tune an open-weight language model for quantitative finance research, multi-regime modeling, and crypto market microstructure.

The goal is to build a focused, high-quality, and domain-specific dataset suitable for LoRA fine-tuning.

The corpus emphasizes:

- empirical asset pricing
- statistical arbitrage
- regime-switching models
- execution microstructure
- MEV dynamics in decentralized markets
- best practices in backtesting and model evaluation

This is not a general finance dataset. It is intentionally narrow and high-signal to reduce noise and improve downstream reasoning.

## 1. Repository Structure

```
data/
  raw/                # Original PDFs and source documents
  extracted/          # Plain-text extracted from PDFs
  chunks/             # Cleaned training chunks (800–2000 tokens)
dataset_v1.jsonl      # Final combined dataset for fine-tuning
scripts/              # Utilities for extraction and chunking
README.md
```

## 2. Contents of Dataset V1

V1 includes five core pillars that provide the model with a foundational understanding of quantitative finance and crypto microstructure. These were selected for conceptual clarity, methodological depth, and relevance to systematic research.

### 2.1 Statistical Arbitrage & Return Predictability

- Avellaneda & Lee (2010) – Statistical Arbitrage in the U.S. Equities Market
- Jegadeesh & Titman (1993, 2001) – Momentum strategies
- Harvey, Liu & Zhu – Backtesting, p-hacking, and factor validation
- Selected material from Fama & French (factor structure and cross-sectional returns)

Purpose: Provide a rigorous basis for short-horizon predictability, factor modeling, and classical stat-arb formulations.

### 2.2 Time-Series Modeling & Regime-Switching

- Hamilton (1989) – Markov switching framework
- Kim & Nelson – Bayesian estimation of regime-switching processes
- Rabiner – Hidden Markov Models (tutorial)
- Selected literature on HMM+RNN / HMM+LSTM hybrid systems

Purpose: Establish a mathematical foundation for multi-regime dynamics, latent state inference, and probabilistic transitions.

### 2.3 Execution, Market Microstructure & MEV

Traditional microstructure:

- Kyle (1985) – Information and market impact
- Bouchaud, Farmer, Lillo – Order flow, impact, microstructure invariants
- Almgren & Chriss – Optimal execution and slippage modeling

Crypto & DeFi:

- Daian et al. (2020) – Flash Boys 2.0 (MEV taxonomy)
- Recent MEV survey papers (sandwiching, backrunning, on-chain latency)
- AMM and DEX microstructure references (Uniswap v2/v3, CFMM theory)

Purpose: Expose the model to adversarial execution environments, liquidity fragmentation, and on-chain market structure.

### 2.4 ML & Deep Learning for Finance

- López de Prado – Advances in Financial Machine Learning (algorithmic sections only)
- Tsay – Volatility, GARCH, and multivariate time-series excerpts
- LSTM/GRU/Transformer-based financial forecasting literature
- Time-series attention, temporal convolution, and hybrid latent state models

Purpose: Map the link between statistical models and modern ML architectures in financial contexts.

### 2.5 Research Notes (Author-Provided)

Includes authored material relevant to:

- hybrid HMM-LSTM regime detection
- regime-aware risk overlays
- MEV-aware execution modeling
- design rationale for simulation pipelines
- notes on factor construction and diagnostics

Purpose: Embed domain-specific reasoning and methodology that does not appear in public literature.

## 3. Chunking Protocol

All documents are:

- converted to plain text,
- normalized (whitespace, UTF-8, equations preserved where possible), and
- segmented into 800–2000 token chunks with minimal overlap.

Chunks follow a simple JSONL schema:

```
{"text": "<chunk content>"}
```

This format is compatible with:

- HuggingFace LoRA training scripts
- Axolotl
- Open-source fine-tuning frameworks

## 4. Training Objective

The dataset is intended for:

- LoRA/QLoRA fine-tuning
- on a 30–34B active MoE model (e.g., Kimi K2 Small)
- for quantitative reasoning, multi-regime inference, execution modeling, and crypto microstructure

The focus is correctness, mathematical grounding, and methodological consistency. No synthetic conversational data is included in V1.

## 5. Future Extensions

Planned additions for V2/V3:

- volatility clustering literature (GARCH, EGARCH, FIGARCH)
- execution cost estimation papers in crypto
- reinforcement learning for execution and portfolio policies
- agent-based market microstructure simulations
- additional authored technical notes
- curated Jupyter notebooks demonstrating empirical workflows