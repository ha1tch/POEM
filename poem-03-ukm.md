# 3. Unified Knowledge Model

## 3.1 Introduction

The development of Poesy's knowledge architecture emerges from a recurring observation that has appeared throughout the history of computing, information science, and cognitive science:

> The same knowledge often exists simultaneously in multiple representations.

A conversation may reference a document.

A document may describe an event.

An event may involve entities.

Entities may participate in relationships.

Relationships may form structures.

Structures may reveal patterns.

Patterns may eventually become concepts.

Human cognition appears remarkably adept at traversing these representations. We may remember a specific conversation, a general principle, a person, an analogy, or a causal chain, and move fluidly between them without consciously considering the underlying representation.

Most software systems, however, separate these forms of knowledge.

Databases store records.

Search engines store indexes.

Graphs store relationships.

Conversations store messages.

Documents store content.

Each system becomes its own island.

The Unified Knowledge Model represents an attempt to reduce these divisions.

Its purpose is not to eliminate specialized representations.

Rather, its purpose is to ensure that all representations participate in a common cognitive substrate.

---

# 3.2 Historical Background

## 3.2.1 The Persistent Fragmentation of Knowledge

Since the earliest information systems, knowledge has been fragmented according to implementation concerns.

The history of computing is largely a history of specialized storage systems:

### Filesystems

Organized around documents.

### Relational Databases

Organized around structured records.

### Search Engines

Organized around retrieval.

### Graph Databases

Organized around relationships.

### Knowledge Bases

Organized around facts.

### Communication Systems

Organized around messages.

Each representation solves a particular problem exceptionally well.

Yet each introduces a new boundary.

Human cognition rarely respects such boundaries.

When thinking about a person, we simultaneously access:

* memories
* relationships
* documents
* events
* abstractions
* emotions
* concepts

The divisions are computational rather than cognitive.

---

## 3.2.2 Semantic Networks

One of the earliest attempts to address this problem emerged in the form of semantic networks.

Researchers in the 1960s and 1970s proposed representing knowledge as interconnected concepts rather than isolated records.

Systems such as:

* Semantic Network
* Conceptual Graphs
* Frame Systems

sought to model knowledge through relationships.

Although many of these systems were constrained by the computational resources of their era, they introduced an important insight:

> Knowledge derives meaning not only from content, but from connections.

This principle remains foundational.

---

## 3.2.3 Hypertext and Associative Trails

The associative navigation tradition — Bush's Memex, Engelbart's augmentation work, Nelson's hypertext — was introduced in Chapter 1 and applies with equal force here. Knowledge exploration proceeds through association rather than linear search. The Unified Knowledge Model inherits this directly: traversal is as fundamental a capability as storage.

---

## 3.2.4 Knowledge Graphs

The rise of large-scale knowledge graphs represented another major milestone.

Examples include:

* DBpedia
* Wikidata
* Google Knowledge Graph

These systems demonstrated that explicit relationships could dramatically improve retrieval and discovery.

However, they also revealed limitations.

Knowledge graphs excel at representing structure.

They often struggle with:

* ambiguity
* narrative
* chronology
* evolving context

This limitation becomes particularly important when considering cognition.

Knowledge consists not only of facts and relationships but also of experiences and events.

---

# 3.3 Knowledge Objects

## 3.3.1 Fundamental Unit

The Unified Knowledge Model introduces the concept of the knowledge object.

A knowledge object is the primary cognitive unit within the system.

Examples include:

* Messages
* Conversations
* Documents
* Summaries
* Entities
* Events
* Graph nodes
* Search results
* Future cognitive artifacts

A knowledge object is not defined by its storage representation.

It is defined by its identity.

---

## 3.3.2 Stable Identity

A recurring challenge in complex systems is identity fragmentation.

The same concept often appears in multiple systems:

```text id="2d5xgq"
Database Row
Graph Node
Search Result
Summary Mention
Conversation Reference
```

Traditional architectures frequently treat these as distinct objects.

The Unified Knowledge Model treats them as projections of a common identity.

This distinction is profound.

It transforms retrieval from:

> locating text

into:

> locating knowledge.

---

## 3.3.3 Provenance

Every knowledge object should maintain provenance.

Provenance answers:

* Where did this originate?
* When was it created?
* How was it derived?
* What transformations occurred?

Historically provenance has often been neglected in AI systems.

Modern agent architectures increasingly recognize its importance.

Without provenance:

* reasoning becomes opaque
* audits become difficult
* trust becomes fragile

Poesy's architecture treats provenance as a first-class concern.

---

# 3.4 Multiple Representations

## 3.4.1 Representation Independence

One of the central principles of the Unified Knowledge Model is representation independence.

