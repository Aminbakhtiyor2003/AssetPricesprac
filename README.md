# AssetPricesprac

Asset Factor Similarity Model
A Research Framework for Regime Intuition and Cross-Asset Pattern Recognition

Project Summary
This project explores a disciplined framework for identifying historical analogs in cross-asset factor returns. The motivation was not to build a trading signal, but to develop structured intuition around how factor and style returns evolve through regimes—especially as they relate to directional consensus, relative rotation, and sequential dependencies.

The dataset comes from AQR, a leading quantitative investment firm with a well-established research pedigree. Their long history of factor-level data offers a rare opportunity to work with high-integrity time series extending nearly a century. I selected this dataset not only for its credibility, but because AQR uses it in their own published research—a strong signal of its practical relevance.

Although I do not claim to fully understand every methodological nuance behind each factor’s construction, the purpose here is exploratory. Understanding relationships between factors—rather than the mechanics of their internal definitions—was the primary goal. In short, this is not a deep dive into what factors are, but an exercise in understanding how they behave relative to each other through time.

The inspiration came partly from AQR’s own work on regime modeling, as well as broader literature around asset rotation and tactical allocation. I’ve experimented previously with macroeconomic-based forecasting models, but found that predicting economic variables to predict other variables to then infer asset prices created unnecessary abstraction. In contrast, this project uses asset return behavior directly—simplifying the path from data to insight.

Model Construction
Data Scope
The model begins in the early 1980s. Although data extends further back, I deliberately excluded the 1970s—particularly fixed income—due to the structural distortions introduced by the Volcker tightening cycle. That period represented a discontinuity in bond pricing behavior that meaningfully skewed similarity metrics. Post-1980 data offers a more stable and interpretable foundation.

Similarity Matching
For a selected target month, the model identifies the five most similar months in history based on either:

Euclidean distance – which captures absolute return magnitude differences, and is sensitive to volatility; or

Cosine similarity – which focuses on return directionality and is scale-invariant.

Both approaches generally produced overlapping analogs, suggesting some robustness in pattern matching. Cosine similarity was especially useful when directional behavior was more important than amplitude, which aligns with the project's goal of understanding return structures rather than absolute dispersion.

Categorical Labeling
Returns were bucketed into three categories—positive, flat, and negative—based on a ±0.2% threshold. This discretization removes micro-noise while preserving meaningful directional signals. While simplistic, it allows for clear base-rate calculations and facilitates downstream analysis of conditional outcomes.

T+1 Forward Mapping
After identifying the analogs, I evaluated the month after (T+1) each similar period to assess how each factor performed. While the framework supports longer horizons (T+2, T+3), I chose T+1 for interpretability and statistical reliability. As forecast horizons extend, the usefulness of historical similarity declines due to compounding uncertainty.

The underlying idea is straightforward: When we’ve seen this configuration before, what happened next? This is not intended as a deterministic forecast, but rather as a probabilistic anchor based on repeatable market configurations.

Base Rate Aggregation
For each factor or style, I calculated the percentage of times it moved up, down, or remained flat in the T+1 month following the selected analogs. These base rates are used not as signals, but as contextual reference points—a method of quantifying the range of plausible directional outcomes under a given starting state.

Philosophy and Purpose
This is not a model meant for real-time execution or signal generation. It is designed to facilitate intuition-building around regime behavior and inter-factor dynamics. In markets, few things are stable over time—factor payoffs, correlations, and volatilities all shift—but structure can still be inferred probabilistically if approached carefully.

The philosophical framework borrows from the probabilistic reasoning outlined in Superforecasting. Anchoring, when done blindly, can introduce bias. But when tied to rigorously selected historical precedent and validated with contextual analysis, it provides a necessary starting point for judgment under uncertainty.

To mitigate the risk of false analogs, I manually review each similarity result. Statistical match does not guarantee narrative coherence. I ask:

Were the macroeconomic conditions broadly aligned?

Was investor positioning comparable?

Did exogenous risks exist that invalidate the analogy?

Without this layer of contextual filtering, models risk being “numerically correct but contextually irrelevant.” I treat historical precedent as a hypothesis generator—not as proof.

Finally, I acknowledge the limits of this approach. Structural breaks, policy shocks, and behavioral shifts—so-called “black swans”—will always challenge models trained on precedent. Still, as Mark Twain is often quoted: “History doesn’t repeat itself, but it often rhymes.” This framework seeks to detect the rhymes—not recite the verses.

Future Directions
To improve the model’s relevance and robustness, I plan to iterate across several fronts:

Threshold Optimization
Volatility-adjusted thresholds may replace fixed ±0.2% cutoffs to account for different market environments. This could improve return labeling accuracy during high-volatility regimes.

Advanced Similarity Metrics
I will explore alternative distance measures, such as Mahalanobis distance (for correlation-aware similarity) and dynamic time warping (to allow for temporal misalignment in sequences).

Unsupervised Machine Learning
Clustering methods, K-Nearest Neighbors, and dimensionality reduction techniques (e.g., PCA, t-SNE) may improve analog selection and reduce manual bias in identifying similar periods.

Signal Layering
Incorporating macroeconomic indicators, volatility metrics, or investor sentiment could allow the model to condition similarity matching on more than price returns, improving relevance and reducing noise.

Out-of-Sample Testing
As updated factor data becomes available through 2025, I plan to test the model out-of-sample. The goal is not predictive accuracy per se, but rather evaluating whether the intuition it produces remains consistent and informative.

Final Remarks
This project represents a research process rather than a final product. Its aim is to improve my reasoning about market regimes, factor interactions, and base rate inference. While not meant to forecast with precision, the framework encourages probabilistic thinking, contextual discipline, and respect for history—not as oracle, but as reference.

In the end, my objective is not to be precisely right, but to be structurally reasonable—and to improve the quality of my judgment when facing uncertainty.
