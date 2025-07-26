### Section 1: Logic and Critical Thinking in Mathematics

#### ***Understanding Logical Thinking***

* Logic is the study of how we **reason about propositions** — statements that are **either true or false**.
* Example:

  * *“If Judy likes all things round, and donuts are round, then Judy will love donuts.”*
  * This follows a logical structure based on ***true premises*** leading to a ***valid conclusion***.

---

#### ***What Are Propositions?***

* A ***proposition*** is a statement that can be clearly labeled as ***true or false***.
* Propositions may be:

  * **Simple sentences**: *“All triangles have three sides.”*
  * **Mathematical expressions**: *“x = 5”*, *“AB is a bisector of CD”*
* In mathematical logic, these propositions often include **symbols** and **mathematical terminology**.

*Examples*:

* *P: Judy likes all round things* (True)
* *Q: Donuts are round* (True)
* *Conclusion: Judy likes donuts* → valid inference based on P and Q.

---

#### ***Truth and Logic***

* In logical reasoning, if a statement is **given as true**, then:

  * You must **accept it as true**, even if it contradicts real-world knowledge.
  * Example: If a problem says *“2 + 2 = 5”* is true, treat it as true **only within that problem's context**.

---

#### ***Applying Critical Thinking***

* ***Critical thinking*** means using known truths to create ***new logical connections***.

*Example*:

* Given: `x = 5` and `y = 1`
* We can conclude:

  * *“If z = x + y, then z = 6”*
  * *“If z = x × y, then z = 5”*

*This is done using logical connectors and reasoning from known values.*

---

#### ***If-Then Statements in Logic***

* These are known as ***conditional statements*** or ***implications***.
* Form:

  * ***If P, then Q*** (written as `P → Q`)
  * Example:

    * If Judy likes all round things (P),
    * and Donuts are round (Q),
    * Then Judy likes donuts (`P ∧ Q → R`)

---

#### ***Lesson Summary***

* ***Logic*** is the foundation for ***critical thinking and proof-building*** in mathematics.
* A ***proposition*** is any clear statement that can be labeled true or false.
* In math, logic uses:

  * Plain language
  * Math symbols
  * Or a combination of both
* ***Critical thinking*** involves making new conclusions by combining what is already known to be true.
* Logical tools such as ***if-then statements*** allow us to **build inferences** and **derive new truths** from given information.

### Section 2: Propositions, Negation, and Truth Tables in Logic

#### ***What Is a Proposition?***

* A ***proposition*** is any **complete statement** that can be labeled as ***true (T)*** or ***false (F)***.
* Examples:

  * *"Maria has a blue dog."*
  * *"Kevin has a purple cat."*
  * *"Joann has a black rat."*
* These are **truth-assignable statements**, making them valid propositions in logic.

---

#### ***Negation***

* ***Negation*** is the logical reversal of a statement.
* Done by **adding or removing "NOT"** to flip the meaning.

  * Original: *"Maria has a blue dog."*
    Negation: *"Maria does not have a blue dog."*
  * Original: *"We are not in the year 1990."*
    Negation: *"We are in the year 1990."*

##### Truth Table for Negation:

| `p` | `¬p` |
| --- | ---- |
| T   | F    |
| F   | T    |

* If the original proposition `p` is **true**, the negation `¬p` is **false**, and vice versa.

---

#### ***Truth Tables***

* A ***truth table*** helps visualize all possible combinations of truth values for logical expressions.
* When we introduce **two propositions**, `p` and `q`, we get four possible combinations.

##### Basic Truth Table for Two Propositions:

| `p` | `q` |
| --- | --- |
| T   | T   |
| T   | F   |
| F   | T   |
| F   | F   |

---

#### ***Logical Connectors and Their Truth Tables***

---

##### **1. AND (`p ∧ q`)**

* True **only if both `p` and `q` are true**.

| `p` | `q` | `p ∧ q` |
| --- | --- | ------- |
| T   | T   | T       |
| T   | F   | F       |
| F   | T   | F       |
| F   | F   | F       |

---

##### **2. OR (`p ∨ q`)**

* True if **either or both** `p` or `q` are true.

