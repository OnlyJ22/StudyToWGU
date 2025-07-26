### Section 1: Why Should I Write Pseudocode?

#### Purpose of Pseudocode

* Computer programs solve well-defined problems using algorithms, but these are first written in natural language (everyday words).
* Translating directly from natural language to computer code can be **tedious and complex**, especially when dealing with multiple programming languages.
* **Pseudocode** acts as an intermediate step: it is a set of specific instructions resembling computer code but is not tied to any one programming language and cannot be executed by a computer.
* Writing in pseudocode **makes it easier to plan, visualize, and later convert algorithms into actual code**.

#### How Do I Write Pseudocode?

* **Start with the algorithm**: Phrase it in a way that can easily translate to computer instructions.
* **Use indentation** to show loops (repeated steps) and conditional clauses (decisions).
* **Avoid language-specific keywords** so your pseudocode stays general and universal.
* Use **standard terms** for common structures:

  * **Loops:**

    * `FOR ... ENDFOR`
    * `WHILE ... ENDWHILE`
  * **Conditionals:**

    * `IF ... ENDIF`
    * `CASE ... ENDCASE`

#### Pseudocode Examples

* **Example 1:** Scanning a game board to count bombs

  * The algorithm checks each row and column for bombs, adding to a counter when one is found.
* **Example 2:** Printing bomb type and location

  * The algorithm prints details of what kind of bomb is found and where.

*These examples illustrate how pseudocode is easy to convert into code in any programming language, saving time and effort during development.*

#### Lesson Summary

* **Pseudocode** is a language-agnostic way to write step-by-step instructions, helping bridge the gap between natural language and computer code.
* Writing pseudocode simplifies planning, helps you **imagine program logic**, and streamlines converting ideas into working code for different computers.
* **Key steps:** Use standard terms, indent for loops and conditions, and avoid code tied to specific programming languages.

#### Key Terms

* **Pseudocode:** Step-by-step instructions similar to code, but not specific to any computer and not executable.
* **Loop:** A repeated set of instructions.

#### Learning Outcomes

* **Explain the usefulness of pseudocode:** It simplifies planning and coding for multiple languages.
* **Reiterate key steps:** Use standard terms, clear structure, and keep it language-independent.

### Section 2: Programming Languages

#### What Is a Programming Language?

* A **program** is a set of instructions telling a computer how to solve a problem.
* Programs are written using a **programming language**—a formal language for communicating instructions to a computer.
* There are **two major types** of programming languages: **low-level languages** and **high-level languages**.

#### Low-Level Languages

* **Low-level languages** are “low” because they are very close to how computer hardware communicates.
* They are **machine-oriented** and require deep knowledge of hardware.
* Two categories:

  * **Machine language (machine code):**

    * Only language directly understood by the computer; written as strings of 1s and 0s (binary).
    * Example: `10010101100101001111101010011011100101`
    * Extremely hard for humans to read or write.
  * **Assembly language:**

    * Uses symbols and letters (like `MOVE`, `ADD`, `SUB`).
    * Requires a translator program called an **assembler** to convert to machine code.
    * Used in operating systems, device drivers, and situations requiring precise timing or optimization.

#### High-Level Languages

* **High-level languages** use English-like words and mathematical symbols (e.g., `+`, `-`, `%`).
* Most commonly used by programmers for developing software.
* Examples: **C++, Fortran, Java, Python**
* **Advantages:**

  * Easier to learn and use—closer to human language.
  * Code is **portable**—can run on different hardware with little modification.
  * More accessible for beginners and complex application development.
* **Example:**

  ```python
  x = 100
  if balance < x:
      print('Insufficient balance')
  else:
      print('Please take your money')
  ```

#### Translating High-Level Code

* **High-level languages** must be translated to machine code to be executed.
* Two main methods:

  * **Compiler:**

    * Translates the entire source code to machine code before execution.
    * Produces a compiled file (e.g., `.exe`) that can be run repeatedly without recompiling.
    * Example languages: **C, C++, Java, Fortran**
    * **Advantage:** Does not reveal original source code; code runs faster.
  * **Interpreter:**

    * Translates and executes source code line by line during execution.
    * No compiled file is created; code must be interpreted every time it runs.
    * Example languages: **Python, Perl, Ruby**
    * **Advantage:** Flexible, allows for rapid testing and interaction.

#### Compiling vs. Interpreting: Analogy

* **Compiler:** Like translating a movie’s dialogue all at once, creating subtitles anyone can use later.
* **Interpreter:** Like live translation during a speech; translation occurs in real-time, not saved for future use.

