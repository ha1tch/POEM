# 8. Retrieval Policy Layer

## 8.1 Introduction

Throughout the history of computing, information retrieval has often been treated as a technical problem.

How should information be indexed?

How should queries be executed?

How should ranking be performed?

How should documents be retrieved?

These questions remain important.

However, as cognitive systems evolve, a deeper question emerges:

> How does a cognitive system decide what information to seek in the first place?

This question fundamentally differs from traditional retrieval concerns.

Classical retrieval assumes that a user has already determined what information is needed.

A search engine receives a query.

A database receives a request.

A retrieval mechanism executes an instruction.

The cognitive system itself remains passive.

Poesy's architecture increasingly challenges this assumption.

As cognition becomes:

* persistent
* exploratory
* goal-directed
* memory-rich
* graph-aware

retrieval ceases to be a passive operation.

It becomes an active cognitive decision.

This section introduces the concept of the Retrieval Policy Layer.

The Retrieval Policy Layer is responsible for determining:

* when to retrieve
* what retrieval method to use
* how deeply to explore
* how much evidence to gather
* when to stop gathering information

In many respects, it serves as the bridge between cognition and knowledge.

If memory is the terrain, and focal cognition is the traveler, retrieval policy determines the route.

---

# 8.2 Historical Background

## 8.2.1 Classical Information Retrieval

The field of Information Retrieval emerged long before modern AI.

Researchers such as:

* Gerard Salton
* Karen Spärck Jones

developed many of the concepts still used today:

* indexing
* ranking
* relevance
* term weighting
* retrieval evaluation

Classical retrieval systems generally followed a simple model:

```text
Need
 ↓
Query
 ↓
Retrieval
 ↓
Results
```

The human supplied intent.

The system supplied information.

---

## 8.2.2 Search as an External Activity

Historically, search has occupied a peculiar role in computing.

Search is often treated as something performed by a user.

The system itself remains unaware of:

* why the search occurred
* what larger objective exists
* whether the search succeeded

Search is procedural.

Not cognitive.

This distinction remained largely unchallenged for decades.

---

## 8.2.3 Expert Systems

Expert systems introduced a subtle shift.

Systems such as:

* MYCIN
* DENDRAL

began selecting which rules to evaluate.

Retrieval became partially internalized.

The system determined:

* what information was needed
* which inference chain to follow

However, these systems remained constrained by predefined rule structures.

---

## 8.2.4 The Rise of Search Engines

The web transformed retrieval.

Search became:

* large scale
* dynamic
* probabilistic

Systems increasingly focused on:

* ranking
* relevance estimation
* link structure
* authority signals

The retrieval problem expanded dramatically.

Yet retrieval still remained largely reactive.

---

# 8.3 The Retrieval Crisis of Modern AI

## 8.3.1 Language Models Changed Everything

Large language models introduced a new situation.

Models appeared capable of answering questions without retrieval.

For a brief period, many assumed retrieval might become unnecessary.

This assumption proved incorrect.

---

## 8.3.2 Knowledge Limitations

Model parameters possess important limitations:

* finite training cutoff
* imperfect recall
* hallucination risk
* inability to access private knowledge

These limitations naturally revived interest in retrieval.

---

## 8.3.3 The Rise of RAG

Retrieval-Augmented Generation emerged as a practical solution.

Classical RAG follows:

```text
Question
 ↓
Embedding Search
 ↓
Retrieved Chunks
 ↓
Prompt
 ↓
Answer
```

This architecture represented a major breakthrough.

However, it also introduced new problems.

---

## 8.3.4 The Retrieval Bottleneck

Modern systems increasingly discover that retrieval itself becomes the bottleneck.

Questions include:

* Which retrieval strategy?
* How many documents?
* Which sources?
* What level of detail?
* How much confidence?

The challenge is no longer retrieval.

The challenge is retrieval policy.

---

# 8.4 Retrieval as a Cognitive Decision

## 8.4.1 A Shift in Perspective

The Retrieval Policy Layer adopts a fundamentally different perspective.

Retrieval is not a database operation.

Retrieval is a cognitive action.

Just as humans decide:

* whether to consult a book
* whether to ask a colleague
* whether to revisit notes

machine cognition must decide:

* whether to search
* whether to drill
* whether to fetch
* whether to explore

Retrieval becomes part of reasoning.

---

## 8.4.2 Information-Seeking Behavior

Information science has long studied information-seeking behavior.

Researchers observed that humans do not retrieve information uniformly.

People choose different strategies depending on:

* uncertainty
* familiarity
* urgency
* confidence

This insight translates naturally into cognitive systems.

Different situations require different retrieval behaviors.

---

# 8.5 Retrieval Modalities

## 8.5.1 Internal Memory

The lowest-cost retrieval source is existing memory.

Questions include:

* Have we seen this before?
* Does relevant context already exist?

Internal memory should generally be consulted first.

---

## 8.5.2 Full-Text Search

Lexical search remains one of the most powerful retrieval tools available.

Advantages:

* deterministic
* transparent
* efficient
* explainable

Particularly useful when exact terminology matters.

---

## 8.5.3 Graph Retrieval

Graph retrieval supports:

* relationship discovery
* path finding
* neighborhood exploration

Graph retrieval excels when structure matters.

Questions such as:

> What is connected?

cannot be answered effectively through search alone.

---

## 8.5.4 Drill Retrieval

Drill retrieval represents one of Poesy's distinctive contributions.

The objective is not:

> Find another document.

The objective is:

> Increase resolution.

Example:

```text
Project
 ↓
Subsystem
 ↓
Component
 ↓
Issue
```

The retrieval action changes cognitive scale rather than cognitive location.

---

