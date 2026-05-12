---
layout: page
permalink: /research/
title: Research
description: 
nav: true
nav_order: 2
---

{% include scripts/mathjax.html %}

You can find my Google Scholar page [here](https://scholar.google.com/citations?user=EH_qcqkAAAAJ&hl=en).

#### Research in Distribution Estimation

*Distribution estimation* concerns the problem of estimating an unknown *probability distribution* from a finite set of samples. The *empirical estimator*—equivalently, the *maximum likelihood estimator (MLE)*—is known to be *asymptotically optimal*. However, alternative procedures such as *add-constant estimators*, the *modified Good–Turing estimator*, and the *profile maximum likelihood (PML) estimator* can demonstrate improved performance under various choices of *loss functions*. These estimators are *natural*, in the sense that they assign equal probability to symbols that appear the same number of times in the observed sample.

In our first work, we characterize the *unavoidable estimation error* incurred by the class of natural estimators. This is the price any estimator has to pay for being natural. Further, we also provide an estimator for this unavoidable estimation error.

1\. **Estimating Error in Natural Distribution Estimation**  
   **H. Balasundaram**, A. Thangaraj.  
   *Annual Allerton Conference on Communication, Control, and Computing*, 2025. [Conference Paper](https://hdl.handle.net/2142/130303). [Slides](https://easychair.org/smart-slide/slide/CwFS#{sn:1}).

Now that there is an unavoidable lower bound on the estimator error, we develop strategies that leverage some *side information* to beat the performance of natural estimators. The side information could be as follows: suppose we know a *synonymous* distribution that is some distance from the distribution we are trying to estimate. Such side information improves our estimation error and we analyze minimax bounds in this scenario.

2\. **Distribution Estimation with Side Information**  
   **H. Balasundaram**, A. Thangaraj.  
   *Accepted to International Symposium on Information Theory*, 2026. [arXiv](https://arxiv.org/abs/2601.08535). [EE Research Symposium Slides]({{ '/assets/pdf/ee_symposium_slides.pdf' | relative_url }})   

How will one get such a synonymous distribution practically? We analyze this in the context of language models, and show that two words with similar *embeddings* also have similar distributions of words occurring after that word. For instance, the probability distibution of words occurring after the word 'big' and after the word 'enormous' would be similar and thus it is possible to mutually improve their estimates. We use this idea to construct better language models and improve the *perplexity*, the metric used to evaluate language models.

3\. **Semantic Smoothing for Language Models via Distribution Estimation and Embeddings**  
   **H. Balasundaram**, S. S. Narashiman, P. Mathur, A. Thangaraj.  
   [arXiv](https://arxiv.org/abs/2605.07994).

---

#### Research in Online Convex Optimization

The problem of *Online Convex Optimization (OCO)*, where a policy selects an action before observing a convex cost function, is well understood, with a regret bound of $$O(\sqrt{T})$$ for $$T$$ timesteps. Another related problem is *Nested Convex Body Chasing (NCBC)*, where a policy has to play actions inside nested convex bodies which are displayed online and attempt to minimize the distance between consecutive actions. We study two problems- *COCO* and *CONES*, which are both interesting and practical intersections of OCO and NCBC.

*Constrained Online Convex Optimization (COCO)* is a natural extension of OCO in which, after each action, the policy observes not only a cost function but also a constraint function. Since it may be impossible to satisfy the constraint at every step online, the goal is to simultaneously minimize regret while controlling the cumulative constraint violation. Prior work by *Vaze and Sinha* established that both regret and total constraint violation can both be bounded by $$O(\sqrt{T})$$, a result that was widely believed to be optimal. In this work, we refute that belief and show that, in two dimensions, it is possible to achieve:

- Regret: $$O(\sqrt{T})$$  
- Constraint violation: $$O(T^{1/3})$$

We show that incurring a constraint violation reduces either the *area* or the *perimeter* of the constraint sets shown, and this process cannot continue indefinitely. This yields a simultaneous upper bound on both the regret and the constraint violation.

1\. **Breaking the $$O(\sqrt{T})$$ Cumulative Constraint Violation Barrier while Achieving $$O(\sqrt{T})$$ Static Regret in Constrained Online Convex Optimization**  
   **H. Balasundaram**, Karthick Krishna Mahendran, Rahul Vaze.  
   [arXiv](https://arxiv.org/abs/2603.20671)

Next, we consider a case where a single function $$f$$ is known and constraint sets are shown online, and an algorithm has to simultaneously control both the regret and the movement cost. This is the problem of *Convex Optimization with Nested Evolving feasible Sets (CONES)*. We prove that it is, in general, possible to get non-positive regret and $$\log(T)$$ movement cost for a wide class of functions $$f$$.

2\. **Convex Optimization with Nested Evolving Feasible Sets**  
   Karthick Krishna M., **H. Balasundaram**, R. Vaze.  
   *arXiv preprint arXiv:2605.07386*, 2026. [arXiv](https://arxiv.org/abs/2605.07386).

---

#### Research in Information Theory

1\. **Learning to Transmit Over Unknown Erasure Channels with Empirical Erasure Rate Feedback**     
   **H. Balasundaram**, K. Jagannathan.  
   [arXiv](https://arxiv.org/abs/2507.08599).

---

#### Research on Stable Matchings

1\. **Generalized Capacity Planning for the Hospital-Residents Problem**  
   **H. Balasundaram**, G. Limaye, M. Nasre, and A. Raja.  
   *Theoretical Computer Science*, 2026. [Journal Paper](https://www.sciencedirect.com/science/article/pii/S0304397526000198).

2\. **Stability Notions for Hospital Residents with Sizes**     
   **H. Balasundaram**, Krishnashree J. B., G. Limaye, M. Nasre.  
   *Foundations of Software Technology and Theoretical Computer Science 2025*. [Conference Paper](https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.FSTTCS.2025.11).

