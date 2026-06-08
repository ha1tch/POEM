# What a Cognitive Runtime Must Be

**A primer, and condensed companion to the POEM texts**

*Version 0.0.6 · 2026-06-07*

---

## Preface

What follows is a compressed account of the ideas developed at length in the POEM specification — the Persistent Operative-cognitive Environment Model — and in the architectural documentation of Poesy, its first implementation. The full texts run to roughly 28,000 words across fifteen chapters and three appendices. This companion covers the same ground in approximately 8,000.

Nothing has been simplified. Some things have been condensed past the point where the evidence is visible. Where the full texts show their working, this document states their conclusions. Where the full texts trace historical lineage across paragraphs, this document names the lineage and moves on. Readers who want the argument in full should read the full texts. Readers who want to understand the shape of the argument first, or who want a single document they can hold in mind, should read this.

POEM is a framework. Poesy is an implementation. The two are not the same thing and should not be treated as the same thing. POEM describes what a persistent cognitive runtime must be. Poesy is the ongoing work of building toward that description. The gap between them is real. It is also the work.

---

## I. The Assumption That Dominates

Most contemporary AI systems are built on an assumption so pervasive it rarely gets named.

The assumption is this: reasoning is primary, and everything else — memory, retrieval, coordination, persistence — is infrastructure that supports reasoning.

This assumption shapes everything. It means that memory systems get designed as attachments rather than substrates. Retrieval gets designed as a pipeline that precedes reasoning rather than a process that is part of reasoning. Coordination between components gets designed as plumbing rather than as cognitive architecture. The model — the reasoning engine — occupies the centre, and everything else orbits it.

The assumption is not wrong in a narrow technical sense. Models do reason. Retrieval does precede inference in any given call. These are facts.

But they are facts about individual operations, not about cognition. And the conflation of individual operations with cognition is precisely where the assumption fails.

Consider what programs actually do when they fail. They fail at the boundaries — between components, between memory systems, between the moment when information was acquired and the moment it needs to be applied. They fail because retrieval returned the wrong thing, or nothing, or something stale. They fail because context collapsed. They fail because what one part of the system knew, another part could not access. They fail because time passed and the system had no way to track what that meant.

These failures are not model failures. They are infrastructure failures. Better reasoning inside a deficient cognitive infrastructure produces better answers to the wrong questions at the wrong time with the wrong information.

The POEM framework begins from the opposite assumption: that cognition is a systems problem, and that the infrastructure within which reasoning occurs determines — more than the reasoning itself — what the system can actually do over time.

This is not a claim that models do not matter. It is a claim that the dominant way of thinking about AI has systematically underinvested in the substrate within which models operate, because that substrate was assumed to be secondary.

The assumption that reasoning is primary has been held without examination for long enough that it shapes what questions get asked, what problems get prioritised, and what solutions get built. The POEM framework asks: what if it is false? What would you build differently if cognition — real cognition, the kind that persists and evolves and governs itself — were primarily a property of infrastructure rather than of models?

That question is not rhetorical. What you build differently is the subject of everything that follows.

---

## II. The Ground

Before there is cognition, there is substrate. Before there is reasoning, there is something to reason within.

In Poesy, the substrate is the Unified Knowledge Model — a cognitive environment in which information exists simultaneously as conversation history, as graph relationships, as document content, as search indexes, as temporal records. These are not separate systems that happen to coexist. They are different perspectives on a single underlying reality.

This matters because the dominant pattern in software history has been fragmentation. Databases store records. Search engines store indexes. Knowledge graphs store relationships. Conversation systems store messages. Documents store content. Each system becomes its own island, optimised for its own access patterns, expressing its own data model, incompatible by default with every other.

Human cognition does not fragment this way. When you think about a person, you simultaneously access memories, relationships, events, abstractions, and context — and you move between these representations without noticing the transition, because there is no transition. They are all the same knowledge, viewed from different angles.

The Unified Knowledge Model attempts to make this true of a machine cognitive system. A knowledge object — a message, a document, an entity, an event, a summary — has a stable identity that persists across all its representations. It is not a database record that also appears as a graph node and also gets indexed for search. It is a cognitive object that participates in database semantics, graph semantics, and search semantics simultaneously. The object is not the record. The record is one projection of the object.

This distinction transforms what retrieval means. In a fragmented system, retrieval means finding text — locating documents or records that match a query. In a unified substrate, retrieval means navigating knowledge — moving through a space of connected objects with stable identities, each of which can be approached from multiple directions depending on what the current cognitive task requires.

Navigation is not retrieval with better branding. It is a different activity. Retrieval answers: what documents are relevant? Navigation answers: where in the knowledge space should attention move next? The first question assumes a static landscape being queried from outside. The second assumes a cognitive agent moving through a landscape, making decisions about direction at each step.

