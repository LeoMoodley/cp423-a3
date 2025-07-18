## cp423-a3
Due Date: July 20th 11:59 PM

## Creator
Leonardo Moodley
Student ID: 210337850

## Summary
This program is meant to calculate the specific concepts Ranked Retrieval, Feature-75 Ranker, BM25 Baseline, Link Analyisis & Fusion,
and Probabilisiic Models. In order to complete this, I would run everything on the a3_solution.py file, but in order to 
organize the tasks more efficently, I would store helper functions as Q1, Q2, Q3, Q4, and Q5 in seperate files to make the calulculations easier to perform.

## Summarization of each helper function of a3_solutions.py
# Question 1 
The Q1.py file can be ran through a function called Q1_main and this function can be found in a3_solutions.py. It's called first, before the other helper functions,
and performs calculations and other commands asked from the Question requirements.
# Question 2
The Q2.py file can be ran through a function called Q2_main and this function can be found in a3_solutions.py. It's called second, after Q1_main, before the other helper functions,
and performs calculations and other commands asked from the Question requirements such as Average Precision or nDCG@20.

d) The single-feature ranker based on feature 75 demonstrates strong early precision (P@10 = 0.6000). Indicating 
it effectivley places relevant documents near the top of the ranking. However, it suffers from poor recall (R@10 = 0.704),
showing that it fails to retrieve most relevant documents overall. This suggests that while feature 75 may be a good local signal, it lacks
the broader coverage needed for comprehensive relevance ranking.
# Question 3
The Q3.py file can be ran through a function called Q3_main and this function can be found in a3_solutions.py. It's called third, after Q1_main and Q2_main, before the Q4_main helper function,
and performs calculations and other commands asked from the Question requirements such as MAP, MRR and nDCG over 2656 queries.
c)
BM25 outperforms the Feature-75 ranker across most evaluation metrics, highlighting its effectiveness as a general-purpose retrieval model. It achieves a higher MAP (0.5222 vs. 0.4579) and a significantly better MRR (0.6875 vs. N/A), indicating stronger performance at ranking the most relevant documents early. While Feature-75 performs better in nDCG@20 (0.5960 vs. 0.3241), this may be due to its ability to rank a subset of relevant documents highly, despite poorer overall coverage. BM25’s lower nDCG@20 may reflect its broader but less sharply focused ranking. This comparison suggests that while a single feature may exploit certain patterns well, traditional models like BM25 offer more balanced performance.
# Question 4
The Q4.py file can be ran through a function called Q3_main and this function can be found in a3_solutions.py. It's called third, after Q1_main, Q2_main, and Q3_main but before the Q5_main helper function, and performs calculations and other commands such as Spearman correlation and in-degree distribution from the Question requirements.
c)
iii)
The high Spearman correlation (ρ = 0.7892) between in-degree and PageRank reflects the strong overlap in how both measures identify important nodes. In-degree simply counts how many links point to a node, while PageRank recursively weights incoming links by the quality (i.e., rank) of the source nodes. In the web graph, pages with high in-degree often attract links from authoritative sources, which boosts their PageRank. While PageRank also accounts for the link structure beyond immediate neighbors—like damping factors and random jumps—the overall popularity of a node still plays a central role. This structural similarity explains the strong monotonic relationship captured by Spearman's rank correlation. However, the correlation is not perfect due to PageRank's additional normalization and global propagation mechanisms, which can cause some nodes with modest in-degree to rank higher if they receive links from highly ranked pages.
# Question 5
The Q5.py file can be ran through a function called Q5_main and this function can be found in a3_solutions.py. It's called third, after Q1_main, Q2_main, Q3_main and Q4_main, and performs calculations and other commands duch as the MAP, nDCG@20, and MRR for the probablistic model from the Question requirements.
c)
BM25 outperforms the Query-Likelihood Model with Dirichlet smoothing across all metrics: MAP (0.5222 vs. 0.4804), MRR (0.6875 vs. 0.6255), and nDCG@20 (0.3241 vs. 0.2759). This difference stems from both theoretical and practical distinctions between the models.

First, length normalization is handled more effectively in BM25. While Dirichlet smoothing adjusts term probabilities based on document length via the µ parameter, BM25 explicitly penalizes overly long documents using its b parameter in a more interpretable and tunable way. This helps BM25 balance verbosity and relevance more robustly.

Second, both models assume term independence, but BM25 assigns diminishing returns to term frequency via its saturation function, while Dirichlet smoothing increases probability linearly with term frequency. BM25’s saturation curve prevents any single term from dominating the score, resulting in more stable and effective rankings when terms are repeated excessively.

Overall, BM25’s empirical success and theoretical refinements make it more suited to ranking tasks in heterogeneous document collections compared to the stricter probabilistic assumptions used in the Dirichlet model.

# Question 6 Reflection
For a search engine that presents 10 organic results per page, Mean Reciprocal Rank (MRR) best captures user satisfaction. MRR focuses on the rank position of the first relevant result, which directly reflects a common user behavior: clicking the first satisfactory link and stopping their search. Most users rarely scroll past the top few results, especially if the first answer meets their intent. Thus, MRR aligns closely with the real-world impact of search ranking on user experience.

Although Precision@10 (P@10) seems appropriate due to the 10-result layout, it treats all positions equally and doesn’t reward highly ranked relevant documents over lower-ranked ones. Similarly, nDCG@10 captures graded relevance and position, but it assumes users examine multiple results and benefit from multiple relevant documents—an assumption that doesn’t always hold for navigational or specific informational queries.

MRR's strength is in reflecting how quickly a user finds a useful result, which is often the primary driver of satisfaction. If a relevant link appears first, the user experiences minimal effort and high satisfaction. This makes MRR particularly valuable for search engines aimed at quick answer delivery.

Therefore, while all metrics offer insight, MRR is the most intuitive and user-aligned for single-page, top-10 ranked search interfaces.

