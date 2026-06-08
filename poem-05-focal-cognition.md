# 5. Focal Cognition

## 5.1 Introduction

The preceding sections introduced two foundational ideas.

The first was the concept of a Unified Knowledge Model, in which information exists as a navigable cognitive substrate rather than as isolated documents, messages, or database records.

The second was Multi-Resolution Memory, which allows knowledge to exist simultaneously at multiple levels of abstraction and detail.

These concepts define the environment within which cognition operates.

However, they do not yet explain cognition itself.

A landscape may exist.

A map may exist.

A memory hierarchy may exist.

Yet none of these explain how attention moves through that environment.

This section introduces the concept of **Focal Cognition**.

Focal Cognition refers to the active process of directed reasoning operating within the cognitive substrate.

It is the mechanism by which attention selects goals, explores knowledge, drills into detail, evaluates evidence, and ultimately produces decisions.

If Multi-Resolution Memory defines the terrain, Focal Cognition defines the traveler.

---

# 5.2 Historical Background

## 5.2.1 The History of Attention

One of the most striking features of both human and machine intelligence is that cognition appears fundamentally constrained by attention.

Information abundance is not intelligence.

The ability to determine what deserves attention appears considerably more important.

Throughout the twentieth century, cognitive scientists increasingly shifted their focus from memory alone toward attentional mechanisms.

Researchers such as:

* William James
* Donald Broadbent
* Daniel Kahneman

recognized that intelligent behavior depends not merely on possessing information but on selectively processing information.

William James famously described attention as:

> "the taking possession by the mind... of one out of what seem several simultaneously possible objects or trains of thought."

This observation remains remarkably relevant.

Modern AI systems frequently possess access to enormous quantities of information.

The challenge increasingly becomes selecting which information deserves immediate cognitive resources.

---

## 5.2.2 Working Memory

Modern cognitive science often distinguishes between:

### Long-Term Memory

Knowledge accumulated over time.

### Working Memory

Knowledge actively participating in current thought.

This distinction appears repeatedly throughout cognition research.

Humans do not reason using everything they know.

They reason using a dynamically selected subset of what they know.

Language models exhibit similar constraints.

Even with large context windows, reasoning occurs over a bounded working set.

The architecture of Poesy adopts this distinction directly.

The Unified Knowledge Model represents long-term cognitive substrate.

Focal Cognition represents the active working process operating over selected portions of that substrate.

---

## 5.2.3 Executive Function

The notion of an executive process — a higher-level mechanism that coordinates and directs lower-level cognitive operations — appears repeatedly throughout theories of cognition.

The most architecturally relevant formulation is Global Workspace Theory, developed by Bernard Baars and later extended by Stanislas Dehaene. The theory proposes that the brain contains many specialized, largely independent processes operating in parallel. Most of this activity remains local and unconscious. What we experience as focused thought occurs when one process — or a coalition of processes — succeeds in broadcasting its content to a shared global workspace, making it available to the system as a whole.

The significance for machine cognition is not the neuroscience. It is the architectural implication: attention is not a property of information. It is an achievement of selection. The question is never simply what information exists, but which information gains access to the workspace where reasoning occurs.

Focal Cognition is the runtime expression of this idea. The knowledge substrate may contain vast amounts of relevant material. What enters working memory — what gets broadcast into the focal workspace — is determined by attentional selection, not by storage.

This is a fundamentally different question from the one that most retrieval systems answer.

> How should a cognitive system allocate attention among many possible directions of thought?

That question is as open in machine cognition today as it was in cognitive science fifty years ago. Focal Cognition is Poesy's attempt to make it an explicit architectural concern rather than an implicit consequence of prompt assembly.

---

# 5.3 Defining Focal Cognition

## 5.3.1 Definition

Focal Cognition is the primary reasoning process currently responsible for pursuing a goal.

At any moment, the system may possess:

* many memories
* many documents
* many relationships
* many opportunities

Yet only a small subset participates directly in active reasoning.

The process operating over that subset constitutes Focal Cognition.

---

## 5.3.2 Characteristics

Focal Cognition possesses several defining properties.

### Goal-Oriented

It is attempting to achieve something.

Examples:

* answer a question
* investigate a topic
* solve a problem
* plan an action

---

### Resource Intensive

It consumes the majority of available reasoning resources.

---

### Context-Bounded

It operates over an assembled working memory.

---

### Decision-Making Authority

It owns conclusions.

Peripheral processes may advise.

Focal Cognition decides.

---

## 5.3.3 The Cognitive Spotlight

An intuitive metaphor is the spotlight.

Imagine an enormous landscape of knowledge.

Only a small region is illuminated at any moment.

```text
Knowledge Landscape

██████████████████████
███████◉██████████████
██████████████████████
```

The illuminated region represents current attention.

Everything else remains available but inactive.

Focal Cognition determines where the spotlight points.

---

# 5.4 From Queries to Goals

## 5.4.1 Traditional Information Systems

Classical information systems are query-centric.

The process is straightforward:

```text
Question
 ↓
Search
 ↓
Answer
```

This model works well for bounded tasks.

However, many cognitive tasks are not query-oriented.

Examples:

* investigations
* research
* planning
* discovery
* diagnosis

These activities evolve dynamically.

The destination may be unknown at the outset.

---

## 5.4.2 Goal-Oriented Cognition

Focal Cognition therefore operates around goals rather than queries.