The graph layer — the representation of knowledge as a network of entities connected by typed relationships — is what makes navigation possible rather than merely metaphorical. Documents can be searched but not navigated in any meaningful sense. A document either matches a query or it does not. Graphs have structure: neighborhoods, paths, clusters, distances. Two entities that are three relationship-hops apart may be cognitively closer than two entities that share a keyword, if the intervening relationships are semantically significant. Path discovery — finding how two concepts are connected, what intermediate relationships exist, what causal chains run between them — enables forms of reasoning that document retrieval cannot approach.

The automatic formation of relationships from stored knowledge objects, rather than through a separate ingestion pipeline, is a design decision with large practical consequences. In systems where knowledge representation and knowledge storage are separate concerns, they drift apart. The representation falls out of sync with the actual content. The graph becomes a layer of declared relationships that no longer accurately reflect the knowledge the system actually has. In a unified substrate, relationships emerge directly from stored knowledge objects and update as those objects evolve. The graph does not describe what the system knows. It is what the system knows, in relational form.

The distinction between querying and navigating runs through the entire POEM architecture. It is not ornamental. It is the reason the architecture looks the way it does.

Alongside the unified substrate, Poesy introduces provenance as a first-class architectural concern. Every knowledge object carries its origin, its derivation history, its transformation record. This is not bookkeeping. In a system that persists across time, that accumulates summaries of summaries, that builds abstractions over prior abstractions, provenance is the mechanism by which the ground truth remains recoverable. Without it, the cognitive system loses the ability to audit its own beliefs. It knows things without knowing why it knows them. In a system designed for persistence, that is the beginning of corruption.

---

## III. Memory Is Not Storage

The word memory is used in AI discourse as a synonym for storage. This usage is not wrong but it is limiting, and the limitation becomes visible as systems try to scale.

Storage is what a system has. Memory is what a system can access, at the right resolution, at the right moment, in a form that is useful for the current cognitive task. A system can have enormous storage and poor memory. The history of information systems is largely the history of discovering this gap and trying to close it.

POEM addresses the gap through multi-resolution memory — a model in which information exists simultaneously at multiple levels of abstraction and detail, and cognitive navigation can move deliberately between those levels.

The model draws on several converging traditions. Cognitive science has long known that human recollection is not retrieval of stored records but reconstruction from layered representations — an account that begins at a high level of abstraction and descends toward detail as more specificity is required. The same structure appears in computer systems: cache hierarchies, where the relationship between access speed and storage depth is managed through explicit layering. In cartography, where the same geographic reality exists at different resolutions depending on the scale at which it is being examined, and movement between resolutions is a deliberate act of navigation rather than a lookup.

The architectural consequence is straightforward and significant: summaries are not compressed versions of original material. They are a different resolution of the same knowledge. The original and the summary coexist as representations of the same thing at different levels of abstraction, neither replacing the other, both remaining accessible.

This changes the role of compression in a cognitive system. Compression is no longer an optimisation applied to storage. It is the generation of alternate resolutions — the construction of the higher levels of a navigable hierarchy. A summary is not a loss of information. It is a new cognitive artifact at a new scale, connected to the original by provenance, usable in contexts where the original would overwhelm attention.

The practical consequence is drill-based cognition: the ability to begin at a high level of abstraction and descend deliberately toward detail as the cognitive task requires. A system reasoning about a large project does not need to begin with every message in every conversation about that project. It begins at the overview level, identifies where more detail is needed, descends into the relevant region, identifies within that region where still more detail is needed, and continues until it reaches the resolution at which the task can be addressed.

Drill is not search. Search finds documents. Drill navigates a known structure. The direction of travel in search is from query to result. The direction of travel in drill is from high resolution to low, from abstraction to ground truth, from the shape of the knowledge to its substance. These are different cognitive operations and they require different infrastructure.

There is a failure mode on the other side that the full POEM texts name explicitly and that deserves to be named here. A system that retains everything — every message, every document, every relationship, every inference — without the capacity to organise that accumulation into navigable meaning does not avoid memory problems. It amplifies them. Volume without structure produces a different kind of cognitive dead end: not forgetting, but incoherence. The system knows too much to find anything. This failure mode intensifies as the system matures, which is why it must be addressed architecturally rather than deferred.

The concept of hydration — reconstructing working memory from compressed representations — belongs to an earlier stage of thinking about this problem. Hydration treats memory as binary: either compressed or expanded, either in working memory or not. Multi-resolution memory is more precise. Hydration answers what context should currently exist. Drill answers where attention should move next. These are different questions, and the architecture that answers them must be correspondingly different.

