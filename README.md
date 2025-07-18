# cp423-a3

## Question 1 

## Question 2
d)
The single-feature ranker based on feature 75 demonstrates strong early precision (P@10 = 0.6000). Indicating 
it effectivley places relevant documents near the top of the ranking. However, it suffers from poor recall (R@10 = 0.704),
showing that it fails to retrieve most relevant documents overall. This suggests that while feature 75 may be a good local signal, it lacks
the broader coverage needed for comprehensive relevance ranking.
## Question 3
c)
BM25 outperforms the Feature-75 ranker across most evaluation metrics, highlighting its effectiveness as a general-purpose retrieval model. It achieves a higher MAP (0.5222 vs. 0.4579) and a significantly better MRR (0.6875 vs. N/A), indicating stronger performance at ranking the most relevant documents early. While Feature-75 performs better in nDCG@20 (0.5960 vs. 0.3241), this may be due to its ability to rank a subset of relevant documents highly, despite poorer overall coverage. BM25’s lower nDCG@20 may reflect its broader but less sharply focused ranking. This comparison suggests that while a single feature may exploit certain patterns well, traditional models like BM25 offer more balanced performance.
## Question 4
c)
iii)
The high Spearman correlation (ρ = 0.7892) between in-degree and PageRank reflects the strong overlap in how both measures identify important nodes. In-degree simply counts how many links point to a node, while PageRank recursively weights incoming links by the quality (i.e., rank) of the source nodes. In the web graph, pages with high in-degree often attract links from authoritative sources, which boosts their PageRank. While PageRank also accounts for the link structure beyond immediate neighbors—like damping factors and random jumps—the overall popularity of a node still plays a central role. This structural similarity explains the strong monotonic relationship captured by Spearman's rank correlation. However, the correlation is not perfect due to PageRank's additional normalization and global propagation mechanisms, which can cause some nodes with modest in-degree to rank higher if they receive links from highly ranked pages.
## Question 5
c)
BM25 outperforms the Query-Likelihood Model with Dirichlet smoothing across all metrics: MAP (0.5222 vs. 0.4804), MRR (0.6875 vs. 0.6255), and nDCG@20 (0.3241 vs. 0.2759). This difference stems from both theoretical and practical distinctions between the models.

First, length normalization is handled more effectively in BM25. While Dirichlet smoothing adjusts term probabilities based on document length via the µ parameter, BM25 explicitly penalizes overly long documents using its b parameter in a more interpretable and tunable way. This helps BM25 balance verbosity and relevance more robustly.

Second, both models assume term independence, but BM25 assigns diminishing returns to term frequency via its saturation function, while Dirichlet smoothing increases probability linearly with term frequency. BM25’s saturation curve prevents any single term from dominating the score, resulting in more stable and effective rankings when terms are repeated excessively.

Overall, BM25’s empirical success and theoretical refinements make it more suited to ranking tasks in heterogeneous document collections compared to the stricter probabilistic assumptions used in the Dirichlet model.
