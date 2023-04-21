# Metric scores 
This repository contains metric scores for "[Beyond neural scaling laws: beating power law scaling via data pruning](openreview.net/forum?id=UmvSlP-PyV)" (NeurIPS 2022 Outstanding Paper Award) by Sorscher*, Geirhos*, Shekhar, Ganguli, & Morcos.

Here is a list of metrics and corresponding papers:
* self-supervised prototypes, supervised prototypes: based on [Sorscher, Geirhos et al. 2022](openreview.net/forum?id=UmvSlP-PyV)
* DDD: based on [Meding, Buschoff et al. 2022](https://arxiv.org/pdf/2110.05922.pdf)
* EL2N (1 model), EL2N (20 models): based on [Paul et al. 2021](https://arxiv.org/pdf/2107.07075.pdf)
* forgetting, influence-max, influence-sum-abs: based on [Feldman & Zhang 2020](https://arxiv.org/pdf/2008.03703.pdf), released [here](https://pluskid.github.io/influence-memorization/) and [here](https://github.com/google-research/heldout-influence-estimation) under the [Apache License 2.0](https://github.com/google-research/heldout-influence-estimation/blob/master/LICENSE).
* active-learning: based on [Chitta et al. 2020](https://arxiv.org/pdf/1905.12737.pdf)

Thanks to the respective authors for their contributions, please make sure to cite them if you use the scores!

A few notes regarding the scores:
* While different scores have different ranges, they are all structured in a way such that high scores indicate keeping an example is beneficial (according to a certain metric). This is the natural structure for some metrics, and perhaps counter-intuitively for some scores which had to be reversed for consistency reasons. For instance, the prototype scores are based on Cosine similarity which is, in its raw form, high for high similarity (= high redundancy); but we then reversed the scores for consistency with the other scores such that now high scores mean low Cosine similarity, i.e. keeping the example is good because there is reduced redundancy.
* active-learning is essentially a binary score - the method selects examples such that 80% of ImageNet is used. To adapt it for our purposes, we assigned a value of either 1 or 0 depending on whether the images were included in this subset. This means that the active learning scores here aren't calibrated for pruning more / less than 20% of ImageNet.
