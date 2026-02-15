Question 1: What is the fundamental difference between predictive modeling and causal inference?
A) Predictive modeling uses larger datasets
B) Causal inference asks what happens to Y if we intervene on X, while prediction asks what Y is expected to be given observed X
C) Predictive modeling cannot use observational data
D) Causal inference always requires randomized experiments

Correct Answer: B
Explanation: Causal inference (Pearl’s do-operator, P(Y|do(X))) focuses on the effect of interventions, while prediction (conditional associations, P(Y|X)) focuses on associations. Option A is irrelevant, Option C is incorrect because prediction often uses observational data, and Option D is incorrect because methods like propensity score matching allow causal inference from observational data.


Question 2: In the UCI Adult Census dataset, age influences both the likelihood of holding a graduate degree and income level. What is age in this context?
A) A mediator
B) A collider
C) A confounder
D) An instrumental variable

Correct Answer: C
Explanation: A confounder is a variable that influences both the treatment and the outcome, creating a backdoor path. Age independently affects education attainment and income. A mediator lies on the causal path between treatment and outcome, while a collider is caused by both treatment and outcome. An instrumental variable affects treatment but not outcome directly.


Question 3 Why should occupation NOT be included as a confounder when estimating the causal effect of education on income?

A) Occupation data is unreliable
B) Occupation is a mediator — education causes occupation, which causes income
C) Occupation is not related to income
D) Occupation is a collider between education and income

Correct Answer: B
Explanation:
Occupation happens after education. Education affects what job someone gets, and that job affects income. If we control for occupation, we block part of education’s effect on income and underestimate the total effect.


Question 4 What does the backdoor criterion identify?

A) Variables that should be used as outcomes
B) Variables that are caused by the treatment
C) The minimum set of variables to condition on to block all non-causal paths between treatment and outcome
D) The strength of the causal effect

Correct Answer: C
Explanation:
The backdoor criterion tells us which variables to control for so we remove bias from confounding paths while keeping the true causal path open.



Question 5 In our analysis, the naive income gap between graduate degree holders and non-holders was 41.6%. After propensity score matching, it dropped to 27.2%. What does this tell us?

A) The graduate degree has no causal effect on income
B) Approximately one-third of the observed gap was due to confounders like age and hours worked, not the degree itself
C) Propensity score matching always reduces the estimated effect
D) The original dataset was too small for reliable analysis

Correct Answer: B
Explanation:
The drop shows that part of the original 41.6% gap was due to differences between the groups. After adjusting for confounders, 27.2% remains as the estimated causal effect.



Question 6 What is a propensity score?

A) The probability of receiving treatment given observed covariates
B) The probability of the outcome given the treatment
C) The average treatment effect
D) The correlation between treatment and outcome

Correct Answer: A
Explanation:
A propensity score is the probability that someone receives treatment based on their characteristics. It helps make fair comparisons between similar individuals.



Question 7 In the LaLonde job training analysis, the naive estimate ($1,794) and the propensity score matching estimate ($1,736) were very similar. Why?

A) Propensity score matching does not work on small datasets
B) The treatment was randomly assigned, so there was little confounding to correct for
C) The confounders were not measured correctly
D) The outcome variable had too little variation

Correct Answer: B
Explanation:
Because the study was randomized, the treatment and control groups were already balanced. There wasn’t much bias to fix, so both estimates were similar.


Question 8 What does the placebo treatment refutation test do?

A) Adds more confounders to the model
B) Tests whether the outcome variable is normally distributed
C) Removes outliers from the dataset
D) Replaces the real treatment with a random variable and checks if the effect disappears

Correct Answer: D
Explanation:
The placebo test randomizes the treatment variable. If the estimated effect disappears, that supports that the original result was real.



Question 9 What is the unconfoundedness assumption?

A) After conditioning on observed covariates, treatment assignment is independent of potential outcomes
B) The treatment must be binary
C) The sample must be randomly selected from the population
D) All variables in the dataset must be included in the model

Correct Answer: A
Explanation:
Unconfoundedness means that after controlling for certain variables, treatment is essentially random. No hidden factors are influencing both treatment and outcome.



Question 10 What happens if you condition on a collider in a causal analysis?

A) It removes confounding bias
B) It has no effect on the estimate
C) It introduces a spurious association between the collider's causes
D) It always makes the estimate more accurate

Correct Answer: C
Explanation:
When you control for a collider, you accidentally create a false relationship between its causes, which adds bias.



Question 11 Why is it important to assess missing data mechanisms before imputation in causal analysis?

A) Missing data always makes the dataset too small to analyze
B) If missingness is related to both treatment and outcome, it can introduce confounding bias
C) Imputation is never appropriate in causal inference
D) Missing data only affects predictive models, not causal models

Correct Answer: B
Explanation:
If missing data is connected to both treatment and outcome, it acts like a hidden confounder. Imputing without understanding this can introduce bias.


Question 12 In our analysis, we used three different estimation methods (PSM, IPW, OLS) for Example 1. Why is using multiple methods valuable?

A) It guarantees the correct answer
B) Different methods always produce the same result
C) It is required by the DoWhy library
D) If multiple methods with different assumptions produce similar estimates, this increases confidence in the result


Correct Answer: D
Explanation:
Each method makes different assumptions. If they all give similar results, we can be more confident the estimate is reliable.



Question 13 What does SUTVA (Stable Unit Treatment Value Assumption) require?

A) One person's treatment assignment does not affect another person's outcome
B) The treatment must be stable over time
C) The treatment effect must be the same for everyone
D) The dataset must have equal numbers of treated and control units

Correct Answer: A
Explanation:
SUTVA means there is no interference. One person’s treatment should not change someone else’s outcome.


Question 14 One-hot encoding is preferred over ordinal encoding for categorical variables in propensity score models. Why?

A) One-hot encoding creates smaller datasets
B) One-hot encoding does not impose an arbitrary ordering on categories that may not have a natural hierarchy
C) Ordinal encoding is incompatible with logistic regression
D) One-hot encoding always improves prediction accuracy

Correct Answer: B
Explanation:
Ordinal encoding assigns numbers that suggest a ranking. Many categories don’t have a natural order, so one-hot encoding avoids introducing false structure.




Question 15 Comparing our two examples, what key insight emerges about when causal adjustment matters most?

A) Causal adjustment is always necessary regardless of study design
B) Causal adjustment matters most in observational data where treatment is not randomly assigned, as shown by the large difference between naive and adjusted estimates in Example 1 versus the small difference in the randomized Example 2
C) Causal adjustment only works with large datasets
D) Causal adjustment is unnecessary when using propensity score matching

Correct Answer: B
Explanation:
In observational data, confounding can strongly bias results, so adjustment makes a big difference. In randomized experiments, groups are already balanced, so adjustment changes very little.
