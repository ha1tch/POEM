# POEM — Persistent Operative-cognitive Environment Model

**Version 0.0.6** · 2026-06-07

POEM is a conceptual framework describing what a persistent cognitive runtime is, what properties it must possess, and what design principles it must respect. It defines a class of systems rather than a single implementation.

**[Poesy](https://github.com/ha1tch/poesy)** is the first concrete attempt to build a POEM-class system — the implementation against which these principles are tested, refined, and grounded. Where POEM asks what such a system must be, Poesy asks what it takes to build one. Any gap between what the architecture describes and what Poesy does today is not a failure. It is the frontier.

---
## What a Cognitive Runtime Must Be
The document [What a Cognitive Runtime Must Be](COGNITIVE-RUNTIME-PRIMER.md) contains a condensed account of the ideas developed at length in the chapters of the POEM concept — the Persistent Operative-cognitive Environment Model — and in the architectural discussion of Poesy, its first implementation.
Both the primer and the chapters cover the same scope at comparable altitude, the primer is a higher efficiency read. 
---
## How to read the POEM document

The POEM chapters progress from motivation through foundational mechanisms to integrating architecture and speculative horizon. Readers new to the project should start with the [Prologue](poem-00-prologue.md) and [Vision](poem-01-vision.md). Those interested in a specific subsystem can jump directly to the relevant chapter; each is written to be legible in isolation, though forward references appear throughout.

The three appendices serve different purposes: Appendix A is a working reference lexicon, while Appendices B and C are explicitly speculative and address long-horizon directions that depend on parallel research programmes outside POEM proper.

---

## POEM Chapters

### [0. Prologue](poem-00-prologue.md)

The intellectual origin of Poesy: a practical problem in session continuity that revealed a deeper challenge in cognition management. Explains the distinction between POEM as a framework and Poesy as its implementation, and how to read the rest of the document.

---

### [1. Vision](poem-01-vision.md)

The long-term objective — a runtime capable of supporting persistent machine cognition — and why that objective matters. Traces the intellectual lineage of the project through hypertext theory, knowledge representation, cognitive science, and the history of AI, locating POEM in relation to each tradition.

---

### [2. Current Architecture](poem-02-architecture.md)

A description of [Poesy](https://github.com/ha1tch/poesy)'s present structure as an intermediate stage between a conversational runtime and a full cognitive runtime. Covers the four-layer model (Storage, Knowledge, Cognition, Model), session management, context reconstruction, and the multi-provider model abstraction.

---

### [3. Unified Knowledge Model](poem-03-ukm.md)

The central knowledge architecture: a substrate in which information exists simultaneously as conversation history, documents, relational records, graph nodes, and search indexes, without those representations being isolated from one another. Explains why fragmentation is the default in software systems and how UKM works against it.

---

### [4. Multi-Resolution Memory](poem-04-multires-memory.md)

Memory treated not as a binary between remembered and forgotten, but as a hierarchy of representations at different levels of abstraction and detail. Draws on cognitive psychology, hierarchical storage systems, geographic information systems, and computer graphics to motivate the design.

---

### [5. Focal Cognition](poem-05-focal-cognition.md)

The active reasoning process: the mechanism by which attention selects goals, drills into knowledge, evaluates evidence, and produces decisions. Introduces Global Workspace Theory as the architectural foundation for how focal attention should work within the cognitive substrate.

---

### [6. Peripheral Cognition](poem-06-peripheral-cognition.md)

The layer of awareness surrounding focal reasoning. Peripheral processes do not advance the main line of reasoning; they range into adjacent territory — monitoring for contradictions, noticing analogies, flagging opportunities — and expand what the focal process can notice. Addresses the structural problem that concentration introduces: the risk of systematic inattention to what lies just outside the current focus.

---

### [7. Cognitive Governance](poem-07-cognitive-governance.md)

The mechanisms responsible for monitoring, auditing, and regulating cognition. Distinguishes cognitive governance from traditional software governance: where the latter is concerned with correctness and permissions, cognitive governance must additionally manage attention, belief formation, goal alignment, reasoning quality, and information integrity.

---

### [8. Retrieval Policy Layer](poem-08-retrieval-policy.md)

An active cognitive layer that determines when to retrieve, which retrieval method to use, how deeply to explore, and when to stop gathering information. Distinguishes retrieval policy from retrieval mechanism: classical retrieval executes instructions; the retrieval policy layer decides what instructions to issue and why.

---

### [9. Cognitive Runtime](poem-09-cognitive-runtime.md)

The integration chapter. Shows how the preceding components — UKM, multi-resolution memory, focal and peripheral cognition, governance, retrieval policy — combine into a runtime that sustains cognition across time rather than merely processing individual requests. Uses the analogy of operating systems as a prior generation of the same design problem.

---

### [10. Knowledge Evolution and Emergent Understanding](poem-10-knowledge-evolution.md)

Addresses the distinction between persistence and evolution: how a POEM-class system must be capable of generating knowledge structures that did not exist as inputs, not merely retrieving or reorganising existing material. Treats knowledge evolution as one of the least-solved problems in contemporary AI and examines what architectural properties make it possible.

---

### [11. Collective Cognition](poem-11-collective-cognition.md)

Examines what happens as individual cognitive systems mature and their knowledge density increases past the point any focal process can navigate. Introduces the concept of *semantic clogging* — not a retrieval or memory problem, but an infrastructure problem — and motivates cognitive societies as the necessary response. Draws the parallel with civilisational infrastructure: universities, journals, peer review, citation networks.

---

## Appendices

### [Appendix A: Terminology and Conceptual Lexicon](poem-12-appendix-a.md)

A reference vocabulary for the POEM research programme. Defines the project's core concepts as architectural terms rather than implementation details: POEM, Poesy, Unified Knowledge Model, Multi-Resolution Memory, Focal Cognition, Peripheral Cognition, and the full set of constructs introduced across the chapters.

---

### [Appendix B: Cognitive Civilisations and the Future of Persistent Intelligence](poem-13-appendix-b.md)

*Speculative.* Addresses long-horizon directions at the largest scale the architecture currently contemplates: cognitive civilisations as the emergent consequence of cognitive societies. Situates POEM in relation to two parallel research programmes — TOSID (a universal semantic classification system) and KMAC (a compiled knowledge representation) — which together constitute the infrastructure layer upon which POEM-class cognitive societies would depend at scale.

---

### [Appendix C: Beyond Agents — The Emergence of Cognitive Infrastructure](poem-14-appendix-c.md)

*Speculative.* A synthesis chapter. Argues that the dominant assumption — progress flows from more capable models — addresses only one axis of the problem. Situates [Poesy](https://github.com/ha1tch/poesy) within the longer history of cognitive infrastructure, from writing and libraries through operating systems to the present, and makes the case that the next transformation will be determined by the cognitive infrastructures within which models operate, not by models alone.

---

## Versioning

| Version | Date | Summary |
|---------|------|---------|
| 0.0.6 | 2026-06-07 | Enriched treatment of Global Workspace Theory (Ch. 5); peripheral reconnaissance clarified (Ch. 6); reconstructive memory consequences developed (Ch. 4); cross-references consolidated (Chs. 3, 6) |

Earlier version notes are kept in the [VERSION](VERSION) file.

---

## Licence

Copyright (c) 2026 haitch  
Licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
