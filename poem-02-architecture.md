# 2. Current Architecture

## 2.1 Introduction

Poesy's current architecture is the product of a gradual evolution rather than a single design effort.

Unlike many contemporary AI systems, which begin with language models and subsequently add memory, retrieval, and orchestration capabilities, Poesy emerged from a concern with persistence, continuity, and context management. As a result, many of its architectural characteristics developed in response to practical constraints rather than theoretical ambitions.

This distinction is significant.

Most agent frameworks are fundamentally execution-centric. They are concerned primarily with determining what action an agent should perform next.

Poesy is increasingly memory-centric. Its central concern is determining how knowledge should be represented, organized, retrieved, compressed, navigated, and governed over extended periods of time.

The current architecture therefore represents an intermediate stage between a traditional conversational runtime and a more comprehensive cognitive runtime.

Its components can be understood as layers within an emerging cognitive substrate.

---

# 2.2 Architectural Overview

At a high level, Poesy currently consists of four major domains:

```text
Model Layer
       ↑
Cognition Layer
       ↑
Knowledge Layer
       ↑
Storage Layer
```

Each layer serves a distinct purpose.

### Storage Layer

Responsible for durable persistence.

### Knowledge Layer

Responsible for representation and retrieval.

### Cognition Layer

Responsible for context construction, memory management, and future cognitive processes.

### Model Layer

Responsible for language-model execution.

This separation is deliberate.

The architecture seeks to avoid coupling knowledge representation to any specific model, provider, or reasoning strategy.

---

# 2.3 Storage Layer

## 2.3.1 Historical Perspective

Traditional software systems have often been divided between two competing philosophies.

### Record-Oriented Systems

Data is stored as mutable records.

State is represented by the latest value.

Examples include:

* Relational databases
* CRUD applications
* Enterprise information systems

---

### Event-Oriented Systems

Data is stored as a sequence of events.

Current state is derived from history.

Examples include:

* Event sourcing
* Transaction logs
* Distributed ledgers

Poesy's storage architecture increasingly aligns with the second tradition.

---

## 2.3.2 Append-Only Histories

One of the earliest architectural decisions within Poesy was the treatment of conversation history as an append-only ledger.

This design has several important consequences.

### Preservation of Provenance

Every statement remains attributable to its origin.

### Reconstruction

Historical state can be reconstructed.

### Auditability

Reasoning chains can be inspected retrospectively.

### Future Compatibility

New summarization and compression strategies can be applied without destroying source information.

This reflects an important architectural principle:

> Raw history should be preserved whenever practical.

Derived representations may evolve.

Historical facts should not.

---

## 2.3.3 Durable Cognitive State

The storage layer is not merely preserving messages.

It is preserving the material from which future cognition may be constructed.

This distinction becomes increasingly important as:

* Memory systems grow
* Knowledge graphs evolve
* Retrieval policies become more sophisticated
* Supervisory systems emerge

The storage layer functions as the foundation upon which all higher-order cognitive structures depend.

---

# 2.4 Session Layer

## 2.4.1 Sessions as Cognitive Containers

Traditional chat systems typically treat conversations as interaction records.

Poesy treats sessions differently.

A session represents a bounded cognitive environment.

It contains:

* Historical dialogue
* Contextual state
* Summaries
* Metadata
* Model configuration
* Future cognitive artifacts

This conception resembles certain ideas from distributed systems.

A session is not merely a conversation.

It is an execution context for cognition.

---

## 2.4.2 Model Specialization

Modern AI systems increasingly employ multiple models.

Different models possess different strengths.

Examples include:

* General reasoning
* Vision processing
* Summarization
* Code generation
* Classification

Poesy incorporates this principle directly into session management.

Rather than treating model selection as an implementation detail, the system recognizes that different cognitive tasks may require different cognitive tools.

This reflects broader industry trends toward model routing and mixture-of-experts architectures.

---

## 2.4.3 Context Construction

Perhaps the most important responsibility of the session layer is context construction.

A language model never sees:

* The database
* The graph
* The full history

It sees a projection.

Constructing that projection is one of the central responsibilities of the runtime.

This observation is critical.

The quality of cognition often depends less on model capability than on context construction.

Poesy therefore treats context assembly as a first-class architectural concern.

---

# 2.5 Knowledge Layer

## 2.5.1 From Storage to Knowledge

Storage preserves information.

Knowledge organizes information.

This distinction has deep roots in both information science and cognitive science.

A library may contain information.

Knowledge emerges from relationships.

The knowledge layer exists to transform stored information into navigable structures.

---

## 2.5.2 Document-Oriented Representation

The document model provides flexibility.

Documents naturally accommodate:

* Conversations
* Metadata
* Summaries
* External content
* Agent artifacts

Document-oriented storage has become increasingly common because cognition rarely conforms to rigid relational schemas.