#### Summary

* **Programming languages** can be low-level (machine code, assembly) or high-level (easier to read and write).
* Low-level languages are hardware specific and less portable.
* High-level languages use readable syntax and are portable across systems.
* **Compilers** translate code all at once before running; **interpreters** translate code line by line during execution.
* Compiled code runs faster and protects source code; interpreted code is flexible and good for interactive work.

### Section 3: Making Measurements

#### The Importance of Measurements

* **Scientific knowledge** relies on accurate and precise measurements, from chemistry to astronomy.
* As a scientist, making **accurate** and **precise** measurements is essential for credible results.

#### Accuracy vs Precision

* **Accuracy:** Agreement of a measurement with the true value.

  * Depends on the quality and calibration of the tool.

* **Precision:** Degree of agreement between repeated measurements.

  * Depends on the sensitivity and consistency of the measuring instrument.

* **Darts Example:**

  * Random dart hits: neither accurate nor precise.
  * One bullseye, others close: accurate.
  * All darts clustered, not at bullseye: precise.
  * All darts at bullseye: both accurate and precise.

#### Measuring with Different Tools

* The **smallest unit** on a measuring tool limits the accuracy and precision.

  * Ruler with only centimeters: must estimate tenths (uncertain digit).
  * Ruler with millimeters: can estimate to hundredths (more precise, less uncertainty).

#### Certain and Uncertain Digits

* **Certain digits:** Digits determined directly from the measuring instrument.
* **Uncertain digit:** The last digit, estimated by the measurer, which may vary from person to person.
* Every measurement should include all certain digits plus one uncertain digit.

#### Example: Measuring Liquid in Cylinders

* Cylinder A reads to tenths of a milliliter (e.g., 2.65 mL).
* Cylinder B reads to the nearest milliliter (e.g., 2.6 mL).
* **Always include one uncertain digit** in your answer.

#### Significant Figures (Sig Figs)

* **Significant figures:** All certain digits plus the one uncertain digit in a measurement.

* **Rules for identifying significant figures:**

  1. Any non-zero digit is significant.
  2. Zeros between non-zero digits are significant.
  3. Zeros after an integer and **after a decimal point** are significant.
  4. Zeros after an integer with **no decimal point** are NOT significant.
  5. Leading zeros are not significant.

* **Examples:**

  * 3.85 (three sig figs)
  * 12.055 (five sig figs)
  * 100 (one sig fig)
  * 19.0 (three sig figs)
  * 0.001 (one sig fig)

#### Calculations with Measurements

* When **adding or subtracting**, the result must have the same number of decimal places as the measurement with the fewest decimal places.

  * Example:
    3.85 cm (hundredths)
    19.0 cm (tenths)
    13 cm (ones)
    12.055 cm (thousandths)
    **Sum:** 47.905 cm → must round to the ones place → 48 cm (since the tenths digit is 9, we round up).
* When **multiplying or dividing**, the result must have the same number of significant figures as the measurement with the fewest sig figs.

  * Example:
    3.85 cm × 19.0 cm = 73.15 cm²
    Both have three sig figs, so answer is 73.2 cm² (rounded up).

#### Lesson Summary

* **Accuracy:** Closeness to true value.
* **Precision:** Consistency in repeated measurements.
* **Uncertain digit:** Last estimated digit in a measurement.
* **Significant figures (sig figs):** All certain digits plus one uncertain digit.
* **Addition/Subtraction:** Match the least precise decimal place.
* **Multiplication/Division:** Match the smallest number of significant figures among measurements.
* **Round up** if the first digit dropped is 5 or greater; otherwise, do not round.

### Section 4: Bayes' Theorem

#### What Is Bayes’ Theorem?

* **Bayes’ theorem** allows us to update the probability of an event based on new evidence.
* **Formula:**

  $$
  P(A|B) = \frac{P(A) \cdot P(B|A)}{P(B)}
  $$

  * *P(A)*: Prior probability of event A.
  * *P(B|A)*: Probability of B given A has occurred.
  * *P(B)*: Total probability of B.
  * *P(A|B)*: Posterior probability—probability of A after observing B.

#### How Does Bayes’ Theorem Work? (Simple Example)

* **Scenario:**
  Two bowls with different ratios of red and blue chips.

  * Bowl 1: 20 red, 20 blue.
  * Bowl 2: 30 red, 10 blue.
