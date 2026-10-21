# Micro-ACT-R Implementations

## 1. Overview

Micro-ACT-R is structured as a multi-stage cognitive pipeline that transforms raw sensory input into a topological memory representation and then selects actions through a potential-based matching process.

The architecture is intentionally split into prototype modules so each subsystem can be developed and tested independently before integration.

---

## 2. High-Level Processing Pipeline

1. Input parsing
   - Convert raw text / environmental signals into structured symbolic or vector representations.

2. Particle encapsulation
   - Represent entities, concepts, or memory fragments as particles with state, activation, and relations.

3. Topological mapping
   - Construct a spatial or graph-like embedding that captures similarity, adjacency, and relational structure.

4. Spatial allocation
   - Distribute particles across topological space according to constraints, similarity, and goal relevance.

5. Quantization & memory synchronization
   - Convert continuous representations into discrete chunks and synchronize memory states across contexts.

6. Match & Select
   - Score candidate actions or memory states using dynamic potential fields and topological compatibility.

7. Execution
   - Emit action, speech, or internal control output based on selected candidate.

---

## 3. Repository Structure

This repository forms the conceptual specification and integration layer for the following prototype repos:

- input-parser
  - Parses and normalizes environmental input into structured representations.
- particle-encapsulation
  - Defines particle-based state representation and interaction dynamics.
- topological-mapper
  - Maps particles into latent or geometric spaces.
- spatial-allocation
  - Allocates entities to regions or memory neighborhoods in topological space.

---

## 4. Core Components

### 4.1 Input Parser

Purpose:
- Convert unstructured raw signals to cognitive primitives.

Responsibilities:
- tokenization / sentence parsing
- entity extraction
- context tracking
- feature normalization

Representative data:
- tokens
- entities
- relations
- attention weights

Expected output:
- a structured representation suitable for particle encoding

---

### 4.2 Particle Encapsulation

Purpose:
- Represent memory items, concepts, or task states as particles.

Core idea:
- Each particle carries:
  - identity
  - activation
  - position
  - momentum / dynamic state
  - relation weights

Suggested state:
```python
particle = {
    "id": "p1",
    "type": "concept",
    "activation": 0.82,
    "position": [0.1, 0.4, 0.7],
    "features": {...},
    "relations": {"r1": 0.9, "r2": 0.6}
}
```
This layer creates the physical analogy for memory and procedural states.

### 4.3 Topological Mapper

Purpose:

Discover the manifold or graph structure induced by particle interactions.
Core operations:

similarity computation
neighborhood formation
embedding / graph construction
manifold deformation under mismatch
Expected behavior:

nearby concepts cluster
conflicting states separate
candidate paths become topologically salient

### 4.4 Spatial Allocation

Purpose:

Assign particles or concepts to appropriate memory regions.
Responsibilities:

region assignment
allocation under constraints
goal-conditioned placement
conflict resolution
This module corresponds to the "memory space" part of the architecture where knowledge and contextual memory are differentiated.

### 4.5 Memory Categories

Micro-ACT-R distinguishes between:

Declarative / knowledge memory

stable invariant structures
rules, facts, abstract relations
Dynamic / contextual memory

temporary states
current context
situation-specific activation
This distinction is important because the architecture treats memory as both structural and fluid.

## 5. Match & Select Process

The Match & Select stage is not a simple rule engine. Instead, it should behave more like:

Candidate generation
Candidate scoring
Potential field relaxation
Selection under mismatch / error energy
Action commitment
In implementation terms, this can be represented as:

```python
candidates = generate_candidates(context, memory)
scores = [score_candidate(c) for c in candidates]
selected = choose_best(scores, topological_constraints=True)
```

Error Energy:

if candidate mismatch is detected, propagate backpressure to the mapping layer
deform topological arrangement
re-evaluate candidate fitness
This is the place where the "self-correction" behavior emerges.

## 6. Data Flow Example

```text
Raw Input
  -> Input Parser
  -> Particle Encapsulation
  -> Topological Mapper
  -> Spatial Allocation
  -> Quantization / Memory Sync
  -> Match & Select
  -> Action / Speech / Execution
```

A simple example:

```text
Input: "The user wants to find a safe route."
  -> parse intent + constraints + environment
  -> encode concept particles
  -> map semantic similarity in topological space
  -> allocate candidate regions
  -> evaluate candidate actions under goal pressure
  -> select best route
```

## 7. Current Implementation Status

This repository currently provides the architectural specification and integration narrative rather than a full executable runtime.

Current status:

conceptual design: complete
prototype repo references: defined
execution engine: pending / under design
formal paper draft: in progress
Suggested status labels:

Conceptual model: implemented
Interface contracts: in design
Runtime system: planned
Validation: upcoming

## 8. Design Principles

Continuous rather than purely discrete reasoning
Memory as spatially organized structure
Topology-aware matching
Dynamic correction via mismatch feedback
Goal-conditioned selection
Multi-scale state representation

## 9. Recommended Next Steps

Define a shared canonical data schema for particles and memory states
Define an interface contract for each prototype repo
Implement a minimal reference runtime
Add simulation / toy tasks for validation
Write tests around mismatch correction behavior
Integrate the modules into a single cognitive loop

## 10. Example Minimal Runtime API

```text
class MicroACTR:
    def __init__(self):
        self.memory = {}
        self.particles = []
        self.topology = None

    def parse_input(self, text):
        ...

    def encapsulate(self, data):
        ...

    def map_topology(self, particles):
        ...

    def select_action(self, goal):
        ...
```
## 11. Notes

This document is intentionally higher-level than a traditional engineering spec. It should capture:

- the conceptual architecture
- subsystem boundaries
- implementation roadmap
- expected behavior of the cognitive loop
  
The long-term goal is not only to simulate reasoning, but to treat reasoning as a dynamical, spatial, and topological process rather than a pure symbolic production system.
