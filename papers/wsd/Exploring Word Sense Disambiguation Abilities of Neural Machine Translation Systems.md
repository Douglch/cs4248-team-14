## Implicit WSD in NMT models with OpenNMT [link](https://aclanthology.org/W18-1812.pdf)

![Pasted image 20250324140751.png](./assets/Pasted%20image%2020250324140751.png)

- PCA conducted on hidden states in RNN for plotting (first 2 components)?
- "each encoder hidden state ${h_i}$ can be thought of as containing the entire context for the input word $i$"
- "if the hidden states represent the context for a particular word, then these hidden states would be able to separate words with different senses **based on the contexts** in which they appear."
- Data: 3000 sentences each for validation and test
- Parameters: Default, except number of layers (1-4)
- Evaluation criteria: Dunn and DB index
- Caveat:
  - Manual annotation: "Test sentences containing any of these words were manually annotated with their associated sense, and labeled as “unclear” if the sense could not be easily determined from the sentential context"
  - Small test size
- **Experiment 1**: Cluster analysis was performed on sentence embeddings extracted from translations of 410 manually annotated sentences containing ambiguous words (_right, like, last, case_), using principal component analysis (PCA) to evaluate clustering quality.
- Result: No general trend from layer plots
- **Experiment 2**: The analysis focused only on cases where _like_ or _right_ were correctly translated, testing _whether clustering improved when the model correctly interpreted word sense._
- Result: "lack of a general trend" -> "NMT systems still struggle with the issue of word sense disambiguation"
- **Experiment 3**: A linear SVM was trained on hidden state embeddings to predict word sense, assessing whether sense information was _effectively encoded_ in the model’s internal representations.

Conclusion:

- "It could be that the NMT system learns how to disambiguate word senses at a different point in the architecture than the encoder. For example, perhaps the NMT system performs the disambiguation step during decoding, thus removing some of the burden of capturing sense information from the encoder."
- "standard NMT encoder layers are not encoding enough sentential context to do well at word sense disambiguation"