Human knowledge is often irregular, evolving, and heterogeneous.

Documents provide a useful foundation for representing such information.

---

## 2.5.3 Full-Text Search

The introduction of full-text search is more significant than it may initially appear.

Historically, information retrieval research predates modern AI by decades.

The work of researchers such as:

* Gerard Salton
* Karen Spärck Jones

established many of the principles still used today.

Modern language-model systems often focus heavily on embeddings and semantic retrieval.

Yet deterministic lexical retrieval remains remarkably powerful.

Full-text search provides:

* Transparency
* Predictability
* Explainability
* Efficiency

For many tasks it remains an essential component of retrieval architecture.

---

## 2.5.4 Graph Representation

One of the most significant developments within the architecture is the emergence of a graph layer.

Graphs possess unique cognitive properties.

Unlike documents, they represent relationships directly.

Unlike vectors, they preserve explicit structure.

Unlike conversations, they are not constrained by chronology.

Historically, graph-based representations have appeared repeatedly in AI:

* Semantic networks
* Frame systems
* Knowledge graphs
* Concept maps

The persistence of these ideas suggests that relational structure is fundamental to intelligent systems.

---

## 2.5.5 Automatic Relationship Formation

A particularly important aspect of the architecture is the movement toward automatic relationship construction.

Rather than requiring separate graph ingestion pipelines, relationships emerge directly from stored knowledge objects.

This produces several benefits:

* Reduced duplication
* Reduced synchronization complexity
* Unified identity model
* Consistent provenance

Knowledge objects remain knowledge objects regardless of how they are viewed.

---

# 2.6 Query Layer

## 2.6.1 Historical Background

Throughout computing history, one recurring theme appears repeatedly:

Users do not wish to manipulate storage.

They wish to express intent.

This principle motivated:

* SQL
* Graph query languages
* Search engines
* Declarative programming

The query layer continues this tradition.

---

## 2.6.2 OQL and Structured Retrieval

Structured query systems provide capabilities that embeddings cannot.

They allow:

* Deterministic filtering
* Exact constraints
* Complex joins
* Explicit reasoning over structure

Modern AI systems increasingly combine:

* Semantic retrieval
* Structured retrieval
* Graph traversal

Poesy's architecture reflects this trend.

The future of retrieval is unlikely to be purely vector-based.

It will almost certainly involve multiple complementary retrieval modalities.

---

## 2.6.3 Path Discovery

Path discovery represents one of the most cognitively interesting capabilities of graph systems.

It enables questions such as:

* How are these concepts connected?
* What intermediate relationships exist?
* What causal chains are present?

These capabilities support forms of reasoning that are difficult to reproduce through document retrieval alone.

---

# 2.7 Compression and Context Management

## 2.7.1 The Context Window Constraint

Every AI system operates under resource constraints.

Historically these constraints have evolved:

* Memory limits
* Storage limits
* Processing limits
* Context limits

The modern equivalent is the context window.

No matter how large context windows become, attention remains finite.

This observation motivates compression.

---

## 2.7.2 Compression as Infrastructure

Many systems treat summarization as a convenience feature.

Poesy increasingly treats compression as infrastructure.

Compression serves multiple purposes:

### Scalability

Allows cognition to extend beyond context limits.

### Abstraction

Creates higher-level representations.

### Navigation

Enables movement between levels of detail.

### Attention Allocation

Reduces cognitive load.

---

## 2.7.3 Preservation of Ground Truth

A critical principle is maintained throughout the architecture:

Compression is not authority.

Compression is interpretation.

The authoritative source remains:

* Original messages
* Original documents
* Original events

This distinction preserves auditability and reduces the risk of cumulative summarization drift.

---

# 2.8 Toward a Unified Knowledge Substrate

The current architecture can be understood as a gradual convergence.

Historically, information systems have separated:

* Databases
* Search engines
* Knowledge graphs
* Conversations
* Memory systems

Poesy increasingly seeks to unify these domains.

A knowledge object may simultaneously participate in:

* Storage
* Search
* Graph traversal
* Summarization
* Retrieval
* Future cognitive processes

The system therefore moves away from isolated data silos and toward a shared cognitive substrate.

---

# 2.9 Current Position

The architecture described in this chapter is not a proposal. The foundational layers — persistent storage, session management, knowledge representation, graph-backed relationships, structured retrieval, and full-text search — exist and operate. They are the substrate upon which the cognitive layers described in subsequent chapters will be constructed.

What does not yet exist, except as design, is the cognitive layer itself: focal cognition, peripheral cognition, governance, and retrieval policy. These are POEM destinations. The infrastructure beneath them is not aspirational. The cognition atop them is.

This distinction matters for how subsequent chapters should be read. The architecture described from chapter 3 onward is the target state of a POEM-class system. Poesy moves toward it from a position of already having the substrate. The distance is real. So is the foundation.
