# Contrastive Learning 


> The goal is to learn an embedding space where similar samples stay close to each other and dissimilar samples are far apart. It can be applied in both supervised and unsupervised settings.


- [Contrastive Learning](#contrastive-learning)
  - [Losses](#losses)
    - [Contrastive Loss](#contrastive-loss)
    - [infoNCE](#infonce)
- [Useful links](#useful-links)


## Losses

### Contrastive Loss

Given a list of input samples ${x_i}$, each has a corresponding label $y_i \in \{1, ..., L\}$ among $L$ classes. We would like to learn a function $f_\theta(.) : X \to \mathbb{R}^d$ that encodes into an embedding vector such that examples from the same class have similar embeddings and samples from different classes have very different ones. Thus, contrastive loss takes a pair of inputs $(x_i, x_j)$ and minimizes the embedding distance when they are from the same class but maximizes the distance otherwise.

$\mathcal{L}_{\text{contrastive}}(x_i, x_j, \theta) = \mathbb{1}[y_i = y_j] ||f_\theta(x_i) - f_\theta(x_j)||^2 + \mathbb{1}[y_i \neq y_j] \text{max}(0, m - ||f_\theta(x_i) - f_\theta(x_j)||^2)$

where $m$ is a margin hyperparameter that controls the distance between embeddings of different classes.    

[Chopra et al, 2005](http://yann.lecun.com/exdb/publis/pdf/chopra-05.pdf)

### infoNCE

\begin{equation}
\mathcal{L}_{\text{contrastive}} = -  \,\log\frac{\exp(\text{S_c}(ts_i, v_i)/\tau)}{\sum_{k=1}^{N}\exp(\text{S_c}(ts_i, v_k)/\tau)} \ \text{if} \  \exists(ts_i,v_i)\ 
\end{equation}


# Useful links
- [Contrastive Representation Learning by Lilian Weng](https://lilianweng.github.io/posts/2021-05-31-contrastive/)