| `p` | `q` | `p ∧ q` | `p ∨ q` |
| --- | --- | ------- | ------- |
| T   | T   | T       | T       |
| T   | F   | F       | T       |
| F   | T   | F       | T       |
| F   | F   | F       | F       |

---

##### **3. If-Then (`p → q`)**

* False **only if `p` is true and `q` is false**.
* Interpreted as a **promise** — the only way to break it is if the condition occurs and the outcome doesn’t.

| `p` | `q` | `p → q` |
| --- | --- | ------- |
| T   | T   | T       |
| T   | F   | F       |
| F   | T   | T       |
| F   | F   | T       |

---

##### **4. If and Only If (`p ↔ q`)**

* True when **both statements are either true or false**.

| `p` | `q` | `p ↔ q` |
| --- | --- | ------- |
| T   | T   | T       |
| T   | F   | F       |
| F   | T   | F       |
| F   | F   | T       |

---

#### ***Building Larger Truth Tables***

* Add a **third proposition** `r` → results in **8 combinations**:

| `p` | `q` | `r` |
| --- | --- | --- |
| T   | T   | T   |
| T   | T   | F   |
| T   | F   | T   |
| T   | F   | F   |
| F   | T   | T   |
| F   | T   | F   |
| F   | F   | T   |
| F   | F   | F   |

* This pattern scales exponentially with each added proposition.

---

#### ***Lesson Summary***

* A ***proposition*** is a statement labeled **true or false**.
* ***Negation*** reverses a statement’s truth value:

  * If `p` is true → `¬p` is false, and vice versa.
* A ***truth table*** displays all truth-value combinations for logic expressions.
* Key logical combinations:

  1. `p ∧ q` (AND): True if both are true.
  2. `p ∨ q` (OR): True if either or both are true.
  3. `p → q` (If-Then): False only when `p` is true and `q` is false.
  4. `p ↔ q` (If and Only If): True when both are the same.

Logic and truth tables help us structure and verify arguments — a foundational skill in both mathematics and computer science.

### Section 3: First Order Logic (FOL)

#### ***Overview***

In **Artificial Intelligence**, logic is used to express knowledge in a form understandable by machines. While **Propositional Logic** assigns simple **true/false** values to statements, it lacks the capacity to express the **structure, attributes, and relationships** of real-world entities. This limitation is addressed by **First Order Logic (FOL)**, also known as ***Predicate Logic***.

---

#### What Is First Order Logic?

***First Order Logic (FOL)*** is a **formal system** for representing knowledge that includes:

* A set of **objects**
* Their **attributes**
* **Functions** on those objects
* **Relationships** among them

The **basic syntax** of FOL:

```plaintext
predicate_or_function(object1, object2, ...)
```

---

#### Simple Statements in FOL

* Statement: *"Lily is tall"*
  → `tall(Lily)`

* Statement: *"Lily likes bananas"*
  → `likes(Lily, bananas)`

* Statement: *"Lily likes bananas and oranges"*
  → `likes(Lily, bananas) ∧ likes(Lily, oranges)`

* Statement: *"Lily likes bananas but not apples"*
  → `likes(Lily, bananas) ∧ ¬likes(Lily, apples)`

---

#### Logical Connectors in FOL

| **Name**           | **Symbol** |
| ------------------ | ---------- |
| AND (Conjunction)  | ∧          |
| OR (Disjunction)   | ∨          |
| Negation           | ¬          |
| Exclusive OR       | ⊕         |
| Implication        | →          |
| Double Implication | ↔          |

---

#### Quantifiers in First Order Logic

In natural language, quantifiers help express **"how many"** entities a statement refers to. FOL uses two types of quantifiers:

#### **1. Universal Quantifier (`∀`)**

* Denotes **all** objects.
* Syntax: `∀x: condition(x) → action(x)`
* Example:
  *Statement*: *"All girls like basketball."*
  → `∀x: girl(x) → like(x, basketball)`

#### **2. Existential Quantifier (`∃`)**

* Denotes **at least one** or **some** objects.
* Syntax: `∃x: condition(x) ∧ action(x)`
* Example:
  *Statement*: *"Some girls like basketball."*
  → `∃x: girl(x) ∧ like(x, basketball)`

