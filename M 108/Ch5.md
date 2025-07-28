### Section 1: Random Variables

#### Definition

A **random variable** is a variable whose possible values are outcomes of a random phenomenon. It maps each outcome of a probability experiment to a numerical value and is denoted typically by capital letters like $X$, $Y$, or $Z$.

Each value of a random variable has a **probability** (or range of probabilities) associated with it, making it a central concept in probability and statistics.

---

#### Discrete Random Variables

A **discrete random variable** has **countable** outcomes, often represented as isolated points on the number line.

**Example:** Tossing two coins
Let $X =$ number of heads.

Possible values:

$$
X = 0, 1, 2
$$

**Probability distribution:**

| # of Heads | Probability |
| ---------- | ----------- |
| 0          | 0.25        |
| 1          | 0.5         |
| 2          | 0.25        |

This is a **probability distribution** showing all possible outcomes of $X$ and their probabilities. The total sum of probabilities always equals 1.

Discrete variables arise from **counting**, e.g., number of defective items, goals scored, heads flipped, etc.

---

#### Continuous Random Variables

A **continuous random variable** takes values within an **interval**. These variables are typically obtained from **measuring**.

**Example:** Student test scores
Let $X =$ test score (from 0% to 100%).

**Frequency distribution (interval-based):**

| Test Scores | Frequency (%) |
| ----------- | ------------- |
| 0% to <20%  | 5%            |
| 20% to <40% | 20%           |
| 40% to <60% | 30%           |
| 60% to <80% | 35%           |
| 80% to 100% | 10%           |

This forms a **relative frequency distribution**, and its graphical representation (like a histogram or density curve) has an **area of 1** under the curve.

Continuous variables include:

* Heights
* Times
* Weights
* Temperatures

These variables can assume **infinite values** within a range (including decimals or fractions).

---

#### Probability Rules for Random Variables

1. **Each probability** must be between 0 and 1:

   $$
   0 \leq P(X = x) \leq 1
   $$

2. **The total probability** across all possible values must equal 1:

   $$
   \sum P(X = x) = 1
   $$

For continuous random variables, this becomes the **area under the curve = 1**.

---

#### Classification Examples

**Example 1:**
Let $X =$ number of defective tires on a car (0 to 4).
→ Discrete random variable (countable values)

**Example 2:**
Let $X =$ running time of movies
→ Continuous random variable (measured time, often with decimals)

**Example 3:**
Let $X =$ number of tosses to get two heads in a row
→ Discrete random variable (values are countable and distinct, even if infinite)

Sample sequences:

* HH → $X = 2$
* THH → $X = 3$
* TTHH → $X = 4$
* … and so on

---

#### Summary

* A **random variable** assigns numerical values to the outcomes of a random process.

* **Discrete random variables**:

  * Have **countable** values.
  * Usually result from **counting**.
  * Represent **isolated points** on a number line.

* **Continuous random variables**:

  * Take on **any value in a range**.
  * Usually result from **measuring**.
  * Represent **intervals** on the number line.

* **Probabilities** for any value or interval are always between 0 and 1.

* **Total probability**:

  * For discrete: sum of all $P(X) = 1$
  * For continuous: area under the density curve = 1

Understanding random variables allows us to simplify complex descriptions into manageable models for **probability calculations**, **distributions**, and **statistical analysis**.

### Section 2: Understanding Discrete Variables

#### Definition

A **discrete variable** is a variable that results from **counting distinct outcomes**. It can only take on specific values — typically whole numbers — and **cannot be divided** into smaller parts. Discrete variables are often the result of experiments like rolling dice, flipping coins, or counting people.

When such a variable is **subject to chance**, it's called a **discrete random variable**. It represents unpredictable outcomes in a set of defined possibilities.

---

#### Example: Brady’s Dice Game

Brady needs to roll a **4** on a standard six-sided die and has **two chances** to do it. The variable here is:

$$
X = \text{number of times Brady rolls a 4}
$$

This is a **discrete random variable** because:

* The outcomes are countable (0, 1, or 2 times)
* Each die roll is independent
* He cannot roll “half a 4”

---

#### Expected Value

The **expected value** is the average number of successes we **expect** over a certain number of trials. It is calculated using the formula:

$$
\text{Expected Value} = n \times P
$$

Where:

* $n$ = number of trials
* $P$ = probability of success in a single trial

---

#### Example: Guessing on a True/False Quiz

