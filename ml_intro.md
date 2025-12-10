---
title: Introduction to Machine Learning and Machine Learning Systems
author: Raffi Khatchadourian (based on material from Christian Kaestner and Eunsuk Kang)
date: December 10, 2025
semester: Fall 2025
footer: Based on "Machine Learning in Production/AI Engineering" by Christian Kaestner and Eunsuk Kang, Carnegie Mellon University
license: Creative Commons Attribution 4.0 International (CC BY 4.0)
---

# Challenges in Engineering Machine Learning (Software) Systems

## Disclaimer

New part of the course.

## Recall

:::::::::::::: {.columns}
::: {.column width="50%"}

![AI vs. ML](graphics/AIvsML.jpg){width=90% title="Courtesy Eunsuk Kang."}

:::
::: {.column width="50%"}

### Machine Learning (ML)

- In ML, the system *learns* patterns from data and uses these patterns to make predictions or decisions on new, unseen data or generate "new" data.

### Machine Learning (ML) Systems

- An ML system is a software system that incorporates machine learning models to perform specific tasks or provide certain functionalities.
- The ML component of an ML system may be relatively small compared to the overall system, but it plays a crucial role in enabling "intelligent" behavior.
   - This includes *personalization*, i.e., adapting behavior based on user data and preferences.
- ML systems often involve data collection, preprocessing, model training, evaluation, deployment, and monitoring.

:::
::::::::::::::

## Challenges in ML Systems

- Building and maintaining ML systems presents unique challenges compared to traditional software systems.
- These challenges arise from the inherent complexity of ML models, data dependencies, and the dynamic nature of real-world environments where these systems operate.

## Traditional Programming vs ML

![Programming vs ML](graphics/programming-vs-ml.png){title="Courtesy Eunsuk Kang."}

## Complexity in Engineering (Software) Systems

![Airplane](graphics/airplane.jpg){title="Courtesy Eunsuk Kang."}

* Automobile: ~30,000 parts; Airplane: ~3,000,000 parts
* MS Office: ~ 40,000,000 LOCs; Debian: ~ 400,000,000 LOCs

> Q: How do we build such complex systems?

## Managing Complexity in Software

* **Abstraction**: Hide details & focus on high-level behavior.
* **Reuse**: Package into reusable libraries & APIs with well-defined _contracts_.
* **Composition**: Build large components out of smaller ones.

```java
public class Algorithms {

    /**
     * Finds the shortest distance between to vertices <code>v1</code>
     * and <code>v2</code> in graph <code>g</code>.
     *
	 * This method is only supported for connected vertices.
     */
    public static int shortestDistance(Graph g, Vertex v1, Vertex v2) {
        // ...
    }
}
```

## (Lack of) Modularity in ML

* Often no clear specification of "correct" behavior.
  * Optimizing metrics instead of providing guarantees.
* Model behavior strongly dependent on training & test sets.
  * What happens if distribution changes?
* Poorly understood interactions between models.
  * Ideally, develop models separately & compose together.
  * In general, must train & tune together.

## Concept Drifts

* ML estimates "f(x) = y"
  * What if the relationship between "x" & "y" changes over time? 
  * What if "f" does not capture certain relationships?

> Q: Examples?

* In general, impossible to predict.
	* Continuously monitor and update model.

## Feedback Loops

* Every system is deployed as part of an environment.
* Output influences the environment.
  * In turn, affects input back to the system.
  * Over time, may lead to undesirable (and difficult to reverse) outcome.
  * Higher risks if initial data set & model is biased.

![Feedback Loop](graphics/feedback-loop.png){title="Courtesy Eunsuk Kang."}

## Example: Crime Prediction

1. Use past data to predict crime rates.
1. Police increases the frequency of patrol in area $X$.
1. More arrested made in area $X$.
1. New crime data fed back to the model.
1. Repeat.

![Crime Map](graphics/crime-map.jpg){title="Courtesy Eunsuk Kang."}

## Discussion: Product Recommendations

![Product recommendations](graphics/recommendations.png){title="Courtesy Eunsuk Kang."}

1. Specification/metrics?
1. Concept drift?
1. Feedback loop?

## Discussion: Streaming Recommendations

![["How Does Amazon & Netflix Personalization Work?"](https://vwo.com/blog/deliver-personalized-recommendations-the-amazon-netflix-way){target="new"} by [Astha Khandelwal](https://vwo.com/blog/author/asthakhandelwal){target="new"}](graphics/netflix-homepage-1024x560.webp)

1. Specification/metrics?
1. Concept drift?
1. Feedback loop?

## Technical Debt

> "Machine learning: The high interest credit card of technical debt" -- [Sculley et al. 2014](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43146.pdf)

![](graphics/debt.jpg){title="Courtesy Eunsuk Kang."}

## Technical Debt

[![](graphics/debt.png){width=45%}](https://www.monkeyuser.com/2018/tech-debt/)

## The Notebook

> Jupyter Notebooks are a gift from God to those who work with data. They allow us to do quick experiments with Julia, Python, R, and more -- [John Paul Ada](https://towardsdatascience.com/no-hassle-machine-learning-experiments-with-azure-notebooks-e1a22e8782c3)

![](graphics/jupyter.png){title="Courtesy Eunsuk Kang." width=60%}

> Q: What are some benefits and drawbacks of Jupyter-style notebooks?

## Notebooks

### Pros

* Quick and easy exploration and experimentation.
* Literate programming intermixing text, code, and results.
* Small code snippets, heavy use of libraries.
* Blocks may execute independently (good or bad?).

### Cons

* Proof of concept on snapshot data only.
* Poor abstraction and testing practices.
* Low automation, often not scalable.
* Difficult transition in production.

### Questions

> Q: What may notebooks be good for (something we learned in this class!)?

## ML and Technical Debt 

* ML can seem like an easy addition, but it may cause long-term costs.
* Needs to be maintained, evolved, and debugged.
* Goals and environment may change; some changes are subtle.

### Example Problems

- Systems and models are tangled; changing one has *cascading* effects on the other.
- Untested, brittle infrastructure; manual deployment.
- Unstable data dependencies, replication crisis.
- Data drift and feedback loops.
- Magic constants and dead experimental code paths.

### Further Reading

Sculley, David, et al. [Hidden technical debt in machine learning systems](http://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems.pdf). Advances in Neural Information Processing Systems. 2015.

<!-- TODO: More on this! -->