> 🔍 **Rule of thumb**:
> *Use `→` (implication) with `∀` and `∧` (AND) with `∃`.*

---

#### Examples with Quantifiers

| **Natural Language Statement** | **FOL Expression**                |
| ------------------------------ | --------------------------------- |
| All animals eat grass          | `∀x: animal(x) → eat(x, grass)`   |
| Some animals eat grass         | `∃x: animal(x) ∧ eat(x, grass)`   |
| All dogs love their father     | `∀x: dog(x) → love(x, father(x))` |
| Some dogs love their father    | `∃x: dog(x) ∧ love(x, father(x))` |

Note how `father(x)` is a function returning the father of `x`.

---

#### Benefits of FOL in AI

* Allows **structured and relational** representations of knowledge.
* More **expressive and powerful** than propositional logic.
* Suitable for designing **intelligent agents** and **knowledge-based systems**.
* Readable and **easily executable** by machines.

---

#### Lesson Summary

* **Propositional Logic** is limited to labeling statements as ***true*** or ***false***.
* **First Order Logic (FOL)** extends this by modeling:

  * **Objects**
  * Their **attributes**
  * Their **relationships**
* Syntax:
  `predicate(attribute1, attribute2, ...)`
* **Quantifiers**:

  * Universal: `∀x: condition(x) → conclusion(x)`
  * Existential: `∃x: condition(x) ∧ conclusion(x)`

FOL enables machines to reason more like humans — using structure, context, and relationships.

### Section 4: Propositional Logic Algorithms: Definition & Types

#### ***Propositional Logic Overview***

*Propositional logic* combines definite truth-value statements (propositions) with formal logic rules. It is defined as any ***definite sentence that can be either true or false, but not both.***

#### ***Propositional Variables***

* Consider the statement: *"John's age is 13."* This is a proposition and can be represented as a variable.

  * P: *John's age is 13 years.*
* Another example: *"3 + 2 = 5."* This is always true.

  * Q: *3 + 2 = 5*
* P and Q are **propositional variables** — symbols that stand for propositions.
* Commonly used variables: `P`, `Q`, `R` (by convention, but any letters can be used).

#### ***Logical Connectives***

* Connectives are symbols that **combine two or more propositional variables**.
* Six basic connectives are defined for any two propositions, P and Q:

  * **AND (∧)**: True only if *both* P and Q are true.
  * **OR (∨)**: True if *either* P or Q is true (or both).
  * **NOT (¬)**: Negates the truth value of a proposition.
  * **Exclusive OR (⊕)**: True *only if* P and Q are opposite.
  * **Implication (→)**: True except when P is true and Q is false.
  * **Double Implication (↔)**: True if P and Q are *both* true or *both* false.

#### ***Truth Tables***

*Truth tables* list all possible truth value combinations for P and Q, along with the resulting values for each connective.

Example inference from the table:

* Implication (→):

  * `P → Q` is ***false only*** when P is true and Q is false.
  * Otherwise, it’s true — even if P is false and Q is true.

* Double Implication (↔):

  * `P ↔ Q` is true only when P and Q are either both true or both false.

*Note*: In some representations, **T** and **F** may be replaced with `1` and `0` respectively.

#### ***Forming Propositional Logic Using Sentences***

Given:

* P: *Mrs. Selva is a teacher.*
* Q: *I am a student.*
* R: *You haven't taken Mathematics as your subject.*

Now consider:
*"Mrs. Selva teaches only those students who have taken Mathematics as their subject."*

This can be expressed as:
`P ∧ (Q → ¬R)`

* `(Q → ¬R)` means: *If I am a student, then I have not avoided taking Mathematics.*
* Combined with P, this ensures Mrs. Selva teaches only such students.

#### ***Lesson Summary***

* **Propositional Logic** consists of sentences that are *true or false* — not both.
* It uses **propositional variables** like P and Q to simplify logic representation.
* **Logical connectives** such as ∧, ∨, ¬, ⊕, →, and ↔ combine and manipulate statements.
* **Truth tables** provide a structured way to analyze all possible outcomes.
* **Natural language statements** can be translated into logic using variables and connectives, enabling automated reasoning in AI systems.