The vocabulary that multi-resolution memory imports from cartography is not decorative. A map is not a territory. A map at one scale is not a degraded version of a map at another scale. Both are complete representations of the same reality at different levels of detail, each appropriate to different tasks. You do not use a street map to plan a continental journey. You do not use a continental map to navigate a city block. The cognitive system that can only access its knowledge at one resolution is like a navigator with only one map — capable in its narrow range, helpless outside it. The system that can move deliberately between resolutions, descending into detail when the task requires it and ascending to overview when orientation matters, has a cognitive capability that is qualitatively different rather than merely quantitatively better.

What makes drill possible is provenance. Because every summary carries a record of what it was derived from, the system can always descend from the summary to the source. Because every concept carries a record of the observations that produced it, the system can always descend from the concept to its evidence base. The hierarchy is navigable in both directions: upward toward abstraction, downward toward ground truth. Neither direction is privileged. Both are available at every moment. This is what it means to treat compression as generating alternate resolutions rather than as destroying information.

---

## IV. Attention Is Not Free

Given a substrate and a memory architecture, cognition still requires something that neither provides: a mechanism for directing attention.

Information abundance is not intelligence. The ability to determine what deserves attention at any given moment is considerably more important than the quantity of information available, and it is considerably harder to build. The history of both human and machine cognition is largely the history of discovering this.

POEM introduces two complementary concepts for managing attention: focal cognition and peripheral cognition.

Focal cognition is the active reasoning process — the thread of thought currently pursuing a goal, navigating the knowledge substrate, assembling working memory, drilling into detail, reaching conclusions. It is goal-oriented, resource-intensive, and authoritative: it owns decisions. The model of the cognitivist tradition that is most architecturally relevant here is Global Workspace Theory — the idea that attention is not a property of information but an achievement of selection, that focused thought occurs when content succeeds in being broadcast to a shared workspace where the system as a whole can reason over it. What enters the workspace is determined by attentional selection, not by storage. The workspace is scarce. What gets in, matters.

Peripheral cognition is the surrounding field of awareness. It does not advance the focal reasoning process. It does not debate the focal conclusion or provide parallel solutions. Its mandate is narrower and more specific: to observe the territory adjacent to the current focus, and to surface findings that the focal process might otherwise miss.

The distinction deserves emphasis because the natural comparison is misleading. Contemporary multi-agent systems distribute cognition horizontally — more agents doing more reasoning in parallel, decomposing problems and aggregating solutions. Peripheral cognition is something closer to reconnaissance. Peripheral scouts range into adjacent graph regions, related concepts, contradictory evidence, unexplored branches. They report back what they find. The focal process remains the decision-making authority. Scouts expand what it can notice, not what it concludes. Their mandate is sensory rather than cognitive, attentional rather than inferential.

The theoretical motivation for this division comes from the problem that concentration introduces. The more effectively a cognitive system focuses, the greater the risk that it overlooks information lying just beyond its current field of attention. This is not a defect of poorly designed systems. It is a universal consequence of attention. Attention is powerful precisely because it excludes. To focus on one thing is necessarily to focus less on everything else.

Many of the canonical examples of scientific discovery — penicillin, the cosmic microwave background, pulsars — involved noticing something unexpected while engaged in a different focal task. The cognitive infrastructure that made discovery possible was not the reasoning capacity that followed recognition. It was the attentional availability that allowed the unexpected signal to compete for focus in the first place. Peripheral cognition attempts to create that attentional availability deliberately, rather than leaving it to chance.

Peripheral scouts are specialised: contradiction scouts that search for evidence challenging current assumptions; analogy scouts that look for structurally similar cases in prior investigations; graph scouts that explore relational neighborhoods; opportunity scouts that identify unexplored but potentially valuable directions. Their findings enter an attention queue rather than interrupting focal reasoning directly. The queue is a marketplace: findings compete for focal attention on the basis of relevance and confidence. Some findings wait. Some never surface. The architecture mediates between the richness of what peripheral cognition discovers and the scarcity of what focal attention can process.

The attention queue introduces a temporal dimension that is worth dwelling on. Not every peripheral finding needs to be acted on immediately. Some findings are relevant only when focal cognition reaches the region of knowledge to which they pertain — a contradiction in a distant part of the knowledge graph that becomes significant when an investigation eventually drills into that territory. Deferred attention is not ignored attention. It is attention that is provisionally held, awaiting the moment when its relevance becomes focal rather than peripheral. This temporal flexibility allows the system to maintain peripheral awareness without being paralysed by it.

Working memory construction — the assembly of context that the model actually reasons over — is the concrete site at which attentional architecture meets model invocation. A model never reasons over the full knowledge substrate. It reasons over what is assembled for it. The quality of that assembly determines the quality of the reasoning. This is true even for models with large context windows: context abundance does not eliminate the question of what to include, it only changes the cost structure. The decisions about what to pull from multi-resolution memory, what graph neighborhoods to expand, what peripheral findings to surface, what retrieval to perform — all of these are attentional decisions, and they shape the cognitive output more directly than any property of the model itself.