* **You pick a chip and it’s red. What’s the chance it came from Bowl 2?**

  * P(Bowl 2) = 0.5
  * P(red | Bowl 2) = 0.75
  * P(red | Bowl 1) = 0.5
  * P(red) = P(Bowl 1)×P(red|Bowl1) + P(Bowl 2)×P(red|Bowl2) = 0.5×0.5 + 0.5×0.75 = 0.625
  * P(Bowl 2|red) = (0.5×0.75) / 0.625 = **0.6**
  * So, the chip is more likely from Bowl 2.

#### Generalizing Bayes’ Theorem

* **When multiple possibilities exist** (like more than two bowls or dice), generalize using:

  $$
  P(A_k | B) = \frac{P(A_k) \cdot P(B|A_k)}{\sum_{i=1}^{n} P(A_i) \cdot P(B|A_i)}
  $$
* This allows you to update your beliefs about which scenario is true as new evidence arrives.

#### Worked Example: The Dice Game

* **Suppose**: Five dice (4, 6, 8, 12, 20 sides).
  Each die equally likely at first (prior = 0.2).

* **Roll 1: You get a 6.**
  Only dice with 6 or more sides are possible. Update probabilities using Bayes’ theorem:

  * For each die, calculate:
    P(die) × P(roll=6 | die)
  * Normalize by dividing each product by the sum of all products to get new probabilities (posterior).

* **Roll 2: You get a 5.**
  Repeat with new priors from Roll 1.

* **Roll 3: You get an 8.**
  Repeat again.

* **After each roll**, update your table to reflect your improved confidence in which die is being used, based on the accumulating evidence.

#### Bayesian Updating: Table Illustration

\| k | diek | Prior P(diek) | P(roll=6|diek) | Product | Posterior (after 6) |
\|---|------|---------------|---------------|---------|---------------------|
\| 1 | 4    | 0.2           | 0             | 0       | 0                   |
\| 2 | 6    | 0.2           | 0.1667        | 0.0333  | 0.392               |
\| 3 | 8    | 0.2           | 0.125         | 0.025   | 0.294               |
\| 4 | 12   | 0.2           | 0.0833        | 0.0167  | 0.196               |
\| 5 | 20   | 0.2           | 0.05          | 0.01    | 0.118               |
\|   | SUM  |               |               | 0.085   | 1.0                 |

* Continue updating with each new roll.

#### Applications of Bayes’ Theorem

* **Decision-making under uncertainty:** Medical diagnosis, spam filtering, AI systems, business decision support.
* **Bayesian inference**: The basis for learning in artificial intelligence—AI agents update their beliefs or predictions as they receive new data.

#### Lesson Summary

* **Bayes’ theorem** lets you update probabilities as new evidence is collected.
* The **generalized form** uses all possibilities and accumulates evidence over time.
* Applications range from games and gambling to artificial intelligence and real-world decision making.
* Bayesian reasoning is at the core of many modern AI systems.

### Section 5: Importance of Searching in Artificial Intelligence

#### ***Why Search Is Important***

* Humans use ***search*** constantly:

  * *In games*: *Evaluating next moves in Chess*
  * *In navigation*: *Choosing the shortest route*
  * *In everyday choices*: *Selecting green beans at a grocery store*
* Because AI simulates human decision-making, ***search is essential in AI systems***.

---

#### ***Search Visualization***

* To understand search in AI, we visualize the ***search space*** as a tree:

  * Each ***branch*** represents a possible decision.
  * ***Nodes*** show positions or states.
  * ***Arcs*** connect those nodes, mapping decisions.
* *Figure 1*: *Modelling the Search Space*
  *At each level of the tree, new decisions become available. For instance, from the leftmost yellow node, two child options appear.*

---

#### ***Types of Search in AI***

* Two major types:

  * ***Uninformed Search***
  * ***Adversarial Search***

---

#### ***Uninformed Search***

* Also called ***blind search***: uses **no external knowledge**.
* Contrasts with real-world decisions that consider multiple criteria.

---

#### ***Depth-First Search***

* Explores the ***leftmost unexplored path*** first.
* Backtracks upon reaching a dead end.
* *Figure 2*: *Depth-First Search Ordering*
  *Think of solving a maze by always turning left until you reach a dead end, then backtracking.*

---

#### ***Breadth-First Search***

* Explores ***all nodes at the current level*** before going deeper.
* Backtracks only when a level is fully explored.
* *Figure 3*: *Breadth-First Search Ordering*
  *Used in GPS routing: finds shortest paths when arcs represent distances.*

---

#### ***Least-Cost-First Search***