## 8.5.5 External Retrieval

External retrieval introduces:

* web search
* APIs
* external databases
* real-time information

External retrieval extends cognition beyond local memory.

---

## 8.5.6 Future Semantic Retrieval

Vector retrieval remains useful.

However, within Poesy's architecture it becomes one retrieval modality among many rather than the foundation of all retrieval.

This distinction reflects a broader post-RAG trend.

---

# 8.6 Retrieval Policies

## 8.6.1 What Is a Retrieval Policy?

A retrieval policy defines:

> Under what conditions should a particular retrieval strategy be employed?

Policies convert retrieval from mechanism into behavior.

---

## 8.6.2 Confidence-Based Policies

Example:

```text
High Confidence
 ↓
No Retrieval

Low Confidence
 ↓
Search
```

This resembles human behavior.

We verify information when uncertainty increases.

---

## 8.6.3 Novelty-Based Policies

Example:

```text
Known Topic
 ↓
Memory

Unknown Topic
 ↓
External Search
```

---

## 8.6.4 Contradiction Policies

Example:

```text
Conflicting Evidence
 ↓
Additional Investigation
```

These policies integrate naturally with Peripheral Cognition.

---

## 8.6.5 Resolution Policies

Example:

```text
Need Detail
 ↓
Drill

Need Overview
 ↓
Summaries
```

This becomes especially important within multi-resolution memory systems.

---

# 8.7 Retrieval Planning

## 8.7.1 Multi-Step Retrieval

Many tasks require multiple retrieval operations.

Example:

```text
Question
 ↓
Search
 ↓
Entity
 ↓
Graph
 ↓
Related Event
 ↓
Drill
 ↓
Evidence
```

The retrieval sequence itself becomes meaningful.

---

## 8.7.2 Retrieval Plans

Future versions of Poesy may generate explicit retrieval plans.

Examples:

```text
1. Search
2. Fetch
3. Graph Expansion
4. Drill
5. Verify
```

This improves:

* traceability
* reproducibility
* governance

---

## 8.7.3 Retrieval as Exploration

The concept of retrieval planning naturally converges with exploration.

The system increasingly behaves less like a search engine and more like an investigator.

---

# 8.8 State of the Art

## 8.8.1 Agentic Retrieval

One of the strongest trends in modern AI is agentic retrieval.

Systems increasingly determine:

* what information to acquire
* when to acquire it
* how to validate it

rather than relying on fixed pipelines.

---

## 8.8.2 GraphRAG

Recent GraphRAG systems combine:

* graph structures
* retrieval
* summarization

These architectures recognize that relationships often matter as much as content.

Poesy's graph layer aligns naturally with this trend.

---

## 8.8.3 Retrieval Planning Systems

Research increasingly explores:

* retrieval agents
* planner-retriever architectures
* multi-stage search systems

The common theme is clear:

Retrieval is becoming strategic.

---

## 8.8.4 Post-RAG Architectures

The emerging state of the art increasingly resembles:

```text
Goal
 ↓
Reasoning
 ↓
Retrieval Decision
 ↓
Information Acquisition
 ↓
Reasoning
 ↓
Further Retrieval
```

rather than:

```text
Retrieve Once
 ↓
Answer
```

This evolution strongly validates the architectural direction of Poesy.

---

# 8.9 Retrieval Policy and Peripheral Cognition

A particularly interesting interaction emerges between retrieval policy and Peripheral Cognition.

Peripheral agents may act as retrieval advisors.

Examples:

### Contradiction Scout

Suggests:

```text
Retrieve conflicting evidence
```

### Historical Scout

Suggests:

```text
Retrieve analogous episodes
```

### Graph Scout

Suggests:

```text
Expand neighborhood
```

This creates a feedback loop between awareness and information acquisition.

---

# 8.10 Retrieval Policy as Cognitive Strategy

At a deeper level, retrieval policy may become one of the defining characteristics of machine cognition.

Different retrieval policies produce different cognitive personalities.

Examples:

### Conservative Cognition

Retrieves sparingly.

### Investigative Cognition

Retrieves aggressively.

### Skeptical Cognition

Prioritizes contradiction searches.

### Exploratory Cognition

Prioritizes neighborhood expansion.

This observation suggests that retrieval policy may become as important as model selection itself.

---

# 8.11 Toward Deliberate Information Acquisition

The evolution of retrieval mirrors a broader evolution occurring throughout AI.

Early systems focused on:

* storing information

Later systems focused on:

* retrieving information

Modern systems increasingly focus on:

* deciding how information should be acquired

The Retrieval Policy Layer embodies this transition.

It transforms retrieval from an implementation detail into an explicit cognitive capability.

The system no longer merely possesses knowledge.

It develops strategies for obtaining knowledge.

---

# 8.12 Toward Cognitive Agency

With the introduction of Retrieval Policy Layers, the major components of the Poesy cognitive architecture now begin to form a coherent whole.

The architecture possesses:

* a unified knowledge substrate
* multi-resolution memory
* focal cognition
* peripheral cognition
* governance mechanisms
* retrieval strategies

Each component addresses a distinct aspect of cognition:

* Memory provides continuity.
* Knowledge provides structure.
* Focal Cognition provides direction.
* Peripheral Cognition provides awareness.
* Governance provides stability.
* Retrieval Policy provides information acquisition.

Taken together, these systems move Poesy beyond the traditional boundaries of chat systems, retrieval systems, and agent frameworks.

They establish the foundations for a cognitive runtime capable not merely of responding, but of navigating, exploring, learning, and managing knowledge across time.

The remaining sections of this roadmap will examine the future research directions that emerge from this foundation and the long-term destination toward which the architecture is evolving.