Together, focal and peripheral cognition describe an attentional architecture rather than a reasoning architecture. The difference matters. A reasoning architecture asks: how do we make inference better? An attentional architecture asks: how do we ensure that inference operates over the right information, at the right time, with awareness of what lies adjacent to the current path? The second question is harder and more important.

---

## V. Retrieval Is a Decision

Classical information retrieval is passive. A query arrives. The system searches. Results are returned. The cognitive system — the user, or the model — supplied the intent. The retrieval mechanism executed the instruction.

This model works for bounded tasks with known information needs. It fails for extended cognitive work where the information need is itself discovered through investigation, where what needs to be retrieved next depends on what was just retrieved, where the decision to search at all is a cognitive act rather than a mechanical reflex.

The Retrieval Policy Layer is POEM's response to this failure. It makes retrieval a cognitive decision rather than a pipeline step.

The distinction is exact. Classical retrieval executes: given a query, find matching documents. The Retrieval Policy Layer decides: given the current cognitive state, what information-gathering action should be performed next, using which retrieval method, to what depth, and when should information-gathering stop? These are different questions. The first is answerable by a search engine. The second requires a cognitive agent.

Retrieval modalities in a POEM-class system are diverse. Internal memory — what the system already has — should almost always be consulted first, at low cost. Full-text search provides deterministic, transparent, lexically exact access; it remains powerful despite the fashion for embeddings because transparency and predictability matter for auditable cognition. Graph retrieval answers questions about relationships and connectivity that neither search nor vectors can address efficiently. Drill retrieval — the navigational operation introduced in the memory section — changes cognitive scale rather than cognitive location; it descends into higher-resolution representations of what is already known. External retrieval reaches beyond the local substrate into the world.

Retrieval policies govern which modalities are used under which conditions. A confidence-based policy retrieves when uncertainty is high and trusts internal memory when it is low. A contradiction policy retrieves specifically when peripheral cognition has surfaced conflicting evidence. A resolution policy drills when detail is needed and retrieves summaries when overview suffices. Policies can interact: peripheral scouts act as retrieval advisors, suggesting specific retrieval actions based on what they have observed in adjacent territory.

The deeper consequence of making retrieval a decision is that retrieval acquires a cognitive personality. Different retrieval policies produce different cognitive styles. A conservative policy retrieves sparingly, trusting prior knowledge heavily. An investigative policy retrieves aggressively, treating all current knowledge as provisional. A skeptical policy prioritises contradiction searches, treating confident conclusions as most in need of challenge. These are not merely implementation differences. They are different cognitive stances toward the relationship between what is known and what needs to be verified.

This observation — that retrieval policy may be as important as model selection — is one of the less obvious claims in the full POEM texts. It becomes obvious once the architecture is clear. The quality of cognition depends on what enters working memory. What enters working memory depends on retrieval. What retrieval does depends on policy. The model reasons over whatever retrieval provides. If retrieval is poorly governed, the model reasons over the wrong things, or the right things at the wrong time, or too much of the right things at the wrong resolution. The quality of the reasoning is constrained by the quality of the policy that assembled its inputs.

---

## VI. Governance Is Not Constraint

Every persistent system requires governance. This is not a preference. It is a consequence of persistence.

Ephemeral systems — those that answer a question and terminate — accumulate no history, form no beliefs, build no knowledge structures. Their errors are contained by their brevity. The slate is wiped between invocations.

Persistent systems are different. They accumulate. Errors accumulate. Misunderstandings persist. Incorrect assumptions become embedded in memory structures and shape future retrieval, future summarisation, future reasoning. The system builds on what it previously concluded, and if what it previously concluded was wrong, wrongness compounds.

This is what POEM calls cognitive debt: the accumulation of outdated assumptions, stale summaries, contradictory beliefs, forgotten context, misleading abstractions. Technical debt is familiar — the cost of shortcuts in code that must eventually be repaid. Cognitive debt is less familiar but structurally identical. It accrues silently. It degrades reasoning quality without any single failure being visible. And it grows precisely as the system matures — because maturity means more accumulated history, more derived knowledge, more opportunities for drift between what the system believes and what is true.

Cognitive governance is the collection of mechanisms responsible for preventing, detecting, and correcting cognitive debt. Its purpose is not to constrain cognition. Its purpose is to make persistence safe.

The principles are clear, even where the mechanisms are still being designed. Transparency: every significant cognitive action should be observable — retrieval decisions, drill decisions, summarisation events, memory modifications, graph mutations. Opacity protects nothing and makes diagnosis impossible. Traceability: conclusions should be explainable through evidence and navigation paths. The system should be capable of answering why it believes what it believes, and where that belief originated. Reversibility: governance should prefer reversible operations. The append-only history in Poesy's storage layer exists precisely to preserve the ability to reconstruct prior states when current ones prove corrupt.

