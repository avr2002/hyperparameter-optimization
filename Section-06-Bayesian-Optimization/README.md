# Hyperparameter Tuning: Challenges


![alt text](./assets/response-surface.png)

- We can't define a formula to find the hyperparameters $\rightarrow$ **black box function**
- The response surface is not differentiable $\rightarrow$ it does not have a gradient
- Try different combinations of hyperparameter and evaluate model performance


# Sequential Search

- Grid Search and Random Search generate all the candidate points up front and evaluate them in parallel.

- For complex models(like Neural Nets.), we cannot use above methods due to very high number of parameters.

- **Sequential search** techniques pick a few hyperparameter settings, evaluate their quality, then decide where to sample next.

    - Iterative and sequential process
    - Not parallelizable
    - Goal: make fewer evaluations, only of those most promising candidate hyperparameters


## Sequential Search Trade-off

- Sequential search techniques pick a few hyperparameter settings, evaluate their quality, then **decide where to sample next.**

- Trade-off:
  - Less ML model training time $\times$ time to estimate where to sample next

- **Sequential search makes sense when the evaluation procedure (training the model – performance) takes much longer than the process of evaluating where to sample next.**


# Bayesian Optimization

- Bayesian optimization is a sequential strategy for global optimization of black-box functions, which does not assume any functional forms.

- Bayesian optimization is usually employed to optimize expensive-to-evaluate functions.

- Mathematically, we want to find the global maximizer(or minimizer) of an unknown(black-box) objective function f: 

$$x^{*} = \underset{x \in \chi}{\mathrm{arg max}}\, f(x)$$ 

where x are hyperparameters.

- **The objective function f:**

    - f is continuous
    - f is difficult to evaluate $\rightarrow$ too much time or money
    - f lacks known structure, like concavity or linearity $\rightarrow$ f is black-box
    - f has no derivative $\rightarrow$ we can’t evaluate a gradient
    - f can be evaluated at arbitrary points of x (the hyperparameters)
      - We can make point-wise observations of f

* **

$$x^{*} = \underset{x \in \chi}{\mathrm{arg max}}\, f(x)$$ 

**f is unknown**

1. In Bayesian optimization we treat $f$ as a random function and place a **prior** over it. *(the prior is a function that captures the belief-distribution, behaviour of f)*

2. Then, we evaluate f at certain points

3. With the new data, the prior (f original belief) is updated to a new the **posterior distribution**

4. The posterior distribution is used to construct an **acquisition function** *to determine
the next query point.*


**Estimating the prior:**

- Gaussian Process
- Tree-parzen estimator
- Random Forests

**Acquisition Function:** that determines the next point to evaluate on.

- Expected Improvement (EI)
- Gaussian process upper confidence bound (UCB)


