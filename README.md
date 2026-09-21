
# Deep Temporal Models with Attention and Skip Connections

> **Solo research conducted through NYU Tandon's [Vertically Integrated Projects](https://engineering.nyu.edu/research/student-research/vertically-integrated-projects) program.**

This repository documents a research progression in commodity-futures direction prediction: starting with macroeconomic baselines, then testing whether alternative news data and graph-aware attention offer a more useful signal.

## Research trajectory

### 1. Macro-only baseline

The first study, [DeepTemporalModelsWithAttentionAndSkipConnection.ipynb](DeepTemporalModelsWithAttentionAndSkipConnection.ipynb), combines FRED-MD macroeconomic features with wheat-price data to predict next-day direction. It evaluates **RNN, BiRNN, LSTM, and BiLSTM** architectures, each enhanced with attention and residual skip connections.

The best accuracy was roughly **52%**—essentially a coin flip for a balanced directional task. That result was the point: broad macro data alone was not a reliable or tradable directional signal for commodity futures in this setup. Commodity moves are often driven by shocks, supply conditions, policy, weather, and market-specific information that macro releases do not capture at the required horizon.

### 2. Alternative data: news

To test a more timely source of information, I collected commodity-related news from **Investing.com, Reuters, Bloomberg, and CNBC** spanning **2010–2026**. The pipeline cleans articles, extracts FinBERT embeddings and sentiment, and aggregates them into daily news features.

### 3. GSHA: graph-augmented news modeling

[GSHA_Research.ipynb](GSHA_Research.ipynb) asks the next question: **does news contain a tradable directional signal, and does graph-aware attention improve its use?**

The Graph-Augmented Hybrid Hyperbolic Attention (GSHA) study represents news days as a dynamic graph, propagates information across semantically and temporally related stories, and uses hybrid hyperbolic-Euclidean cross-attention to connect graph-propagated news with the price sequence. The complete implementation and visual design are available here:

- [GSHA research notebook](GSHA_Research.ipynb)
- [GSHA architecture](<GSHA Architecture.pdf>)
- [News embedding and sentiment pipeline](news_embedding_pipeline.ipynb)

## Research outcome

The wheat-focused GSHA experiment produced an interesting initial result, but it did **not** hold up when extended to additional commodities. This repository therefore presents the work as research—not as a production trading strategy or evidence of a robust, generalizable signal.

That limitation is an important result in itself: a model that appears promising on one commodity must survive cross-commodity replication before it can be treated as meaningful.

## Repository map

| File | Purpose |
|---|---|
| [DeepTemporalModelsWithAttentionAndSkipConnection.ipynb](DeepTemporalModelsWithAttentionAndSkipConnection.ipynb) | Macro-only recurrent-model baseline |
| [news_embedding_pipeline.ipynb](news_embedding_pipeline.ipynb) | CSV-to-embedding and sentiment pipeline without scraping |
| [GSHA_Research.ipynb](GSHA_Research.ipynb) | Graph-augmented wheat-news research notebook |
| [GSHA Architecture.pdf](<GSHA Architecture.pdf>) | GSHA architecture walkthrough |

## Run

```bash
pip install torch transformers scikit-learn pandas matplotlib seaborn jupyter
jupyter notebook GSHA_Research.ipynb
```

The data and notebook outputs are included for research reproducibility. Results should be independently re-run and stress-tested before any financial use.