Examples:

```text
Understand this project
```

```text
Determine why this failure occurred
```

```text
Develop a strategy
```

```text
Investigate this anomaly
```

The goal defines direction.

The path emerges through exploration.

---

# 5.5 Drill-Based Reasoning

## 5.5.1 Motivation

Traditional retrieval systems retrieve documents.

Focal Cognition navigates knowledge.

This distinction becomes especially important in large cognitive environments.

The challenge is not merely locating information.

The challenge is deciding where to descend into greater detail.

---

## 5.5.2 Drill as a Cognitive Primitive

Within Poesy, drill becomes a first-class cognitive operation.

Example:

```text
Project
 ↓
Subsystem
 ↓
Component
 ↓
Issue
 ↓
Evidence
```

Each step narrows focus.

Each step increases detail.

Each step consumes attentional resources.

Drill therefore serves as a mechanism for controlled attention allocation.

---

## 5.5.3 Progressive Refinement

Drill-based cognition closely resembles certain forms of human inquiry.

Investigations often proceed through:

```text
General Observation
 ↓
Hypothesis
 ↓
Focused Investigation
 ↓
Evidence Collection
 ↓
Conclusion
```

The process naturally traverses multiple levels of abstraction.

---

# 5.6 Working Memory Construction

## 5.6.1 The Context Assembly Problem

Language models never reason directly over databases.

They reason over assembled context.

This creates a fundamental architectural question:

> What should enter working memory?

The answer determines reasoning quality.

---

## 5.6.2 Sources of Working Memory

Working memory may be assembled from:

### Session History

Relevant prior interactions.

### Knowledge Objects

Documents and entities.

### Graph Neighborhoods

Related concepts.

### Search Results

Lexical retrieval.

### External Sources

Web information.

### Previous Cognitive Artifacts

Summaries and analyses.

---

## 5.6.3 Dynamic Context

Working memory should not be static.

As drilling proceeds:

```text
Topic
 ↓
New Information
 ↓
Updated Context
 ↓
Further Reasoning
```

Context evolves alongside cognition.

---

# 5.7 State of the Art

## 5.7.1 Agentic Systems

Modern AI increasingly employs agentic architectures.

Examples include:

* planner-executor systems
* research assistants
* autonomous workflows
* tool-using agents

These systems generally recognize that reasoning is not a single inference step.

It is a sequence of decisions.

---

## 5.7.2 ReAct and Tool Use

One influential development was the emergence of reasoning-and-acting paradigms.

The central insight was simple:

Reasoning can determine actions.

Actions can acquire information.

Information can improve reasoning.

This creates a feedback loop.

Modern tool-using systems increasingly rely upon this pattern.

---

## 5.7.3 Retrieval Planning

Recent post-RAG systems increasingly employ:

* retrieval policies
* search planning
* graph exploration
* multi-stage retrieval

The emerging trend is clear.

The important decision is often not:

> What is the answer?

but:

> What should I investigate next?

This is fundamentally a focal cognition problem.

---

# 5.8 Focal Cognition as Navigation

## 5.8.1 Beyond Inference

Many discussions of AI focus exclusively on inference.

Inference is important.

However, in large cognitive environments, navigation may become equally important.

The system must determine:

* where to look
* what to retrieve
* what to ignore
* what to investigate further

Navigation becomes cognition.

---

## 5.8.2 Cognitive Trajectories

Reasoning can be viewed as a trajectory through knowledge space.

Example:

```text
Question
 ↓
Topic
 ↓
Entity
 ↓
Event
 ↓
Document
 ↓
Evidence
 ↓
Conclusion
```

The path itself becomes meaningful.

It reflects how understanding was constructed.

---

## 5.8.3 Traceability

Because focal cognition proceeds through identifiable navigation steps, the process becomes inspectable.

The system can answer:

* Why was this conclusion reached?
* What evidence was consulted?
* What path was followed?

This provides significant advantages over opaque reasoning processes.

---

# 5.9 Limitations of Purely Focal Systems

Despite its strengths, focal cognition possesses a fundamental weakness.

Attention is selective.

Selection implies exclusion.

Whenever the system focuses on one region of knowledge, it necessarily ignores others.

This creates risks:

### Tunnel Vision

Important evidence may be overlooked.

### Confirmation Bias

Supporting information may dominate contradictory information.

### Missed Opportunities

Relevant connections may remain unexplored.

### Context Loss

Peripheral knowledge may disappear from consideration.

These limitations are not unique to machines.

They are universal consequences of attention.

---

# 5.10 The Need for Peripheral Awareness

Historically, many cognitive architectures have struggled with this problem.

The challenge is clear:

How can a system remain focused without becoming blind?

How can it pursue a goal without ignoring potentially important neighboring information?

How can attention remain concentrated while still preserving awareness?

The next stage of Poesy's evolution emerges directly from these questions.

If Focal Cognition represents the cognitive spotlight, then another mechanism is required to observe the regions beyond that spotlight.

This motivates the introduction of **Peripheral Cognition**.

Peripheral Cognition extends the architecture beyond simple goal pursuit toward a richer model of awareness, where exploration occurs not only along the current path of reasoning but also around it.

The resulting system seeks to balance two competing requirements:

* focus
* awareness

A mature cognitive architecture requires both.

Focal Cognition provides the former.

Peripheral Cognition will provide the latter.
