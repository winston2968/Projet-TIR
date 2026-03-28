# TIR : Notes 

## The tractability of SHAP-Score-Bases explanations over Deterministic and Decomposable Boolean Circuits. 

This article presents an efficient algorithm to compute **SHAP-scores** within specific classification models. The SHAP-score is a prominent explanation method for classifiers that assigns a numerical value to each input feature based on its contribution to the decision process. In general, computing SHAP-scores is computationally intractable due to the model's complexity, often being **#P-hard**.
However, this paper focuses on **Boolean Classifiers**, which return either 1 (accept) or 0 (reject) for a given input. These models are represented as **deterministic** and **decomposable** Boolean circuits, a class that encompasses models like Bayesian Classifiers, Random Forests, and Decision Trees.
In this framework, the authors provide a polynomial-time algorithm to compute SHAP-scores over tractable Boolean circuits, initially assuming a uniform distribution over inputs. Both the **determinism** and **decomposability** properties are strictly necessary for this tractability:
* **Determinism** ensures that for every OR gate, no two inputs can be true at the same time for any given assignment.
* **Decomposability** requires that for every AND gate, the sets of features in its sub-circuits are pairwise disjoint (they share no variables).
The core contribution of the paper is the reduction of the SHAP-score computation to a **#SAT** problem (model counting). The authors then define a polynomial-time algorithm to solve this specific \#SAT problem using a **bottom-up induction** process

## SHAP-Instance Weighted and Anchor Explainable AI: Enhancing XGBoost for Financial Fraud Detection

This paper presents a real-case application of SHAP-values and Anchors in fraud detection systems. While traditional statistical methods are common, they struggle with the complex nature of modern fraud. The authors enhance the XGBoost model by using a novel SHAP-instance weighting method to prioritize learning from the most informative samples. To solve the massive class imbalance in the Thailand Stock Exchange dataset, they combine RENN and SMOTE techniques before optimizing the model with Optuna and Hyperband.

The resulting model effectively differentiates between non-fraudulent, fraudulent, and "grey area" behaviors. By reaching a perfect recall (1.000) for fraudulent cases, this approach sets a new standard for accuracy and trust. Furthermore, Anchors are used to translate "black-box" predictions into easy-to-understand if-then rules, providing clear insights for risk management. However, integrating these SHAP and Anchor systems increases the computational load and total processing time.


## Why should I trust you ? 