Suppose you guess on a 10-question true/false quiz.

* $P = 0.5$ (chance of guessing correctly)
* $n = 10$ (number of questions)

$$
\text{Expected Value} = 10 \times 0.5 = 5
$$

So, you’d expect to get 5 questions correct by random guessing.

---

#### Applying Expected Value to Brady’s Game

Brady has **2 chances** to roll a 4.

* Probability of success in a single roll:

$$
P = \frac{1}{6}
$$

* Number of trials:

$$
n = 2
$$

$$
\text{Expected Value} = 2 \times \frac{1}{6} = \frac{2}{6} = 0.3333
$$

This means:

* On average, we expect **one 4 every 6 rolls**
* With **2 rolls**, Brady has a **low chance** of rolling a 4
* He can expect **less than one success**, so **he’s unlikely** to succeed

---

#### Why Expected Value Is Not a Guarantee

The expected value tells you what **typically** happens in the long run, not what will happen in a **specific** experiment. For example:

* 6 rolls → expect 1 four
* 100 rolls → expect about 16 or 17 fours
* 2 rolls → expect 0.3333 fours (i.e., likely none)

---

#### Summary

* A **discrete variable** represents outcomes from **counting**, not measuring.
* A **discrete random variable** models random outcomes with a finite or countable number of possibilities.
* **Expected value** is the **average number of successes** over $n$ trials, calculated as:

  $$
  \text{Expected Value} = n \times P
  $$
* In Brady’s case, with 2 rolls of a die and a 1-in-6 chance each time, he should expect **0.3333 successes**, meaning he's **unlikely to roll a 4**.

Understanding expected value helps you **predict probabilities** and make informed guesses in games, statistics, and real-life decisions.

### Section 3: Generating Discrete Probability Distributions

#### Definition

A **discrete probability distribution** lists all possible values of a **discrete random variable** along with their associated probabilities. These distributions are based on **countable outcomes** of random experiments, such as tossing coins, rolling dice, or betting in games like roulette.

A discrete probability distribution must satisfy two properties:

1. Each probability $P(X)$ is between 0 and 1.
2. The **sum of all probabilities** is 1.

---

#### Example: Tossing Two Coins

Let $X$ = number of **heads** when two coins are tossed.

**Possible outcomes:**
HH, HT, TH, TT
→ So, $X$ can be: 0, 1, or 2

**Probability Distribution:**

| Number of Heads (X) | Probability $P(X)$ |
| ------------------- | ------------------ |
| 0                   | 0.25               |
| 1                   | 0.50               |
| 2                   | 0.25               |
| **Total**           | **1.00**           |

---

#### Calculating Probabilities

* **P(0):** TT = $\frac{1}{2} \times \frac{1}{2} = 0.25$
* **P(1):** HT or TH = $0.25 + 0.25 = 0.50$
* **P(2):** HH = $\frac{1}{2} \times \frac{1}{2} = 0.25$

---

#### Expected Value

The **expected value**, denoted $E(X)$, is the **average outcome** of a random variable over many trials.

**Formula:**

$$
E(X) = \sum (X \cdot P(X))
$$

**Calculation for 2 coins:**

$$
E(X) = (0 \cdot 0.25) + (1 \cdot 0.50) + (2 \cdot 0.25) = 0 + 0.5 + 0.5 = 1
$$

On average, expect **1 head** per 2-coin toss.

---

#### Real-World Application: Roulette

Let’s say a roulette wheel has **38 slots**:

* Numbers 1–36 (18 red, 18 black)
* 0 and 00 (green)

**Betting on green:**

* Win: Net gain of **\$9** (win \$10 – \$1 bet)
* Lose: Net loss of **\$1**

Let $X$ = value of the game per spin.

| X (Gain/Loss) | Probability $P(X)$ |
| ------------- | ------------------ |
| -\$1          | 36/38 = 18/19      |
| +\$9          | 2/38 = 1/19        |

**Expected Value:**

$$
E(X) = (9 \cdot \frac{1}{19}) + (-1 \cdot \frac{18}{19}) = \frac{9 - 18}{19} = -\frac{9}{19} \approx -0.47
$$

**Interpretation:**

* On average, you **lose \$0.47** per \$1 bet on green.
* If you bet \$1 on green **100 times**, you’d expect to lose around **\$47**.

---

#### Summary

* A **discrete probability distribution** outlines possible outcomes and their probabilities.
* Probabilities:

  * Must be **between 0 and 1**
  * Must **sum to 1**
