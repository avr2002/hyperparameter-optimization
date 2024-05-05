# Recap

- **Hyperparameter Optimization**
  
    - The process of finding best hyperparameters for a given dataset is called **Hyperparameter Optimization/Tuning.**

    - The best hyperparams are those that maximize the perf. of the ML algorithm.

- **Hyperparameter Tuning: Search**

    - A search consists of:
      - Hyperparameter Space
      - A method of sampling candidate hyperparams
      - A cross-validation scheme
      - A performance metric to maximize/minimize.

- **Hyperparameter Tuning: Challenges**

    - The critical step is to choose how many different hyperparameter combinations we are going to test.
    
    - As the # of hyperparams combinations $\uparrow$, $\rightarrow$ the chance of getting a better model, and $\uparrow$ the computational cost.

    - **Low Effective Dimension:** 
      - Some hyperparameters affect performance a lot, but most do not have huge impact on model performance
      - Also, the model performance only increases within a certain range of range of parameter value, increasing it furthur doesn't change the model perf.

- **Hyperparameter Nature**

    - Some hyperparameters are discrete
      - E.g.: number of estimators in ensemble models
    
    - Some hyperparameters are continuous
        - Penalization coeff.
        - Number of samples per split
    
    - Some hyperparameters are categorical:
      - Loss(deviance, exponential)
      - Regularization(Lasso(L1), Ridge(L2))

- **Hyperparameter Tuning: Considerations**
  
  -  When we create hyperparameter sampling strategies we need to consider:
     -  Number of hyperparameters of the ML Model
     -  The Low Effective dimension
     -  The nature of the parameters (discrete, continuous)
     -  The computing resources available

- **Basic Hyperparameter Tuning Methods**
    - Manual Search
    - Grid Search
    - Random Search


# Grid Search

- Examines all possible combinations of the specified hyperparameters.
- Cartesian product, Combinations: $hyp_1 \times hyp_2 \times \dotsc \times hype_n$

- **Limitations:**
  
  - **Curse of dimensionality:** possible combinations grow exponentially with the number of hyperparameters
  - Computationally expensive
  - Hyperparameter values are determined manually
  - **Not ideal for continuous hyperparameters**
    - A subset of "reasonable" hyperparameter values are set manually
  - Does not explore the entire hyperparameter space (not feasible)
  - It performs worse than other searches (for models with complex hyperparameter spaces)

- **Advantages:**
  
  -  For models with simpler hyperparameter spaces works well
  -  It can be parallelized. If run in parallel, it is fast in terms of wall clock time
  -  Sometimes, we run a small grid, determine where the optimum lies, and then expand the grid in that direction.


# Random Search

- Hyperparameter values are selected by independent (random) draws from a uniform distribution of the hyperparameter space

- In plain English, Random Search selects the combinations of hyperparameter values at random from all the possible combinations given a hyperparameter space.

- Random Search is effective beacuse of **Low Effective Dimension**.

- **Advantages:**
    - Random Search allows the exploration of more dimensions of the important parameter
      - Grid Search wastes time exploring non-important dimensions 
    
    - Random Search selects values from a distribution of parameter values
      - As opposed to Grid Search where parameters are defined manually.
    
    - Random Search is suitable for continuous hyperparameters

* **

- It can be parallelized.
- High efficiency in high dimensional spaces.
- Well suited for continuous hyperparameters.

* **

- Disadvantage: Small reduction in efficiency in low dimensional spaces

* **

- **Random Search - Considerations**
    - We choose a (computational) budget independently(ish) of the number of parameters and possible values.

    - Adding parameters that do not influence the performance does not decrease efficiency of the search (if enough iterations are allowed).
  
    - Important to specify a continuous distribution of the hyperparameter to take full advantage of the randomization.

    - With 60 combinations of hyperparams, it is suggested that we can get optimal hyperparams with 95% prob.


* **

#### See Demo of `scikit-optimize` & `hyperot` in demo notebooks