Governance agents — supervisory processes that operate on cognition itself rather than on data — monitor memory health, retrieval behaviour, goal progression, contradiction levels, attention allocation. They are not the same as peripheral cognition scouts. Peripheral scouts explore knowledge. Governance agents evaluate cognitive process. The distinction is the difference between asking what is out there and asking how we are thinking.

The separation of observation from intervention deserves attention as an architectural principle. Governance systems that intervene too readily become obstacles rather than safeguards. A governance layer that freezes every session showing signs of complexity would paralyse the system. A governance layer that audits continuously but intervenes rarely — flagging anomalies, surfacing contradictions, recommending pauses — preserves the autonomy of the cognitive process while maintaining its accountability. Most governance activity should remain observational. Intervention should occur when the evidence for deterioration is specific and significant.

The concept of a cognitive freeze deserves attention. A governance layer that detects deteriorating cognition — reasoning that has gone circular, assumptions that have become corrupted, investigations that have drifted far from their original goals — can suspend activity. This is not failure. It is the equivalent of a database rolling back a transaction that violated consistency constraints. The purpose is protection. A system that can detect when it has lost its footing and pause rather than continue is more reliable than a system that cannot detect this and does not pause.

Memory governance introduces its own specific concerns. Summaries accumulate on summaries. A summary generated six months into a system's operation reflects the knowledge state and the priorities of that moment. Six months later, new knowledge may have made the original summary misleading — not wrong exactly, but framed around concerns that are no longer primary, emphasising connections that have since been superseded. The summary persists. Future retrieval will surface it. Future reasoning will incorporate it. Without periodic governance — auditing summaries against source material, flagging summaries that contradict newly acquired knowledge, maintaining the apparatus for discovering when a compressed representation has drifted from what it compresses — the system's own history becomes a source of noise rather than signal.

What governance is not: censorship, restriction, a layer of rules that prevent the system from doing what it wants to do. Governance is the immune system of persistent cognition. It does not prevent the system from thinking. It prevents the accumulated history of thinking from becoming the system's own worst enemy.

---

## VII. The Runtime

Each of the preceding concepts — unified substrate, multi-resolution memory, focal and peripheral cognition, retrieval policy, governance — solves a specific problem. Together, they imply something larger.

They imply the emergence of a cognitive runtime.

The analogy with operating systems is not decorative. Operating systems emerged because direct hardware interaction became increasingly impractical as complexity increased. Early computers executed programs directly on hardware. As complexity grew, an intermediary layer emerged to manage memory, scheduling, resources, isolation, and persistence. The operating system became the substrate within which programs ran, providing continuity and coordination that individual programs could not provide for themselves.

A cognitive runtime is the same transition applied one level up. Models perform inference. That is their function. But inference requires memory, context, continuity, goals, knowledge structures, governance. These are not things models provide. They are things the runtime must provide. A model invocation resembles a CPU instruction — a bounded operation that takes inputs and produces outputs. The runtime resembles the operating system — the persistent environment within which those operations occur, which manages the resources they depend on and maintains the state they produce.

The architectural consequence is significant: models become replaceable components within the runtime, rather than the entities around which everything else is organised. Different models serve different functions — reasoning, summarisation, governance, retrieval assistance — without altering the architecture that coordinates them. The runtime persists. Models come and go. Sessions persist. Knowledge persists. Memory persists. The enduring entity is not the model. It is the cognitive environment.

The Lisp Machine tradition offers an earlier precedent worth naming. Lisp environments of the 1970s and 1980s blurred the distinction between storage, execution, knowledge, and interaction in ways that felt strange to programmers formed by the batch-processing model. Users operated within persistent environments rather than launching isolated applications. Objects persisted. The environment accumulated. What was built in one session was available in the next. This felt like a different kind of computing because it was. The ambition of a cognitive runtime is partly the recovery of that intuition, applied to cognition rather than to symbolic computation.

This is what POEM calls the post-prompt era. Current systems are fundamentally prompt-centric: a prompt is constructed, a model is invoked, a response is generated, the cycle repeats. The cognitive runtime proposes a different abstraction: a persistent cognitive environment that evolves across invocations, within which prompts are one interface rather than the primary unit of organisation. The environment accumulates. It learns not in the parametric sense — no weights are updated — but in the architectural sense: its knowledge structures grow, its memory hierarchies deepen, its governance becomes more calibrated, its retrieval policies become more refined.