* The **expected value** tells you the **average** or **long-run** value:

  $$
  E(X) = \sum (X \cdot P(X))
  $$
* This concept is useful in understanding outcomes in experiments, **games of chance**, and **decision making** based on probabilistic outcomes.

### Section 4: Changing Data Into Probability

#### Interpreting Discrete Data

When we collect data — like the **number of cell phones per household** — it's often in the form of **raw counts**. To better interpret this data, we convert it into a **probability distribution**.

A **discrete random variable** is one that can take on a **finite or countably infinite number of values**. In our case:

$$
X = \text{Number of cell phones per household}
$$

Since households can’t have half a phone, $X$ is **discrete**.

---

#### Example: Households in Phonyville

| X = Cell Phones | Households | $P(X)$ = Proportion |
| --------------- | ---------- | ------------------- |
| 0               | 457        | 0.007147            |
| 1               | 18,763     | 0.293447            |
| 2               | 22,345     | 0.349468            |
| 3               | 12,534     | 0.196028            |
| 4               | 9,830      | 0.153738            |
| 5 or more       | 11         | 0.000172            |
| **Total**       | **63,940** | **1.000000**        |

These probabilities were computed as:

$$
P(X = k) = \frac{\text{Frequency of } k}{\text{Total households}}
$$

This forms a **discrete probability distribution** for $X$, and the sum of all probabilities equals **1**, as required.

---

#### Expected Value

To calculate the **expected number of cell phones per household**, use:

$$
E(X) = \sum X \cdot P(X)
$$

| X | P(X)     | $X \cdot P(X)$ |
| - | -------- | -------------- |
| 0 | 0.007147 | 0.000          |
| 1 | 0.293447 | 0.293          |
| 2 | 0.349468 | 0.699          |
| 3 | 0.196028 | 0.588          |
| 4 | 0.153738 | 0.615          |
| 5 | 0.000172 | 0.001          |
|   |          | **2.196**      |

So, the **expected number of cell phones per household** in Phonyville is **2.196**, or about **2.2**.

This value represents the **mean** of the distribution and reflects what we’d expect **on average**.

---

#### Real-Life Application: Insurance

Insurance companies use **empirical probability** and **expected value** to price policies. They analyze vast datasets to estimate risks and payouts, then use that information to set prices that cover **expected losses** and provide a **profit margin**.

---

#### Example: Life Insurance Policy

A company wants to price a **1-year \$100,000 policy** for a **20-year-old female**. According to their data:

* $P(\text{dies}) = 0.0025$
* $P(\text{lives}) = 0.9975$

Define $X$ as the **value of the policy to the company**:

| Outcome | Value to Company (X) | Probability P(X) |
| ------- | -------------------- | ---------------- |
| Dies    | –\$100,000           | 0.0025           |
| Lives   | \$0                  | 0.9975           |

**Expected value:**

$$
E(X) = (-100{,}000)(0.0025) + (0)(0.9975) = -250
$$

This means the company expects to **lose \$250** per such policy.

To break even, it must **charge \$250**. To make a profit of \$40 per policy, it should **charge \$290**.

---

#### Summary

* To convert data into a **probability distribution**:

  * Define the **random variable $X$**
  * Divide each frequency by the total to find $P(X)$

* A **discrete probability distribution**:

  * Lists each possible value of $X$ with its probability
  * Has total probability = 1

* The **expected value**:

  $$
  E(X) = \sum X \cdot P(X)
  $$

  * Tells you the **average outcome**
  * Used in planning, forecasting, and **risk analysis**

* **Real-life applications** include:

  * Insurance pricing
  * Business decisions
  * Risk assessment

Understanding these principles equips you to **make informed decisions using data and probability**.

### Section 5: Expected Value in Dice Games

#### What Is Expected Value?

The **expected value** (denoted $E(X)$) is a prediction of what a player can expect to **win or lose on average per game**. It is calculated as:

$$
E(X) = \sum \left( X \cdot P(X) \right)
$$

Where:

* $X$: Outcome value (e.g., win/loss)
* $P(X)$: Probability of that outcome

---

#### Game 1: Two Dice Game (Lose \$3 on 2, 4, 10; Lose \$2 on 7; Win \$1 on anything else)

**Step 1: Possible Outcomes and Probabilities (6-sided dice)**

* Total outcomes: $6 \times 6 = 36$