This article proposes a **Local Interpretable Model Agnostic Explanations (LIME)** system for classification models. Its objective is to provide a local approximation of a black-box model behavior by an interpretable model (ex: random forest, linear model, etc...). The article also presents an amelioration of this method to provide a more global explanation of the model prediction by selecting local and non-redundant LIME explanations which faithfully represent the black-box model result called **Sub-modular picks LIME (SP-LIME)**. 
LIME can be interpreted as a perturbation model. Indeed, from an original interpretable representation $x'$, it generates a set of samples $z'$ which are drawn by selecting uniformly some $x'$ non-zero components. This sampling is weighted by $ \pi_x$ which defines a locality around $x'$ denoted $\mathcal{Z}$. Then, the problem is to learn an explanation model $g$ such that $g(z') = w_g \cdot z'$ with $w_g$ the importance of an interpretable feature of $x$. 
The paper also introduce a trade-of between the black-box model ($f : \mathbb{R}^d \longrightarrow \mathbb{R}$) interpretation given by $g$ and the complexity of this explanation denoted $\Omega(g)$. Indeed, to explain a black-box model, we can simply return the model weights, but there are incomprehensible by a human. The LIME problem is then the minimization problem of how unfaithful $g$ is in approximating $f$ in locality around $x$ and having $\Omega(g)$ low enough to be human understandable. 
In practice, this optimization problem is intractable because $\Omega(g)$ specific choice function, that's why a K-LASSO resolution is used. The idea is to select the most $K$ relevant features by LASSO algorithm and then get the final weight $w_g$ only for those features.

## Model Agnostic Explanations by Identifying Prediction Invariance  

This article presents the evolution of LIME system by adding Anchors to clearly define LIME coverage boundaries. Indeed, by construction LIME perturbs the output representation $x'$ of a black-box model $f$ by selecting random $x'$ components according to a distribution $\pi_x$. However, this $ \pi_x$ doesn't define a clear zone around $x'$ where the system select the perturbed inputs to give to the models, ones can be very close and the other very far. So that human cannot really understand which feature is more important than another. 
That's why, aLIME is an IF-THEN rules-based system that "anchors" a prediction features such that changing the others don't change de black-box model output. By this approach, precision (defined as how accurate humans are in those predictions) is needed but a too large set of rules only specific to a single instance is not useful for model understandability. Then the combinatorial aLIME problem if to find the shortest Anchor with high precision. 

## ILIME : Local and Global Interpretable Model-Agnostic Explainer of Black-Box Decision

This article showcase an ameliorated version of LIME explainer for classification black-box models. At first, LIME is a model agnostic explainer (it means that it can explain a model independently of its architecture) which outputs the local importance of a feature by an weight learned on perturbed features. This weight is then defined as the distance between the original feature representation and the perturbed one. Here, ILIME outperform this model by using the influence to explain the importance of a feature on a prediction. Formally, it is defined as scalar product between original weight of the prediction on the perturbed feature and the loss function gradient evaluated at this point. Finally, the final "importance" value of a feature on the model's prediction is defined as the product of its influence and its original LIME weight. Thus, a synthetic instance will have an important weight if its representation is near to the original feature one, and if it is able to modify the model prediction. 
To provide a global explanation of the model behavior, ILIME uses a set of local explanations and defines a dendogramm with hierarchical clustering on explanations (weights). If differs from LIME where the user needed to define the number of global explanation we wanted. 

## Anchors

This article presents Anchor, a new explanation systme for complex neural networks. Compared to previous linearly weighted combinaison of the input features, Anchors can be interpreted as local sufficient condition for prediction.

Anchors are build on a set of predicates $A$ called a "rules". We can also see it as a function of instances $x \in X$ :

$$A : 
	\begin{cases}
		X \longrightarrow \{0, 1\} \\ 
		x \longmapsto 
		\begin{cases}
			1 \text{ if all rules are true for } x \\
			0 \text{ otherwise}
		\end{cases}
	\end{cases}
		$$

To link an set of rules $A$ on a prediction $f(x)$ (where $f : X \longrightarrow Y$ is the black-box model, we can finally define Anchors of $x$ iff $A(x) = 1$ and $A$ is a sufficient condition for the prediction $y = f(x)$ :

$$	\mathbb{E}_{\mathcal{D}(z \mid A)}(1_{f(x)=f(z)} \geqslant \tau$$

with $\tau$ the desired level of precision of the Anchor on $x$.

Computing Anchors is the difficult part of the process. This is a combinatorial optimization problem if we decide to choose anchors whihch satisfy a precision constraint with high probability.

$$	\mathbb{P} (prec(A) \geqslant \tau) \geqslant 1 - \delta$$

with $ prec(A) = \mathbb{E}_{\mathcal{D}(z \mid A)}(1_{f(x)=f(z)}$ called the anchors "precision". Among those anchors, we choose the largest coverage ones, where coverage is :

$$cov(A) = \mathbb{E}_{\mathcal{D}(z)} (A(z))$$

Finally, the optimisation problem can be describe by :

$$\max_{\mathbb{P} (prec(A) \geqslant \tau) \geqslant 1 - \delta} cov(A)$$

Because the number of all possible anchor is exponential, we can perform an exhaustive search. That's why the article introduced the Bottom-Up approch:

1. **Initialization**: The anchor $A$ is initialized as an empty rule (applying to all instances).
2. **Candidate Generation**: In each iteration, a set of candidate rules $\mathcal{A}$ is generated by extending $A$ with one additional feature predicate $\{a_i\}$: $\mathcal{A} = \{A \wedge a_i, A \wedge a_{i+1}, A \wedge a_{i+2}, ...\}$
3. **Selection via Multi-Armed Bandit (MAB)**: To identify the best candidate without an exhaustive number of calls to $f$, the problem is formulated as a pure-exploration multi-armed bandit problem. The **KL-LUCB** algorithm is used to find the rule with the highest precision using a minimal set of samples.
4. **Termination**: The process terminates when a rule meets the statistical precision constraint: $\mathbb{P} (prec(A) \geqslant \tau) \geqslant 1 - \delta$

To address the limitations of a purely greedy search, the algorithm extends the construction to a **Beam Search** of size $B$.

- It maintains a set of $B$ current candidates instead of a single one.

- Among the multiple anchors identified that satisfy the precision threshold $\tau$, the algorithm outputs the one with the highest coverage $cov(A)$, effectively optimizing the original problem.

To provide a global understanding of the model, the article adapts a **Submodular Pick** (SP) procedure. The goal is to select a set of $K$ anchors that are non-redundant and cover as many instances in the validation set as possible.