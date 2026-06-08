# 0. Prologue

Poesy did not begin as an attempt to build an agent framework.

It began with a simpler problem: how to maintain meaningful conversations with language models over time while operating within finite context windows, finite computational resources, and imperfect memory. Early versions focused on session management, persistent storage, context reconstruction, model abstraction, and summarization. The objective was practical: preserve continuity without sacrificing efficiency.

As the system evolved, an observation became increasingly difficult to ignore.

Most contemporary AI systems treat cognition as transient. A prompt is assembled, a model is invoked, and the resulting response is produced in relative isolation. Memory, when present, is often implemented as an afterthought: a vector store, a retrieval layer, or a collection of summaries attached to an otherwise stateless process.

Yet human reasoning does not appear to function this way.

Human cognition is persistent. It is layered. It operates across multiple levels of abstraction simultaneously. It maintains both detailed episodic memories and abstract semantic understanding. It revisits previous experiences, forms connections between seemingly unrelated concepts, notices inconsistencies, and continuously reallocates attention between focal concerns and peripheral observations.

The further Poesy developed, the more it became apparent that the central challenge was not model invocation, but cognition management.

This realization motivated a gradual shift in architectural focus.

Rather than treating memory as a support system for reasoning, Poesy increasingly treats reasoning as an activity performed within a structured memory environment. Conversation history, summaries, knowledge graphs, search indexes, documents, and external information sources are viewed as different projections of a larger knowledge substrate. The role of the runtime is to navigate, organize, and govern these representations while providing models with the information necessary to reason effectively.

This perspective naturally leads to several questions.

How should long-lived machine cognition be represented?

How should knowledge be compressed without losing fidelity?

How should agents navigate memory structures that may span millions of events and relationships?

How should systems distinguish between what is currently important and what may become important?

How can reasoning remain focused while still retaining awareness of its surroundings?

The concepts explored in this roadmap emerge from those questions.

Multi-resolution memory, drill-based knowledge navigation, structured retrieval, graph representations, supervisory agents, and retrieval policy layers are not independent features. They are components of a broader effort to create a runtime capable of supporting persistent, inspectable, and governable cognition.

The next stage of this evolution introduces two complementary ideas.

**Focal Cognition** represents the active reasoning process: the thread of thought currently pursuing a goal, exploring a problem, or making a decision.

**Peripheral Cognition** represents a surrounding layer of awareness: specialized processes that explore neighboring regions of memory, search for contradictions, discover analogies, monitor external information, and identify opportunities that the focal process may have overlooked.

Together, these concepts move Poesy beyond the traditional boundaries of chat systems, retrieval systems, and agent frameworks. They point toward a different objective: the development of a cognitive runtime in which memory, attention, retrieval, and reasoning operate as coordinated components of a larger system.

The work described in this document should therefore be viewed not as a product roadmap in the conventional sense, but as an exploration of machine cognition as a systems problem.

This document is the specification of that exploration. It defines **POEM**: a conceptual framework describing what a persistent cognitive runtime is, what properties it must possess, and what design principles it must respect. POEM describes a class of systems. It does not describe a single implementation.

**Poesy** is the first concrete attempt to build a POEM-class system. It is the implementation against which these principles are tested, refined, and grounded. Where POEM asks what such a system must be, Poesy asks what it takes to build one. The two evolve together, but they are not the same thing. POEM should remain stable as Poesy changes. When Poesy forces a revision to a principle, that revision reflects genuine learning about the class, not merely an implementation convenience.

Readers encountering Poesy's current state should therefore understand that any gap between the architecture described here and the implementation at hand is not a failure. It is the frontier.

A note on how to read what follows.

POEM is a category and a destination. It describes what a persistent cognitive runtime must be, what properties it must possess, and what design principles it must respect. Poesy is the ongoing work of building toward that destination — discovering which parts of the architecture are already sound, which require extension, and which remain genuinely open problems.

The chapters that follow are written at the level of POEM. They describe the full architecture of a persistent cognitive runtime as it should eventually exist. Where Poesy already implements a described capability, the implementation validates the principle. Where it does not yet, the principle describes the target. The document does not distinguish these cases in detail, partly because that boundary is actively moving, and partly because revealing the precise current state of Poesy would be premature. What can be said is that the foundational layers — storage, sessions, knowledge representation, and structured retrieval — are substantially further along than a first reading of this document might suggest. The cognitive layers — focal cognition, peripheral cognition, governance, and retrieval policy — remain destinations.

Readers should therefore treat the architecture as a coherent whole, while understanding that Poesy's relationship to it is that of an ongoing implementation, not a completed one. Any gap between what is described here and what Poesy does today is not a failure. It is the work.

The destination remains uncertain. Many of the ideas presented here are experimental and may evolve substantially as implementation and experience reveal new constraints and opportunities.

What is certain is the direction.

Poesy is evolving from a conversation manager into a platform for persistent cognition, where memory is structured, attention is deliberate, knowledge is navigable, and reasoning is only one component of a broader cognitive process.