| Event      | Outcomes                                 | Count | P(X)  | X (Winnings) |
| ---------- | ---------------------------------------- | ----- | ----- | ------------ |
| Sum = 2    | (1,1)                                    | 1     | 1/36  | -\$3         |
| Sum = 4    | (1,3), (2,2), (3,1)                      | 3     | 3/36  | -\$3         |
| Sum = 10   | (4,6), (5,5), (6,4)                      | 3     | 3/36  | -\$3         |
| Sum = 7    | (1,6), (2,5), (3,4), (4,3), (5,2), (6,1) | 6     | 6/36  | -\$2         |
| Other sums | All remaining 23 outcomes                | 23    | 23/36 | +\$1         |

**Step 2: Compute Expected Value**

$$
E(X) = (-3)\cdot\frac{7}{36} + (-2)\cdot\frac{6}{36} + 1\cdot\frac{23}{36}
$$

$$
E(X) = \frac{-21 -12 + 23}{36} = \frac{-10}{36} = -0.28
$$

So, **on average you lose \$0.28 per roll**.

---

#### Game 2: Rolling Three Dice – Win \$100 on 3 Sixes, Lose \$1 Otherwise

**Step 1: Total outcomes with 3 dice:**

$$
6 \times 6 \times 6 = 216
$$

* Only 1 outcome gives triple sixes: (6,6,6)
* So:

  * $P(3 \text{ sixes}) = \frac{1}{216}$
  * $P(\text{anything else}) = \frac{215}{216}$

| Event    | X (Winnings) | P(X)    |
| -------- | ------------ | ------- |
| 3 Sixes  | +\$100       | 1/216   |
| All Else | –\$1         | 215/216 |

**Step 2: Compute Expected Value**

$$
E(X) = (100)\cdot\frac{1}{216} + (-1)\cdot\frac{215}{216}
$$

$$
E(X) = \frac{100 - 215}{216} = \frac{-115}{216} \approx -0.53
$$

You **lose about 53 cents per roll**.

---

#### Game 3: Two Four-Sided Dice (Sum = 7)

**Total outcomes:**

$$
4 \times 4 = 16
$$

**Ways to get sum of 7:**

* (3,4) and (4,3)

$$
P(7) = \frac{2}{16} = \frac{1}{8}
$$

You can calculate expected values similarly for any custom rule.

---

#### Summary

| Game                        | Expected Value | Interpretation                             |
| --------------------------- | -------------- | ------------------------------------------ |
| 2 Dice (Loss on 2,4,10 & 7) | –\$0.28        | Lose 28¢ per game on average               |
| 3 Dice (Win \$100 on 666)   | –\$0.53        | Lose 53¢ per roll of 3 dice                |
| 2 Four-Sided Dice (Sum = 7) | —              | $P(7) = \frac{1}{8}$, compute EV as needed |

* **Expected value tells you long-term average earnings or losses.**
* It helps players understand if a game is statistically in their favor.
* Casinos use EV to **ensure profitability** over many plays.




### Section 6: Drawing Cards and Dependent Probabilities

#### Dependent Events in Card Games

A **dependent event** occurs when the outcome of one event affects the probability of the next. This is common in card games where cards are drawn **without replacement**.

##### Example: Drawing Two Aces

From a standard 52-card deck:

* Probability first card is an Ace: 4/52
* Probability second card is also an Ace (after one Ace removed): 3/51
* Final probability:

  $$
  P(\text{Two Aces}) = \frac{4}{52} \cdot \frac{3}{51} = \frac{12}{2652} = \frac{1}{221} \approx 0.0045
  $$

So, there is a **0.45% chance** of drawing two Aces.

---

#### Blackjack and Probability

In **Blackjack (also known as 21)**, the goal is to get cards adding up to 21.

* Number cards: face value
* Face cards (J, Q, K): 10 points
* Ace: 1 or 11 points

##### Scenario: James Plays Blackjack

* James is dealt 2 cards.
* **Wins \$10** (net gain: \$5) if he gets an Ace **and** a 10-point card (10, J, Q, K).
* **Loses \$5** otherwise. Cards are reshuffled after each round.

---

#### Calculating Winning Probabilities

Let’s calculate the chance of James getting Blackjack.

There are **two winning sequences**:

1. **Ace first**, then 10-point card
2. **10-point card first**, then Ace

Each has the same probability:

* P(Ace first, 10-point card second) =

  $$
  \frac{4}{52} \cdot \frac{16}{51} = \frac{64}{2652} = \frac{16}{663}
  $$

* P(10-point card first, Ace second) =

  $$
  \frac{16}{52} \cdot \frac{4}{51} = \frac{64}{2652} = \frac{16}{663}
  $$

Total probability of winning:

$$
\frac{16}{663} + \frac{16}{663} = \frac{32}{663} \approx 0.048
$$

So, James wins **about 4.8%** of the time and loses **95.2%** of the time.

---

#### Expected Value of the Game

To compute **expected value**, multiply each outcome by its probability:

* Win \$5 with P = 0.048:

  $$
  5 \cdot 0.048 = 0.24
  $$
* Lose \$5 with P = 0.952:

  $$
  -5 \cdot 0.952 = -4.76
  $$

**Expected Value = 0.24 – 4.76 = -4.52**

James expects to **lose \$4.52 per round** on average.

| Outcome   | Value of X | P(X)  | X · P(X)  |
| --------- | ---------- | ----- | --------- |
| Blackjack | +\$5       | 0.048 | 0.24      |
| Not 21    | –\$5       | 0.952 | –4.76     |
| **Total** |            |       | **–4.52** |

---

#### Summary

* **Card draws without replacement** create **dependent probabilities**.
* Probability of **drawing two Aces**: 1/221.
* In **Blackjack**, the chance of being dealt a 21 is 32/663 or \~4.8%.
* The **expected value** for James is **–\$4.52**, meaning he loses money over time.
* These concepts illustrate how **dependent probabilities** and **expected value** are crucial for understanding and analyzing card games.

### Section 7: Probability in Poker

#### Combination Formula

To calculate the probability of poker hands, we use the combination formula:

$$
C(n, r) = \frac{n!}{r!(n - r)!}
$$

Factorials are used to count combinations. Use a calculator or web tool to compute values like `10!`.

---

#### Basics of a Fair Deck

* A standard deck has **52 cards** (no jokers).
* There are **4 suits**: hearts, spades, clubs, diamonds.
* Each suit has **13 ranks**: Ace through King.
* Example:

  * P(10♦) = 1/52
  * P(any Ace) = 4/52

---

#### Royal Flush

A Royal Flush: Ace, King, Queen, Jack, 10 — same suit.
There are **4** possible Royal Flushes (one per suit).

$$
\text{Total possible 5-card hands} = C(52, 5) = 2,598,960
$$

$$
\text{P(Royal Flush)} = \frac{4}{2,598,960} = \frac{1}{649,740}
$$

---

#### Straight Flush (excluding Royal Flush)

* A straight flush = 5 consecutive cards, same suit
* There are **9** possible straight flushes per suit
* Total = 9 × 4 = 36

$$
\text{P(Straight Flush)} = \frac{36}{2,598,960} ≈ \frac{1}{72,193}
$$

---

#### Flush

* A flush = 5 cards of same suit (not necessarily consecutive)
* Per suit:

  * C(13, 5) = 1,287
  * Remove 10 straight flushes (incl. Royal Flush): 1,287 – 10 = 1,277
* All suits:

  * 1,277 × 4 = 5,108

$$
\text{P(Flush)} = \frac{5,108}{2,598,960}
$$

---

#### Straight

* A straight = 5 consecutive cards of **any suit**
* 10 possible sequences (e.g., A-2-3-4-5 up to 10-J-Q-K-A)
* Each card in the 5-card hand can be any of 4 suits:

$$
4^5 = 1,024 \text{ suit combinations per sequence}
$$

$$
10 × 1,024 = 10,240 \text{ total combinations}
$$

* Subtract:

  * 4 Royal Flushes
  * 36 Straight Flushes

$$
10,240 – 4 – 36 = 10,200
$$

$$
\text{P(Straight)} = \frac{10,200}{2,598,960} ≈ \frac{1}{255}
$$
Here are your **"Probability in Poker"** notes properly **formatted and summarized** following your original style:


### Section 8: Understanding Lotteries and Expected Values

---

#### Expected Value

The expected value is the number of successful outcomes expected in an experiment:

$$
\text{Expected Value (E)} = n \times P
$$

Since there is only one winning ticket, we use:

$$
P = \frac{1}{n}
$$

---

#### Pick 4 Lotteries

Select 4 numbers from 1 to 10. No repetition. Order **does not** matter.

**Combination Calculation:**

