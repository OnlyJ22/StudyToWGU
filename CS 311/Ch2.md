### Section 1: Siri and Alexa

#### Introduction to Intelligent Agents

* When you interact with Siri (“Hey, Siri, what’s the weather?”) or Alexa (“Alexa, who won the game?”), you’re engaging with **intelligent agents**—tools of artificial intelligence designed to perceive, process, and respond to user requests.
* Intelligent agents are now common in smartphones, computers, home assistants (like Amazon Echo), and many other devices.

#### What is an Intelligent Agent?

* An **intelligent agent** is any system that can **perceive its environment** (using sensors), **process information** (using experience and knowledge), and **act or respond** (using actuators).

  * **Sensors:** Microphones, cameras, GPS, etc. (analogous to human senses)
  * **Actuators:** Speakers, displays, or other output mechanisms (analogous to human actions, like speaking or moving)
* Intelligent agents use vast data and computational resources to make decisions, improve with more data, and tailor responses to individual users.
* Example: **Self-driving cars** use cameras and GPS as sensors to perceive their environment, and actuators (steering, braking) to navigate roads safely.

#### Agent Classes

| Agent Type    | Description                                                                        | Example                                                   |
| ------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Simple Reflex | Acts only on current perceptions, no memory or history.                            | **Roomba**: Cleans floor when it detects dirt.            |
| Model-Based   | Uses memory/history to model both current and unknown parts of the environment.    | **Google Waymo**: Uses GPS history to predict routes.     |
| Goal-Based    | Like model-based but directed toward achieving a specific goal.                    | **Self-driving car**: Navigates to a programmed address.  |
| Utility-Based | Incorporates preferences and desirability to choose the best action toward a goal. | **GPS app**: Changes route to avoid accidents.            |
| Learning      | Learns and improves over time by acquiring new knowledge through experience.       | **Amazon Echo**: Gets smarter and more helpful over time. |

#### Summary

* **Intelligent agents** make decisions and take actions based on their perception of the environment and accumulated knowledge.
* They use **sensors** to gather data and **actuators** to carry out responses or actions.
* There are five main classes of intelligent agents:

  * **Simple Reflex**: Responds to immediate stimuli.
  * **Model-Based**: Uses history and environment models.
  * **Goal-Based**: Driven by specific goals.
  * **Utility-Based**: Considers the desirability of outcomes.
  * **Learning**: Improves by learning from experience and new data.

### Section 2: Intelligent Agents

#### Everyday Example

* After a long day, you put on the kettle and forget about it while changing clothes. When the kettle whistles, you rush back and instinctively drop it after touching the hot handle—a simple reflex to avoid being burned.
* **Simple reflexes** are found not only in humans but also in artificial intelligence systems.

#### Simple Reflex Agent

* A **simple reflex agent** is the most basic type of intelligent agent in AI.
* **How it works:**

  * It **perceives** its current environment.
  * It **acts** based on pre-determined rules responding to that environment.
  * It does **not** consider the past or anticipate the future.
* **Example:**

  * A home thermostat turns on the air conditioner if the temperature reaches a set point (e.g., 75°F), regardless of temperature trends from previous days.
  * A smart light bulb turns on at 6 p.m. every night, even if natural daylight lasts longer in summer.

#### Condition-Action Rule

* **Condition-action rule:** “If \[condition] occurs, then \[action] is taken.”

  * Example: “If the temperature reaches 75°F, then the AC turns on.”
* The agent follows **fixed responses**; it cannot modify or rethink its actions even if the condition is only slightly unmet.

  * For instance, if it’s already hot at 73°F, the simple reflex agent will not act until 75°F is reached.

#### Example: Robotic Vacuum Cleaner

* Robotic vacuums are **simple reflex agents**:

  * **Condition:** Senses dirt or debris on the floor.
  * **Action:** Initiates vacuuming.
  * **If the floor is clean:** The vacuum moves on, following its rule set.

#### Summary

* A **simple reflex agent** is a type of intelligent agent that acts based solely on its current percept—what it senses at the moment.
* It uses **pre-programmed, condition-action rules** to decide what to do.
* These agents **cannot learn**, adapt, or use history to modify their behavior.
* Common examples include thermostats, smart lights, and robotic vacuum cleaners that respond directly and only to present conditions.

### Section 3: Intelligent Agents Pt.2

#### Driverless Cars as Intelligent Agents

* **Waymo** (formerly Google’s autonomous car project) is an example of an **intelligent agent**: it observes its environment with sensors and takes action with actuators.
* Intelligent agents like Waymo are designed to operate independently in complex, real-world environments.

#### Model-Based Reflex Agents

* A **model-based reflex agent** uses both its **current perceptions** and its **internal memory** (percept history) to make decisions.

  * **Percept:** A lasting result of something perceived; not just a current observation but part of the agent’s internal memory.

* **Internal memory** allows these agents to understand things about their environment—even if not directly observable—by drawing on past experience.

  * Example: Waymo uses GPS and sensors to keep track of its location and surroundings.
  * It “learns” to associate red brake lights with slowing vehicles, so it knows when to apply brakes—even if it can’t directly see the driver ahead pressing the pedal.
  * It uses memory and modeling to estimate whether it’s safe to change lanes.

* **How model-based agents work:**

  * Build an internal model of their world using prior percepts and sensor input.
  * Use this model to make better, more flexible decisions in uncertain or partially observable situations.

* **Contrast with Simple Reflex Agents:**

  * Simple reflex agents only act on the current percept with fixed rules (e.g., “if dirty, then clean”).
  * Model-based agents can adapt based on what they’ve previously perceived, making them more robust in complex or changing environments.

#### Model-Based Cleaning Example

* **Roomba robot vacuums** use sensors to map the room and remember which areas have been cleaned.

  * The Roomba uses its **internal model** to avoid cleaning the same spot repeatedly and to cover the entire floor more efficiently.
  * It applies prior learning from previous cleaning sessions for a smarter, more thorough clean.

#### Summary

* A **model-based reflex agent** is an intelligent agent that uses both **current perceptions** and **internal memory** (percept history) to build a working model of the world.
* This internal model enables the agent to:

  * Fill in gaps where direct observation is not possible.
  * Make more adaptive and flexible decisions.
* Examples: **Waymo** self-driving car and **Roomba** vacuum cleaner—both use models built from past experiences to make better decisions in real time.
