---
dg-publish: true
---
>[!danger]+
>Shamelessly ăn cắp từ thread [[D] Resources for Understanding The Original Transformer Paper : r/MachineLearning (reddit.com)](https://www.reddit.com/r/MachineLearning/comments/pkedi4/d_resources_for_understanding_the_original/).

The [Attention Is All You Need paper](https://arxiv.org/abs/1706.03762), aka. The Original Transformer paper, is one of the most important papers in deep learning. I found this paper to be quite difficult to understand having only read a dozen papers before. This is a list of resources that I used to understand this paper:
# 0. Prerequisites
(Assuming you already know about LSTMs, Seq-to-Seq, etc.)
1. [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/abs/1409.0473) - This is the first paper to use the attention mechanism for machine translation.
2. [Effective Approaches to Attention-based Neural Machine Translation](https://arxiv.org/abs/1508.04025) - An improvement of the above paper. Introduces some important concepts like Dot-Product Attention.
3. [TensorFlow Tutorial: Neural machine translation with attention](https://www.tensorflow.org/text/tutorials/nmt_with_attention) - Code example always helps
# 1. Tutorials (for beginners)
First, go ahead and read the paper; it doesn’t matter if you don’t fully understand it. Then use these resources:
1. [RASA’s video series](https://youtu.be/EXNBy8G43MM) - Perhaps the best in this list although hugely underrated. The only video I have seen that actually motivates the idea of self-attention
2. [CodeEmporium’s video](https://youtu.be/TQQlZhbC5ps) - Good high-level overview
3. [Yannic Kilcher’s video](https://youtu.be/iDulhoQ2pro) - More details
4. [Lukasz Kaiser’s lecture](https://youtu.be/rBCqOTEfxvg) - Must-watch as it is from one of the authors of the paper
5. [Video and article by Jay Alammar](https://jalammar.github.io/illustrated-transformer/) - Nice visuals. Goes in-depth into the computations. Very useful for understanding multi head attention.
Try reading the paper again now; it will, hopefully, make a lot more sense.
# 2. Code
- [Tensorflow code example](https://www.tensorflow.org/text/tutorials/transformer)
- [Pytorch code example by Aladdin Persson](https://youtu.be/U0s0f995w14)
# 3. Complement
- Read [[Transformers Reading#^b40c48\|Transformers Reading#^b40c48]] 
- Read [2207.09238 Formal Algorithms for Transformers (arxiv.org)](https://arxiv.org/abs/2207.09238)
- Read [On Layer Normalization in the Transformer Architecture (arxiv.org)](https://arxiv.org/pdf/2002.04745.pdf)
- Read [Transformers from Scratch (e2eml.school)](https://e2eml.school/transformers.html)
- Read [[2004.08249] Understanding the Difficulty of Training Transformers (arxiv.org)](https://arxiv.org/abs/2004.08249)
- Read [The Annotated Transformer (harvard.edu)](https://nlp.seas.harvard.edu/2018/04/03/attention.html)
- [[1503.08895] End-To-End Memory Networks (arxiv.org)](https://arxiv.org/abs/1503.08895)
- [[1606.03126] Key-Value Memory Networks for Directly Reading Documents (arxiv.org)](https://arxiv.org/abs/1606.03126)
- [udlbook](https://udlbook.github.io/udlbook/)


>[!note]+ Reading list to understand Transformers
>MHO the resources listed under Theory part are more like tutorials for new-comers.
>
>For the theory, here is a list of papers I recommend for people to read with a strong linear algebra/probability/functional analysis background.
>- Tsai, Y. H. H., Bai, S., Yamada, M., Morency, L. P., & Salakhutdinov, R. (2019). Transformer Dissection: A Unified Understanding of Transformer's Attention via the Lens of Kernel. [arXiv preprint arXiv:1908.11775](https://arxiv.org/abs/1908.11775): one of the first papers to draw connection between the scaled dot-product attention to the kernel methods, as the softmax of the attention matrix becomes a positive kernel to use the memorized weights to compare the embedding of two tokens, also the first paper to emphasize the importance of the positional encodings.
>- Choromanski, Krzysztof, Valerii Likhosherstov, David Dohan, Xingyou Song, Andreea Gane, Tamas Sarlos, Peter Hawkins et al. "Rethinking attention with performers." [arXiv preprint arXiv:2009.14794 (2020)](https://arxiv.org/abs/2009.14794): one of the first papers to further strengthen the (Gaussian and shifted Gaussian) kernel interpretation of the Transformers, shows a random feature map approximates the softmax kernel pretty well.
>- Wright, M. A., & Gonzalez, J. E. (2021). Transformers are Deep Infinite-Dimensional Non-Mercer Binary Kernel Machines. [arXiv preprint arXiv:2106.01506](https://arxiv.org/abs/2106.01506): this paper formally formalize the Mercer kernel interpretation in Reproducing kernel Banach spaces (RKBS), yet the main theorem's proof is a tad lacking and just a simple rephrase, and the authors have not drawn a clear link between the functions in the RKBS with the latent representation. Kinda a missing opportunity.
>- Lastly a shameless plug-in of my work: [https://arxiv.org/abs/2105.14995](https://arxiv.org/abs/2105.14995). First paper to link a linearized scaled dot-product attention to a Galerkin-type projection for discrete approximation spaces in Hilbert spaces (think a learnable Gram-Schmidt). First paper to prove rigorously the attention mechanism's approximation power (Céa's lemma) being sequence-length invariant if softmax is removed using a discretized Ladyzhenskaya–Babuška–Brezzi condition.
>
>**Comment about paper**:
>Do you mean this paper?
>- Schlag, I., Irie, K., & Schmidhuber, J. (2021, July). Linear Transformers are secretly fast weight programmers. In International Conference on Machine Learning (pp. 9355-9366). PMLR. [https://arxiv.org/abs/2102.11174](https://arxiv.org/abs/2102.11174)
>- [Neural nets learn to program neural nets with with fast weights (1991) (idsia.ch)](https://people.idsia.ch/~juergen/fast-weight-programmer-1991-transformer.html)
>
>If so, personally I feel the connection is even much much looser than that of the additive attention used in Neural Turing Machine, e.g., see
>- Bahdanau, Dzmitry, Kyunghyun Cho, and Yoshua Bengio. "Neural machine translation by jointly learning to align and translate." arXiv preprint arXiv:1409.0473 (2014).
>
>Considering how similar equation (5) in the paper above is with the scaled dot-product attention. Meanwhile, IMHO, the scaled dot-product attention is the natural (linear algebraic) generalization of the bi-directional RNN interpretation used in the NMT version of "attention". Also in this paper, the attention matrix representing the similarity between embeddings of different positions is drawn directly (but not in the J. Schmidhuber paper).
>
>I am aware that J. Schmidhuber is one of the founding father of the deep learning, and I do not mean to offend you. Again, personally I feel the 2 Transformer papers I read by J. Schmidhuber had some bold claims that "the attention mechanism is equivalent to the fast weight programmers (FWP)" which I could hardly agree upon.
>
>IMHO FWP is trying to reduce the computational cost of RNNs, and the attention is taking another direction: ramping up the computational cost vs RNNs, but the operation is easy to be parallelized. 
>
>**Another comment**:
>I'd probably also add [Hopfield Network is All You Need](https://arxiv.org/pdf/2008.02217), showing that Transformers can be interpreted as a Hopfield net, which I find a super useful way to think of them.
>
>**Another comment**:
>Knowledge about [LSTM](https://en.wikipedia.org/wiki/Long_short-term_memory) is nessesary and learn about [RNN](https://arxiv.org/abs/1308.0850).

^b40c48