$$
C(10, 4) = \frac{10!}{4!(10 - 4)!} = 210
$$

**Probability of Winning:**

$$
P = \frac{1}{210}
$$

---

#### Powerball-Type Lottery

Pick 6 numbers from 1–59 and 1 bonus number from 1–35. No repetition. Order **does not** matter.

**Main Number Combinations:**

$$
C(59, 6) = \frac{59!}{6!53!} = 45,057,474
$$

**Bonus Number Choices:**
35 possibilities

**Total Combinations:**

$$
45,057,474 \times 35 = 1,577,011,590
$$

**Probability of Winning:**

$$
P = \frac{1}{1,577,011,590}
$$

---

#### Summary

* Pick 4: Higher odds (1 in 210)
* Powerball-type: Extremely low odds (1 in 1.577 billion)
* Combinations calculated using factorial formula
* Bonus number multiplies total combinations
* Expected value determined by $P = \frac{1}{n}$

### Section 9: Games and Expected Values

#### Introduction

If you've studied **probability** and **statistics**, you know that outcomes can feel like a shot in the dark. For instance, rolling a die guarantees a result between 1 and 6 — so betting on a 7 is obviously unwise. Still, probability isn't random guesswork. In fact, it plays a key role in **game theory**, a mathematical field dedicated to logical decision-making.

This section explores **expected values** — anticipated outcomes of random events — and shows how they guide better choices in both gaming and real-life scenarios.

---

#### What is an Expected Value?

An **expected value (EV)** represents the average outcome of a random event if repeated many times. It’s a weighted average, accounting for all possible outcomes and their respective probabilities.

**Formula:**

$$
\text{Expected Value} = \sum ( \text{Value of Outcome} \times \text{Probability of Outcome} )
$$

Expected values help us determine the most **rational choice** in uncertain situations, particularly in games of chance or cost-benefit analyses.

---

#### Defining the Game

To use expected values effectively:

1. **Define the parameters** of the game or situation.
2. **List all possible outcomes.**
3. **Assign probabilities** to each outcome.
4. **Calculate the expected value** using the formula above.

**Example:** Rolling a fair six-sided die

* Possible values: 1, 2, 3, 4, 5, 6
* Probability of each: \$\frac{1}{6}\$
* Expected value:

$$
EV = \frac{1+2+3+4+5+6}{6} = 3.5
$$

Even though you can never roll a 3.5, it represents the long-run average if you rolled the die many times.

---

#### Example 1: Betting for a Card (Blackjack Strategy)

**Scenario:** You’re playing blackjack and have a hand value of 16. Should you hit or stay?

##### Case A:

* Your hand: King + 6 = 16
* Dealer shows a face card
* 48 cards remain in the deck
* 2 known 10-point cards are visible

**Analysis:**

* **Favorable outcomes:** 20 cards help (do not bust)
* **Unfavorable outcomes:** 28 cards cause a bust
* **Probability of improvement:**

$$
\frac{20}{48} \approx 41.7\%
$$

##### Case B:

* Your hand: 3 + 5 + 8 = 16
* Dealer shows a 4
* 47 cards left

**Analysis:**

* **Favorable outcomes:** 17
* **Unfavorable outcomes:** 30
* **Probability of improvement:**

$$
\frac{17}{47} \approx 36.2\%
$$

This shows that **expected value changes** depending on the **remaining cards and visible information**.

---

#### Example 2: Insurance Rates and Expected Value

**Scenario:** You're choosing between two car insurance plans:

* **High deductible, low premium**
* **Low deductible, high premium**

##### Decision Strategy:

Use expected value to balance risk vs. cost.

* If you **rarely drive**, your **expected chance of an accident is low**.
  → Favor the **high deductible** (lower monthly cost).

* If you **commute daily**, your **expected risk increases**.
  → Favor the **low deductible** (avoid large one-time payments).

**Expected value allows for a rational assessment of financial risk**, based on your driving habits and accident probability.

---

#### Summary

* **Expected value (EV)** is the predicted average result of an uncertain event.
* It helps evaluate **strategic decisions**, whether in games or real-world contexts.
* EV requires:

  * Defining the scenario
  * Listing all outcomes and their probabilities
* In **games** like blackjack, EV helps determine whether to draw another card.
* In **insurance**, EV informs cost-efficient decisions based on risk profiles.

Expected value is a **powerful decision-making tool** — not just in probability puzzles, but also in finance, insurance, and beyond.
