### Section 1: Binomial Random Variables

#### Definition

A **binomial random variable** counts the number of successes in a fixed number of independent trials, each with two possible outcomes: *success* or *failure*. The distribution is defined by three components:

* $n$: Number of trials
* $p$: Probability of success on a single trial
* $x$: Number of observed successes (the binomial random variable)

#### Example Scenario

Jennifer surveys 20 college friends to find out how many play video games:

* Each response is a *Bernoulli trial* (either "yes" or "no")
* Probability of success (playing video games): $p = 0.5$
* Number of trials: $n = 20$
* Number of successes: $x$ (unknown until data is collected)

---

#### Mean (Expected Value)

The **mean**, or **expected value**, of a binomial distribution is given by:

$$
\mu = n \cdot p
$$

In Jennifer’s case:

$$
\mu = 20 \cdot 0.5 = 10
$$

*Interpretation*: On average, Jennifer can expect 10 of her 20 friends to say they play video games.

---

#### Standard Deviation

The **standard deviation** of a binomial distribution measures the expected variability from the mean:

$$
\sigma = \sqrt{n \cdot p \cdot (1 - p)}
$$

For Jennifer:

$$
\sigma = \sqrt{20 \cdot 0.5 \cdot (1 - 0.5)} = \sqrt{5} \approx 2.24
$$

*Interpretation*: Typical values should fall within about $\pm 2.24$ of the mean. That is, expected number of successes should range from:

* $10 - 2.24 = 7.76$
* $10 + 2.24 = 12.24$

Values outside this range may be considered statistically unusual.

---

#### Summary of Key Concepts

* A **binomial experiment** has:

  * Fixed number of trials ($n$)
  * Two possible outcomes per trial (success/failure)
  * Constant probability of success ($p$)
  * Independent trials

* A **binomial random variable** ($x$) counts the number of successes.

* **Mean (Expected Value)**:

  $$
  \mu = n \cdot p
  $$

* **Standard Deviation**:

  $$
  \sigma = \sqrt{n \cdot p \cdot (1 - p)}
  $$

These formulas help predict outcomes and determine whether observed results are typical or unusual in binomial contexts.

### Section 2: Understanding Binomial Experiments

#### Characteristics of a Binomial Experiment

A **binomial experiment** is a statistical trial structure with the following properties:

* A **fixed number of trials** (e.g., 20 students surveyed per class)
* **Only two possible outcomes** per trial (e.g., "yes" or "no")
* Each trial is **independent** (e.g., students respond individually)
* The **probability of success** is constant across trials

---

#### Application to Jeanette's Project

Jeanette investigates comfort with technology across three classes (technology, history, math) using a binomial framework.

##### Step 1: Formulate Hypotheses

Jeanette hypothesizes the following probability of students feeling comfortable with technology:

* Technology class: 80% (based on student interest)
* History and Math: not specified in detail here, but similar steps apply

##### Step 2: Theoretical Probability

The **theoretical probability** refers to the expected likelihood based on known or assumed probabilities without conducting the experiment.

* Because responses are binary ("yes" or "no"), the **default theoretical model** assumes a 50% chance for each response.
* Therefore, the **theoretical probability** of comfort is 50%.

##### Step 3: Actual Probability

Jeanette surveys 20 students in the technology class:

* 6 students respond "yes" (comfortable with tech)
* 14 students respond "no"

So the **actual probability** is calculated as:

* Ratio: $\frac{6}{20} = 0.30$
* Percentage: **30%**

This means only 30% of surveyed students feel comfortable with technology.

---

#### Comparing Hypothesis, Theoretical, and Actual Probability

| Type                     | Value | Explanation                                                  |
| ------------------------ | ----- | ------------------------------------------------------------ |
| Hypothesized Probability | 80%   | Jeanette’s guess based on expected class interest            |
| Theoretical Probability  | 50%   | Assumes equal chance of "yes" or "no" without survey data    |
| Actual Probability       | 30%   | Based on survey of 6 out of 20 students who reported comfort |

---

#### Key Concepts Review

* **Binomial Experiment**: Involves a set number of independent trials with binary outcomes.
* **Hypothesized Probability**: The initial belief or prediction about the outcome probability.
* **Theoretical Probability**: Calculated without experimentation, based on logical assumptions.
* **Actual Probability**: Determined from empirical data collected through experimentation.

These distinctions help in evaluating expectations vs. real-world data when conducting binomial experiments.