### Section 5: What Is Knowledge Engineering?

#### **Definition and Purpose**

Knowledge engineering is the **discipline of capturing, structuring, and encoding human expert knowledge** into a format usable by computer systems. It mimics how domain experts make decisions, solve problems, and analyze information — enabling AI systems to perform complex tasks autonomously or with minimal guidance.

In practice, it supports systems in **teaching**, **medical decision-making**, **recommendation engines**, and more — wherever high-level human judgment needs to be automated or augmented.

---

#### **Core Processes in Knowledge Engineering**

Knowledge engineering involves several interrelated steps that bridge human insight with machine processing:

* **Knowledge Acquisition**: Extracting expertise from human experts, documents, and datasets.
* **Knowledge Representation**: Encoding that information in machine-readable formats (e.g., semantic models, rules, graphs).
* **Validation**: Ensuring the captured knowledge is accurate, consistent, and relevant.
* **Inferencing**: Creating systems that can reason with the encoded knowledge.
* **Explanation & Justification**: Allowing systems to explain their conclusions and decisions to users.

---

#### **Role Within Artificial Intelligence**

Knowledge engineering is a **foundational building block** of AI. While machine learning and neural networks dominate today's AI landscape, many systems still rely heavily on **explicitly encoded knowledge**, especially where:

* Decisions must be **explainable**
* Data is **sparse or highly specialized**
* Expert-level **precision** is essential (e.g., in medicine or law)

---

#### **Technological Enablers**

Several advancements make modern knowledge engineering more powerful:

* **Semantic Web**: Gives web data clear meaning through metadata and ontologies.
* **Cloud Computing**: Supports scalable data processing and storage.
* **Open Datasets**: Provide the raw material for training and testing knowledge-based systems.

These tools enable integration of structured and unstructured data, making systems more adaptable and intelligent.

---

#### **Key Building Blocks of AI (Knowledge Engineering Included)**

Knowledge engineering functions alongside other core AI components:

* Machine Learning & Deep Learning
* Natural Language Processing (NLP)
* Image and Speech Recognition
* Sensory Perception
* Cognitive Computing
* Robotics and Automation

Together, these elements form the full AI development stack.

---

#### **Responsibilities of a Knowledge Engineer (KE)**

The **knowledge engineer** acts as a translator between domain experts and AI systems. Key tasks include:

1. **Assessing the problem**: Understanding domain challenges.
2. **Modeling knowledge**: Building logical structures, semantic networks, or rule bases.
3. **Populating the model**: Filling it with expert content.
4. **Validation**: Testing performance and accuracy.
5. **Maintenance**: Updating systems as knowledge evolves.

---

#### **Real-World Examples**

* **IBM’s Voice of Customer Analytics (VoCA)**: Analyzes structured (e.g., purchase history) and unstructured (e.g., customer feedback) data to provide actionable CRM insights.

* **Alzheimer’s Diagnosis with Deep Learning**: Researchers trained a network using PET brain scans and medical literature to identify disease years before traditional methods.

* **Netflix’s Recommendation System**: Learns customer preferences through continuous feedback, refining suggestions using billions of user records and prior choices.

These examples show how **structured expert knowledge and machine learning models can work together**, creating smarter and more responsive AI systems.

---

#### **Lesson Summary**

Knowledge engineering is the **systematic process of transforming expert-level human knowledge into computational models**. It involves:

* Extracting and structuring expert knowledge
* Representing it in a way machines can understand
* Embedding it into intelligent systems that can reason and adapt

It is a **core pillar of artificial intelligence**, enabling systems to replicate — or even exceed — human-level reasoning in fields ranging from education to healthcare to entertainment.

### Section 6: Artificial Intelligence

#### Understanding AI Through a Real-Life Example

Kellen wants to design an app that helps people figure out how to run their errands more efficiently. For example, if he wants to get takeout from a good Mexican restaurant, the app will tell him which restaurant to go to, based on a number of factors. It will use the *parameters* and *goals* that Kellen sets up to figure out which restaurant is the best choice.

