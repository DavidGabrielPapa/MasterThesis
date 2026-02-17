# MasterThesis

As discussed on Wednesday, 19th November, I am outlining my proposed tasks below:
1. Study the Hollywood actor network:

    a. Extract the network, using the available data on actor collaborations in the 1990s and 2000s.
  
    b. Using the mbti_celebrities.csv file (originally extracted from https://www.personality-database.com/), assign an MBTI type to each Hollywood actor in the network in (1.a).

    c. Compute network measures for each actor. Then, examine how each personality type correlates with the corresponding network measure.

2. Repeat steps (1.a)—(1.c) for a network of musical collaborations. 
3. Repeat steps (1.a)—(1.c) for a network of political relationships.

As the first stage, we need to focus on task (1) only. Once (1.a) and (1.b) are completed, I would proceed with (1.c) as follows:

- [Pre-analysis to check if data are good and enough] I would calculate the percentage of nodes with MBTI in the entire network — Determine how many nodes have an MBTI type assigned.
- [Pre-analysis to check if data are good and enough] I would calculate the MBTI distribution in the entire network — Check if the distribution is representative or biased (e.g., overrepresentation of ENFPs).
- [(1.c) analysis] I would calculate the following network measures (most of which are already implemented in NetworkX): 
  - Degree Centrality to be linked to E/I (Extraversion/Introversion). I hypothesize that a high degree correlates with high Extraversion (E). I would use “nx.degree_centrality(G)”.
  - Participation Coefficient to be linked to N/S (Intuition/Sensing). I hypothesize that a high participation correlates with high intuition (N). I would use “nx.community.louvain_communities(G)” followed by “brainconn.centrality.participation_coef”. Please bear in mind that “brainconn” is a separate package, not part of “NetworkX”(more info here: https://github.com/fiuneuro/brainconn).
  - Betweenness Centrality to be linked to T/F (Thinking/Feeling). I hypothesize that a high betweenness correlates with high Thinking (T). I would use “nx.betweenness_centrality(G)”.
  - Node Constraint to be linked to J/P (Judging/Perceiving). I hypothesize that a high node constraint correlates with high Judging (J). I would use “nx.constraint(G)”.
- [(1.c) analysis] If not already normalised, I would normalise the node measures (possibly between “0” and “1”) and store them in a table. The normalization ensures all metrics contribute equally to the analysis, as they may have different ranges. I would probably use a “pandas.DataFrame”, where each row represents a node (person) and the columns include the node ID (1 column), the node measures (one column per measure), and the MBTI personality type (1 column).
- [(1.c) analysis] I would plot scatterplots among MBTI personality types and node measures (one scatterplot per measure).