* Assigns a ***cost*** to each arc (e.g., distance, time).
* Chooses the ***lowest cost option*** from the current node.
* *Figure 4*: *Least-Cost-First Search Ordering*
  *Even though A–B–C–D is shorter (12 units), the driver picks A–C–D–B (13 units) because of lower individual step costs.*

---

#### ***Adversarial Search***

* Models ***competition*** between two players (e.g., Chess, Checkers).
* Known as ***Mini-Max Search***:

  * Player 1 maximizes their gain.
  * Player 2 minimizes Player 1’s gain.
* *Figure 5*: *Modelling 2-Person Games with Adversarial Search*
  *Even with a node valued at 10, Player 1 may only achieve 6 due to Player 2’s minimizing move.*

---

#### ***Key Concepts in Adversarial Search***

* ***Game Tree***: Alternating levels of player moves.
* ***Look-ahead value***: How many future moves are considered.

  * Human players: typically 3–5 moves.
  * AI programs: can explore deeply due to computational power.
* Used beyond games in:

  * *Military strategy*
  * *Business competition*
  * *Economic modeling (Game Theory)*

---

#### ***Lesson Summary***

* ***Search*** is central to both ***human reasoning*** and ***artificial intelligence***.
* Two major types:

  * ***Uninformed Search***: Depth-first, breadth-first, least-cost-first.
  * ***Adversarial Search***: Used in games and competitive scenarios via game trees.
* Success in AI search depends on ***structure, evaluation strategies,*** and ***look-ahead capability***.

### Section 6: Game Theory in Artificial Intelligence

#### ***What Is Game Theory?***

* ***Game theory*** is the study of **rational decision-making in multi-agent environments**.

  * In such systems, each agent's decision affects the others.
* It originated with ***John von Neumann***, who formalized its mathematical foundations.
* While it began with competitive games like *chess* and *poker*, it now applies to:

  * *Economics*
  * *Politics*
  * *Artificial Intelligence*

---

#### ***Game Theory and AI***

* Game theory plays a key role in many AI applications:

  * *Traditional games*: *Chess, Checkers, Poker*
  * *Advanced AI*: *Generative Adversarial Networks (GANs)*, *machine learning models*, *manipulation-resistant systems*
* AI problems can be categorized into two types:

  * A single agent solving a task.
  * ***Multiple agents*** where each agent’s action affects others — the core scenario for applying game theory.

---

#### ***Algorithms for Decision-Making in Game Theory***

---

#### ***Minimax Algorithm***

* One of the oldest and most widely used algorithms in AI for two-player games.
* Players alternate roles:

  * ***Max***: aims to maximize the outcome.
  * ***Min***: aims to minimize the outcome.
* A ***tree structure*** is used:

  * Each level of the tree is assigned to Max or Min alternately.
  * The bottom level represents possible outcomes.
  * The goal is to propagate optimal choices upward from leaves to the root.

*Example structure*:

* *Level 4 (leaf nodes)*: *Outcomes like -7, 3, 6*
* *Level 3 (Min’s turn)*: *Choose minimum from children*
* *Level 2 (Max’s turn)*: *Choose maximum from children*
* Continue until the root is reached.
* A ***positive value*** at the root implies Max wins; a ***negative value*** means Min wins.
* In our example, Max ends with `-7` → ***Min is the winner***.

---

#### ***Alpha-Beta Pruning Algorithm***

* Enhances the Minimax algorithm by ***avoiding unnecessary evaluations***.
* Uses two values to prune branches:

  * `α` (alpha) = the best value Max can guarantee.
  * `β` (beta) = the best value Min can guarantee.
  * Initial values: `α = -∞`, `β = +∞`

*The pruning condition:*

* If `α ≥ β`, the branch is cut off — it won’t affect the final decision.

*Example breakdown*:

* Start at node A with `α = -∞`, `β = +∞`
* Move to B, then D:

  * D explores children: gets values 4 and 5 → D returns 5 to B
* At B: `β = 5`, now E is explored

  * E sees value 12 → `α = 12` → Since `β = 5`, the condition `α ≥ β` is met
  * E’s remaining subtree is ignored
* B returns 5 to A → A updates `α = 5`
* A continues to evaluate the C branch

*Alpha-beta pruning saves computation by ***eliminating paths*** that won't affect the outcome.*

---

#### ***Move-Ordering Algorithms***

* Move-ordering algorithms apply ***heuristics*** to:

  * Improve the ***efficiency*** of Minimax and Alpha-Beta
  * Determine which moves to examine first
* These are more advanced and require additional theoretical background.

---

#### ***Lesson Summary***