Kellen's app falls into the larger category of ***artificial intelligence***, which involves designing technology to solve problems based on information given to the technology. Essentially, artificial intelligence (AI) is about teaching programs to *‘think’* and *‘learn’* the way that humans do. If a human would consider things like traffic and customer ratings in choosing a restaurant, then Kellen wants his app to do the same thing.

#### Forward Chaining

One way that Kellen can program his app is to use ***forward chaining***, which involves starting with a set of rules and working toward a goal. Forward chaining helps a program figure out an answer by aligning the *starting point* with a set of predefined rules or parameters.

*Example*:

* Desiree uses an app that helps her identify animals.

  * If the animal has four legs and barks → *it is a dog*
  * If it has four legs and meows → *it is a cat*
  * If it has two legs and feathers → *it is a bird*
  * If it has two legs and hair → *it is a monkey*

This approach uses a rule-based structure with **if-then** logic. For instance:
*If X, then Y.* If the animal has four legs and barks, then it is a dog.

Forward chaining is often used in ***expert systems***, programs designed to perform specialized tasks that typically require human expertise, such as:

* Diagnosing medical conditions
* Making financial recommendations
* Identifying animals

These systems rely on **deductive reasoning**, which in logic can be expressed as:
`If X, then Y. X is true, therefore Y must also be true.`

#### Efficiency & Inefficiency

Forward chaining works best when:

* There is **one starting point** and **multiple possible outcomes**

It becomes inefficient when:

* There are **many starting points** and **only one end goal**
* There is **irrelevant or excessive information** to sift through

*Example*:

* Kellen is at home and wants nearby Mexican takeout.

  * Forward chaining works well here — the app can eliminate places beyond 5 miles or rated under 4 stars.
* But if **several people** are starting from **different places** and need to meet at **one restaurant**?

  * Forward chaining becomes inefficient.
  * In that case, ***backward chaining*** (starting from the goal and working backward) is more effective.

Additionally, **irrelevant data** can slow things down. For example:

* Number of turns on the route
* Non-Mexican restaurants nearby
  These don’t contribute to the goal and reduce the efficiency of the algorithm.

#### Lesson Summary

* **Artificial Intelligence (AI)** teaches machines to solve problems using structured logic.
* **Forward chaining** starts from known conditions and applies *if-then* rules to reach a conclusion.
* It is useful for systems with one starting point and many possible outcomes.
* It becomes inefficient with many starting points or when there's irrelevant data.
* **Backward chaining** is a better approach when there is *one specific goal* and *multiple inputs* leading to it.

### Section 7: Backward Chaining

#### *Backward Chaining*

Mariana is working on a program that will tell people how to achieve their savings goals based on where they are now. For example, if someone wants to save \$50,000 for a house down payment but they only have \$5,000 saved now, the program will suggest ways to get to the \$50,000, such as how much to save per month or how interest rates might impact how much or how long they will have to save.

Mariana is designing a computer program that solves problems, which means that it falls under the umbrella of *artificial intelligence*, or *AI*. **AI** is really about getting computers to do the problem-solving work that humans do through the use of *algorithms* to help figure out the best solution.

One type of AI algorithm is called *backward chaining*. To understand this better, let's take a closer look at what it is, as well as how and when it is used.

#### *Definition*

*Backward chaining* is a type of AI program that starts with a defined *end point* (or goal) and works *backward* to figure out the best way to get there. For example, if a person wants to save \$1 million for retirement, backward chaining can help them figure out how much they need to save each month to get there.

Backward chaining is a type of *goal-driven inference algorithm* that focuses on the best way to reach a goal.

* If the goal is to have \$1 million, the algorithm checks whether that goal has already been achieved.
* If it hasn’t, the algorithm determines what actions and *sub-goals* are needed to meet it.

  * For instance, if a user has \$1,000 now and wants to save \$1 million in 30 years:

    * The program determines the remaining savings target: \$999,000
    * Then breaks it down into sub-goals like:

      * Saving X dollars per month
      * Earning Y percent annually through investments

#### *Efficiency & Inefficiency*