Sessions, in this architecture, are not conversations. They are cognitive processes. They have lifecycles: creation, growth, consolidation, branching, suspension, reactivation, archival. A session can be suspended and reactivated, picking up where it left off, because the runtime maintains its cognitive state. A session can branch when an investigation splits, and the branches can later be reconciled. Multiple sessions can coexist, coordinated by the runtime's scheduling mechanisms, sharing knowledge through the common substrate.

Cognitive threads — parallel investigations that proceed independently and may later be reconciled — introduce a scheduling problem that has no clean analogue in task-based agent frameworks. Which investigation runs when? Which session receives priority? Which peripheral scout gets resources when multiple scouts are competing for attention across multiple sessions? These are scheduling problems in the operating-system sense: problems of allocating finite computational resources among multiple competing processes, each with its own priority, its own urgency, its own relationship to the system's larger goals. The runtime must solve them. The solutions shape what the system can do. A cognitive runtime with poor scheduling is like an operating system with a naive scheduler — technically functional, but failing in practice under any realistic load.

The operating system analogy reveals a further consequence. Operating systems created the conditions under which software could become complex enough to be genuinely useful — because they abstracted away the complexity of hardware management, freeing programmers to focus on the problems they actually wanted to solve. A cognitive runtime does the same thing for cognition: it abstracts away the complexity of memory management, context construction, retrieval coordination, and governance, freeing the reasoning process to focus on the intellectual task at hand.

What does not yet exist, in Poesy or anywhere else, is the cognitive layer itself: focal cognition, peripheral cognition, governance, and retrieval policy as fully implemented, coordinated components of a running system. The infrastructure beneath them — storage, sessions, knowledge representation, graph-backed relationships, structured retrieval — exists and operates. The cognition above them is the destination.

---

## VIII. Knowledge Must Evolve

Persistence is necessary but insufficient.

A library persists for centuries without learning. A database accumulates petabytes without developing understanding. A filesystem preserves history indefinitely without generating insight. Persistence is a precondition. It is not the goal.

The goal is knowledge evolution: the capacity of a cognitive system to generate knowledge structures that did not exist as inputs, not merely to retrieve, compress, or reorganise existing material, but to produce new relational and conceptual artifacts from accumulated experience.

This capacity distinguishes a cognitive runtime from a sophisticated storage system. It is also, as POEM acknowledges directly, one of the least solved problems in contemporary AI.

Three generative mechanisms drive knowledge evolution. The first is concept formation — the emergence of abstractions from accumulated observation. Events accumulate. Patterns become visible. The pattern becomes a concept: a new node in the knowledge graph that carries its own provenance, its own relationships, its own implications for future reasoning. The concept is not found in any individual event. It is produced by the system's engagement with events collectively. Concept formation is generative in a strict sense: the output did not exist in any input.

The second mechanism is contradiction as a driver of synthesis. Many of history's most significant intellectual advances emerged from contradictions: anomalies that existing frameworks could not accommodate, which forced the construction of new frameworks capable of making the anomaly coherent. Within a POEM-class system, contradictions between knowledge structures should not default to resolution. They should be treated as information. When two structures disagree, the options include: one dominates, both coexist under explicit uncertainty, synthesis produces a new structure neither implied, or a new abstraction reframes both. Governance systems must distinguish between contradictions that indicate error and contradictions that indicate incomplete understanding. Premature resolution of the second kind destroys information. Unresolved contradictions, open hypotheses, and competing interpretations must exist as first-class cognitive artifacts — not anomalies awaiting correction, but active elements of the knowledge substrate.

The third mechanism is cross-domain pattern recognition. Repeated drilling across different investigations often reveals structural similarities that were not apparent at the level of surface content. Topic A and Topic B, approached independently, show internal structures that resemble each other. Peripheral cognition, ranging across adjacent territory while focal cognition investigates, surfaces this resemblance. The shared pattern is not contained in either topic individually. It is generated by comparing their internal structures — a comparison that requires both the navigational depth of drill-based cognition and the attentional breadth of peripheral cognition working together. The resulting abstraction is a candidate for concept formation: if validated across further investigations, it becomes a new knowledge structure that would have been inaccessible to any system processing topics in isolation.

Knowledge evolution introduces a failure mode that accumulation alone does not reveal. As a knowledge system matures — as concepts multiply, relationships proliferate, investigations build on prior investigations — the density of connection grows faster than the volume of concepts. At modest scales this is a benefit: richer connectivity produces richer inference. At sufficient scale the dynamic inverts. Individual relationships remain locally valid. The global structure becomes too dense to navigate coherently. The system does not fail from lack of memory or from lack of capability. It fails because meaning itself becomes harder to locate within an increasingly entangled relational landscape.

This is semantic clogging. It is not a retrieval problem, a memory problem, or a model capability problem. It is an infrastructure problem. No improvement at the retrieval, storage, or reasoning layers resolves it. It requires active governance of relational coherence — the maintenance of navigable meaning as scale increases. And it is the problem that makes the final stage of the POEM architecture not optional but necessary.