Knowledge should not be constrained by how it is viewed.

A single object may participate simultaneously in:

* Document representation
* Graph representation
* Search representation
* Summary representation
* Temporal representation

The underlying identity remains constant.

---

## 3.4.2 Documents

Documents provide:

* flexibility
* expressiveness
* extensibility

They are particularly useful for:

* unstructured information
* narrative information
* conversational information

Documents therefore remain one of the foundational representations.

---

## 3.4.3 Graphs

Graphs provide:

* relationships
* neighborhoods
* paths
* connectivity

Graphs answer questions that documents cannot answer efficiently.

Examples:

* How are these concepts connected?
* What lies nearby?
* What paths exist?

Graphs therefore function as the relational projection of knowledge.

---

## 3.4.4 Search Indexes

Search indexes provide:

* lexical access
* deterministic retrieval
* efficient discovery

Despite the rise of embeddings, full-text search remains one of the most effective retrieval mechanisms available.

Its transparency and predictability make it indispensable.

---

## 3.4.5 Temporal Structures

Conversations and events introduce chronology.

Chronology answers questions such as:

* What happened first?
* What led to this decision?
* How did understanding evolve?

Temporal structure is not naturally represented by documents or graphs.

It therefore constitutes its own cognitive projection.

---

# 3.5 Retrieval as Navigation

## 3.5.1 Traditional Retrieval

Classical retrieval systems typically follow:

```text id="wzjaj8"
Query
 ↓
Search
 ↓
Documents
```

This model remains useful.

However, it assumes that retrieval is fundamentally document-oriented.

---

## 3.5.2 Navigation-Oriented Retrieval

The Unified Knowledge Model adopts a broader perspective.

Retrieval becomes navigation.

Possible actions include:

* Search
* Fetch
* Expand
* Traverse
* Drill
* Follow
* Compare

The objective is not merely to find information.

The objective is to move through knowledge space.

---

## 3.5.3 State of the Art

Modern retrieval systems increasingly move in this direction.

Recent developments include:

* Agentic retrieval
* GraphRAG
* Knowledge graph augmentation
* Retrieval planning
* Multi-stage retrieval systems

The common theme is clear:

Retrieval is becoming an active cognitive process rather than a passive database operation.

Poesy's architecture is strongly aligned with this trend.

---

# 3.6 Knowledge Resolution

## 3.6.1 A Missing Dimension

Most information systems represent knowledge at a single scale.

A document is a document.

A graph node is a graph node.

A search result is a search result.

Human cognition appears to operate differently.

We can think simultaneously about:

* a civilisation
* a nation
* a city
* a street
* a building
* a room

Each represents the same reality at different scales.

The Unified Knowledge Model therefore introduces the concept of knowledge resolution.

---

## 3.6.2 Resolution Hierarchies

Knowledge may exist at multiple levels:

```text id="j2m3ud"
Overview
    ↓
Topics
    ↓
Entities
    ↓
Events
    ↓
Messages
```

Each level provides:

* reduced complexity
* increased abstraction

while preserving navigability toward deeper detail.

---

## 3.6.3 Compression and Resolution

Compression becomes more than storage optimization.

It becomes:

> generation of alternate resolutions.

This interpretation fundamentally changes the role of summaries.

Summaries are no longer merely shortened versions.

They become navigable layers within a knowledge hierarchy.

---

# 3.7 Toward Drill-Based Knowledge Navigation

The emergence of drill-based navigation follows naturally from the preceding principles.

If knowledge exists:

* at multiple resolutions
* across multiple representations
* with stable identities

then cognition should be able to move between these layers deliberately.

Rather than:

```text id="gndzkt"
Summary
or
Full Detail
```

the system can support:

```text id="vp9n8p"
Summary
 ↓
Expand
 ↓
Drill
 ↓
Expand
 ↓
Drill
 ↓
Raw Knowledge
```

This creates a fundamentally different relationship between memory and reasoning.

The model no longer consumes knowledge as a fixed context.

It navigates knowledge dynamically.

---

# 3.8 Toward a Cognitive Substrate

The ultimate significance of the Unified Knowledge Model is not technical.

It is conceptual.

Historically, AI systems have often been built around:

* models
* prompts
* datasets

The Unified Knowledge Model proposes a different center of gravity.

Knowledge becomes the substrate.

Reasoning becomes an activity performed within that substrate.

Search, graph traversal, summaries, chronology, documents, and future memory structures become complementary views of a common cognitive environment.

This environment forms the foundation upon which later concepts—multi-resolution memory, drill navigation, Focal Cognition, and Peripheral Cognition—will be built.

The Unified Knowledge Model therefore represents more than a storage strategy.

It represents the transition from information management toward cognitive architecture.