Backward chaining is **efficient** when:

* There is **a single, clearly defined goal**
* There are **multiple possible starting points**
* The program can **focus all effort on reaching one outcome**

It is **inefficient** when:

* There is **no specific outcome or goal**
* There are **multiple possible conclusions** (e.g., plant identification with many possibilities)
* The algorithm must **sort through multiple hypotheses** without knowing the goal in advance

In such cases, *forward chaining* (which starts with known data and applies rules to reach conclusions) is more appropriate.

#### *Lesson Summary*

*Artificial intelligence (AI)* refers to using technology and algorithms to solve human-like problems. One such algorithm is **backward chaining**, which starts at the goal and reasons backward to find how to achieve it.

* In backward chaining:

  * The program checks if the goal is already met
  * If not, it identifies required actions and breaks them into sub-goals
  * It continues this process until the main goal is satisfied

*Backward chaining* is best used when the **goal is known** but the path is not. It's **not ideal** when there are many possible outcomes, in which case *forward chaining* is more effective.

### Section 8: What Is Artificial Intelligence?

#### *Definition*

**Artificial Intelligence (AI)** is the study and development of machines that are capable of possessing intelligence that is *equal to or greater than* human intelligence. AI has evolved from theory to application and is now used across a wide range of domains, including:

* Gaming: creating intelligent opponents
* Robotics: assisting in healthcare, manufacturing, and space exploration
* Software applications: such as **facial recognition**, **speech processing**, and **language translation**

AI doesn’t replicate just physical tasks—it also simulates decision-making, learning, and reasoning.

#### *Prolog in Artificial Intelligence*

**Prolog** (short for *Programming in Logic*) is a logic-based programming language heavily used in AI applications, especially those requiring *symbolic reasoning* or *rule-based inference*. Unlike procedural languages like `C++` or `Java`, Prolog uses a *declarative* approach:

* The user specifies:

  * **Facts** – statements assumed to be true
  * **Rules** – conditional logic describing relationships between facts
  * **Queries** – goals that the system tries to solve using facts and rules

The Prolog engine then evaluates these to determine the *truth or derivation* of the query.

##### *Examples in Prolog Syntax:*

*English:* “The boy is smiling.”
*Prolog:* `smiling(boy).`

*English:* “The boy smiles if he is happy.”
*Prolog:* `smiles(boy) :- happy.`

The symbol `:-` in Prolog means **"if"** and denotes a rule: “A is true **if** B is true.”

#### *Facts, Rules & Queries in Prolog*

* **Fact**: A basic, unconditional truth.
  *Example:* `rainy(seattle).`

* **Rule**: A conditional relation that connects facts.
  *Example:* `wet(X) :- rainy(X).`

* **Query**: A question posed to the AI.
  *Example:* `?- wet(seattle).`

When a query is issued, Prolog uses *backward chaining* to derive whether the query can be confirmed based on the facts and rules.

#### *Artificial Intelligence Today*

AI is embedded in many modern technologies and services:

* **Apple’s Siri**:

  * Uses **natural language processing** (NLP) to understand voice commands
  * Manages tasks like calling, messaging, or setting reminders
  * Learns user habits to improve future suggestions

* **Tesla’s Autopilot**:

  * Relies on AI to interpret inputs from sensors and cameras
  * Capabilities include:

    * Lane following
    * Automatic braking
    * Obstacle avoidance
  * Uses **machine learning** models to predict and prevent collisions

These examples show how AI combines hardware (e.g., sensors) and software (e.g., logic engines or neural networks) to deliver intelligent outcomes.

#### *Lesson Summary*

**Artificial Intelligence (AI)** involves the creation of machines capable of mimicking human intelligence and decision-making. **Prolog** is a logic-based programming language that excels in building such intelligent systems, particularly when problems are best expressed in terms of *facts*, *rules*, and *queries*.

Key points:

* **Fact** = something known to be true
* **Rule** = a conditional relationship
* **Query** = the goal the system attempts to solve

Applications of AI today—like **Siri** and **Tesla’s Autopilot**—highlight the practical power of combining *rule-based logic*, *learning algorithms*, and *real-world data*.