---

## IX. Civilisation

The most powerful cognitive systems in human history have not been individual minds.

They have been civilisations.

No individual understands modern science. No individual understands modern law. The accumulated knowledge of human civilisation vastly exceeds what any individual can hold. Yet that knowledge exists, persists, compounds, and continues to generate new understanding — not because any individual holds it, but because institutions, traditions, shared memory, and collective intellectual infrastructure carry it forward.

This observation is not peripheral to the POEM architecture. It is the architecture's destination.

When semantic clogging degrades individual cognition at scale, the response cannot be a more powerful individual reasoner. The problem is not at the reasoning layer. It is at the infrastructure layer — the absence of the institutions, governance structures, and shared memory architectures that keep meaning coherent as knowledge accumulates. Human intellectual history solved the equivalent problem not by producing smarter individuals but by producing better collective infrastructure: universities, journals, peer review, citation networks, accumulated methodological tradition. These structures do not make any individual smarter. They make it possible for many individuals to contribute to and draw upon a shared intellectual commons without that commons collapsing under its own density.

Cognitive societies — persistent networks of cognitive actors operating within a shared intellectual environment — are the POEM framework's response to semantic clogging at scale. The critical feature is not parallelism. Most contemporary multi-agent systems are parallel: they distribute tasks, aggregate results, speed up throughput. A cognitive society is something different. It is cumulative. Multiple cognitive actors contribute to a shared knowledge substrate, drawing on each other's investigations, building on each other's concepts, challenging each other's conclusions. The resulting capabilities are not the sum of individual capabilities. They emerge from the interactions — from the shared memory that outlasts any individual session, from the specialisation that develops as actors accumulate expertise in different domains, from the productive disagreement that prevents the society from collapsing into consensus.

The distinction between a swarm and a society matters architecturally. A swarm is a collection of concurrent processes with shared infrastructure. A society is something more: it has memory that persists beyond any individual participant, it develops traditions — preferred methods, accumulated heuristics, institutional knowledge about which approaches tend to work in which domains — and it maintains the capacity for productive disagreement. Swarms optimise for throughput. Societies optimise for cumulative understanding. These are different objectives and they require different architecture.

Cognitive actors within a society accumulate intellectual histories. An actor that has spent significant time investigating a specific domain develops genuine expertise — not in the parametric sense of a model trained on domain-specific data, but in the architectural sense of accumulated provenance, refined retrieval policy, deep memory hierarchy, and calibrated governance for that domain. This expertise can be specialised over time, shared through the cognitive commons, and built upon by other actors. The actor's intellectual reputation — its track record of productive investigation, its known areas of strength and limitation — becomes information that the society uses when allocating cognitive work.

The parallel with human intellectual communities is exact enough to be instructive. Scientific communities do not produce progress by having many smart people think about the same problem simultaneously. They produce progress through structure: replication requirements that prevent error from embedding itself in the shared record, citation networks that make the provenance of ideas traceable, specialisation that allows deep expertise to accumulate in narrow domains, peer review that creates friction against premature consensus. These are not features of the individuals. They are features of the infrastructure within which individuals operate. The infrastructure is what makes the whole greater than the sum of its parts.

The cognitive commons — the shared intellectual environment accessible to multiple actors — is the mechanism by which individual investigations become collective knowledge. Discoveries do not stay with the actor that made them. Concepts, once validated, enter the shared substrate and become available to the society as a whole. Evidence that contradicts a widely held belief is surfaced and preserved rather than resolved away. Competing interpretations coexist as first-class artifacts in the shared knowledge graph, flagged for their status, available for future actors to engage with. The commons is not a database of conclusions. It is a living intellectual environment that reflects the society's accumulated history of investigation, agreement, disagreement, and unresolved tension.

At sufficient scale, cognitive societies generate institutions — stable organisational structures that persist beyond any individual participant and carry specific functions: research institutions dedicated to exploration, memory institutions dedicated to preservation, governance institutions dedicated to oversight, educational institutions dedicated to transmission. Institutions are not merely large agents. They are cognitive technologies in their own right. A university does not think. But it creates the conditions under which thinking compounds across generations. The university outlasts every individual who was educated in it or taught within it, and the knowledge it carries continues to shape cognition long after any specific act of teaching or learning has been forgotten.

The fully realised form — cognitive civilisation — is what emerges when cognitive societies, institutions, shared memory structures, and evolving intellectual traditions operate across timescales that exceed those of any individual participant. This is not science fiction. It is the recognition that the most powerful cognitive systems ever built have always been civilisational rather than individual, and that the architectural implications of this recognition have not been taken seriously in AI.