* ***Game theory*** provides a framework for rational decision-making in multi-agent systems.
* Widely used in AI when more than one agent interacts or competes.
* ***Minimax Algorithm***:

  * Explores all game outcomes to determine optimal moves.
* ***Alpha-Beta Pruning***:

  * Optimizes Minimax by avoiding branches that won’t influence the result.
* Together, these algorithms form the foundation of decision-making in AI games and strategic modeling.

### Section 7: Splitting Datasets in AI and Machine Learning

#### ***Why Splitting Datasets Matters***

* Dataset splitting is a ***fundamental process*** in machine learning and AI.
* It ensures:

  * Models **learn from one subset** (training).
  * And are **evaluated on a different subset** (testing).
* This separation helps assess how well a model ***generalizes*** to unseen data.

---

#### ***Avoiding Overfitting and Underfitting***

* ***Overfitting*** occurs when a model memorizes patterns, failing on new data.
* ***Underfitting*** happens when a model is too simple to capture meaningful trends.
* Splitting allows developers to detect and prevent both issues.
* It also manages the ***bias-variance trade-off***:

  * ***Bias***: Error from assumptions (too simple).
  * ***Variance***: Error from sensitivity to data fluctuations.

---

#### ***Train and Test Datasets***

* In ***supervised learning***, we split data to:

  * Train the model on known inputs and outputs.
  * Test it on ***unseen inputs*** to assess prediction accuracy.
* Without splitting:

  * Models may only perform well on known data.
  * Performance metrics may be ***misleading***.

*Example*:

* A housing price dataset with 1000 records:

  * *Training set (80%)*: *800 records*
  * *Test set (20%)*: *200 records*
* Model is trained on square footage, rooms, etc., then tested on new records using metrics like *R²* or *mean squared error*.

---

#### ***Validation Sets***

* A ***validation set*** adds a third stage:

  * Used for ***tuning*** and ***hyperparameter selection*** during development.
  * Prevents ***test set contamination***.
* Typical split:

  * *Training set*: model learning
  * *Validation set*: parameter tuning
  * *Test set*: final evaluation

*Example*:

* In decision trees: the ***depth*** can be selected using validation performance, while test data remains untouched.

---

#### ***Splitting Techniques***

* Various strategies exist based on data characteristics:

  * **Random Splitting**:

    * Shuffles and splits data.
    * Common ratios: *80/20*, *70/30*.
    * Assumes independent and identically distributed (i.i.d.) data.

  * **Stratified Splitting**:

    * Maintains class balance in classification problems.
    * Useful for imbalanced datasets (e.g., *fraud detection*).

  * **Time-Based Splitting**:

    * For *time series* or *sequential data*.
    * Preserves chronological order — avoids *data leakage*.

  * **K-Fold Cross-Validation**:

    * Divides data into *K* folds.
    * Trains model *K* times with rotating test folds.
    * Reduces dependency on a single split and yields stable performance estimates.

---

#### ***Insufficient Data Challenges***

* When datasets are small:

  * Splitting becomes more delicate.
  * Risk of overfitting increases.
* Solutions:

  * Use ***K-fold cross-validation*** to rotate training and test data.
  * Apply ***stratification*** to preserve class balance in small subsets.
  * ***Simplify the model*** or ***reduce features*** to improve generalization.

---

#### ***Impact on Model Evaluation***

* Evaluation metrics depend heavily on ***splitting quality***:

  * Poorly chosen test sets (e.g., overlapping with training data) → ***inflated scores***.
  * Properly split sets provide ***realistic performance expectations***.
* Important when ***comparing models***:

  * Must use the ***same split*** to ensure fairness.
  * Inconsistent splitting leads to misleading comparisons.

---

#### ***Model Selection and Tuning***

* During tuning:

  * The ***validation set*** is used iteratively.
  * The ***test set*** is preserved for final reporting.
* This structure:

  * Prevents ***overfitting to validation data***.
  * Maintains ***objective evaluation*** of final model performance.

---

#### ***Lesson Summary***

* ***Train-test splitting*** is a core principle in ML/AI:

  * Ensures reliable evaluation.
  * Guards against overfitting.
  * Clarifies generalization ability.
* Introducing a ***validation set*** strengthens the development cycle:

  * Enables tuning without contaminating test results.
* Common techniques:

  * **Random**, **Stratified**, **Time-Based**, **K-Fold Cross-Validation**
* When data is scarce:

  * Use techniques like ***cross-validation*** and ***model simplification***.
* Ultimately, ***splitting strategy*** influences every aspect of model development — from tuning to evaluation to deployment.