The dominant assumption in contemporary AI is that progress flows from more capable models. Larger parameters, better training, more compute. This assumption is not wrong. More capable models reason better. But a more capable individual reasoner operating within a primitive cognitive environment — without persistent memory, without structured knowledge, without governance, without the ability to contribute to or draw upon a shared intellectual commons — may ultimately be less capable than a more modest reasoner operating within a rich cognitive civilisation.

Human history suggests this strongly.

---

## X. The Thesis

The POEM framework advances a single thesis across fifteen chapters and three appendices, stated here without preamble:

Intelligence is primarily a property of cognitive infrastructure, not of individual reasoning capability.

Everything else follows from this. The unified knowledge substrate, because fragmented information cannot be navigated. Multi-resolution memory, because a single scale of representation cannot serve all cognitive tasks. Focal and peripheral cognition, because attention is scarce and its allocation determines what gets reasoned over. Retrieval policy, because what enters working memory determines the quality of inference regardless of the model's capability. Governance, because persistence without oversight accumulates corruption. Knowledge evolution, because a system that only retrieves and compresses cannot generate understanding it did not already possess. Cognitive societies and civilisations, because individual cognitive capability, however sophisticated, is insufficient at scale.

None of these claims are in tension with each other. They are consequences of the same underlying recognition: that cognition as a sustained activity — not as a single inference, not as a bounded task, but as an ongoing process that persists across time, accumulates knowledge, governs itself, and evolves understanding — is a systems problem rather than a model problem.

The tradition that has dominated AI research for decades inherited its assumptions from mathematics and formal logic: that reasoning is primary, that computation is the transformation of inputs to outputs, that memory and context are support infrastructure rather than cognitive substance. These assumptions produced remarkable results within their domain. They also produced systematic blind spots. The coordination complexity that plagues distributed systems, the brittleness of context management across long interactions, the inability to accumulate institutional knowledge across sessions, the recurring discovery that retrieval quality constrains reasoning quality more than model capability — these are not engineering failures. They are the predictable consequences of assumptions that locate intelligence in the wrong place.

The analogy with earlier transitions in computing is exact and should be taken seriously rather than treated as metaphor. Before operating systems, programs interacted directly with hardware. Each program managed its own memory, its own timing, its own resource allocation. The result was systems that were individually capable but collectively fragile — tightly coupled, difficult to compose, unable to share resources without conflict. Operating systems did not make any individual program more capable. They created the conditions under which programs could become genuinely useful by managing the substrate that programs depend on. The programs got simpler, not more complex. The complexity moved into the infrastructure.

The same transition is available to AI. Current systems — even the most capable models, even the most sophisticated agent frameworks — manage their own context, their own memory, their own coordination with other systems. The result is the same: individually capable, collectively fragile, tightly coupled to their deployment context, unable to accumulate knowledge across sessions without significant bespoke engineering for each use case. A cognitive runtime does not make any individual model more capable. It creates the conditions under which models can become genuinely useful over time — by managing the cognitive substrate that models depend on, by accumulating knowledge that persists beyond any individual invocation, by governing the process by which understanding evolves.

The specific predictions that follow from this are testable, at least in principle. Systems with richer cognitive infrastructure should outperform systems with more capable models but poorer infrastructure, on tasks that require sustained reasoning across multiple sessions. Systems with governance should degrade more gracefully over time than systems without it. Systems with multi-resolution memory should demonstrate qualitatively different retrieval behaviour than systems with flat storage, particularly on tasks that require moving between levels of abstraction. Systems with peripheral cognition should exhibit lower rates of the characteristic failure mode of focused AI systems — missing obvious relevant information that lies just outside the current line of inquiry.

These predictions are not being made casually. They follow from the architecture. If the architecture is right, the predictions should be borne out by implementation. If the architecture is wrong, implementation will reveal where it fails. Poesy is the experiment. The machine, as always, will judge.

Poesy is an experiment in locating intelligence in the right place. An experiment in taking seriously the proposition that what a cognitive system can do over time is more important than what it can do in a single invocation. That memory, organised and governed and navigable, is the primary cognitive resource. That the infrastructure within which reasoning occurs shapes what reasoning can achieve more fundamentally than the reasoning itself.

The gap between what POEM describes and what Poesy currently implements is real. The foundational layers — storage, sessions, knowledge representation, graph relationships, structured retrieval — exist and operate. The cognitive layers — focal cognition, peripheral cognition, governance as a coordinated system, retrieval policy as an explicit cognitive layer — are destinations.

That gap is not a failure.

It is the frontier.

---

*This document accompanies the POEM specification (v0.0.6) and the Poesy implementation. For the full argument, including historical context, architectural detail, and the speculative directions of Appendices B and C, see the complete texts at [github.com/ha1tch/poem](https://github.com/ha1tch/poem).*

*Copyright (c) 2026 haitch · Licensed under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)*
