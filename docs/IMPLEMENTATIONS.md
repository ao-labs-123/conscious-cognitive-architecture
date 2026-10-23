# Conscious-Declarative Cognitive Architecture (CDCA) Implementations

## 1. Overview

Conscious-Declarative Cognitive Architecture is structured as a multi-stage cognitive pipeline that transforms raw sensory input into a topological memory representation and then selects actions through a potential-based matching process.

The architecture is intentionally split into prototype modules so each subsystem can be developed and tested independently before integration.

The design is explicitly compatible with a natural-language interpretation pipeline in which linguistic structure is first resolved into semantic particles, those particles are linked into a relational topology, and their spatial arrangement ultimately informs selection and execution.

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

A key extension of this layer is the staged semantic interpretation process used for linguistic and causal analysis:

1. Stage 1: Agent and Subject Estimation
   - Identify the principal actor(s), subject(s), and grammatical anchor(s) of the utterance.
2. Stage 2: Context & Causality Inference
   - Infer temporal, situational, and causal dependencies among events and actors.
3. Stage 3: Modification Clarification
   - Resolve adjectives, qualifiers, negation, and relation-specific constraints.
4. Stage 4: Argument Mapping
   - Map predicate arguments to their semantic roles and dependencies.
5. Stage 5: 5W1H Frame Extraction & Semantic Synthesis
   - Assemble the final discourse frame using who / what / when / where / why / how semantics.

This staged interpretation is the bridge between raw language and symbolic-cognitive memory particles.

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

For natural-language processing, particles should be constructed from parsed semantic units, with fields such as:

```python
particle = {
    "id": "p_agent_f06dbc",
    "label": "I",
    "type": "Agent",
    "state": "determined",
    "constraints": ["subject_role", "speaker_reference"],
    "properties": {
        "tense": "present",
        "modality": "assertive",
        "source": "input-parser"
    }
}
```

Required particle fields:
- id: Unique identifier (e.g., p_agent_f06dbc)
- label: Extracted text content (e.g., "I", "you helped", "i succeeded")
- type: Entity classification (Agent, Cause, Effect, etc.)
- state: Deterministic resolution state (determined / unspecified)
- constraints: Logical rules applied during extraction
- properties: Contextual properties and metadata

This layer creates the physical analogy for memory and procedural states.

### 4.3 Topological Mapper

Purpose:

Discover the manifold or graph structure induced by particle interactions.

Core operations:

- similarity computation
- neighborhood formation
- embedding / graph construction
- manifold deformation under mismatch

Expected behavior:

- nearby concepts cluster
- conflicting states separate
- candidate paths become topologically salient

Topological mapping should be represented as a graph over semantic objects and events:

```python
# Nodes (Objects)
Entity: Agents, Subjects, and Nouns (He, I, you, etc.)
Primary 5W1H Role: Who

Event: Actions, Causes, and Contextual Events (the project, i succeeded, etc.)
Primary 5W1H Role: What (and contextual occurrences)

# Edges (Morphisms / Wires)
source: Domain object ID (starting object)
target: Codomain object ID (ending object)
morphism_type: Functional relation classification (Action, Cause, Relation)
attributes / detail: Contextual bound conditions (When, Where, Why, How)
```

This graph acts as the relational substrate over which the system reasons. In practice, the mapper will infer links such as:
- agent -> action
- cause -> effect
- event -> temporal context
- subject -> property or modification

The result is not merely a dependency graph: it is a topological field in which semantic proximity and relational compatibility influence downstream matching.

### 4.4 Spatial Allocation

Purpose:

Assign particles or concepts to appropriate memory regions.

Responsibilities:

- region assignment
- allocation under constraints
- goal-conditioned placement
- conflict resolution

This module corresponds to the "memory space" part of the architecture where knowledge and contextual memory are differentiated.

After topology is inferred, spatial allocation identifies the coordinate or memory neighborhood for each particle. This is the stage where the semantic graph receives a concrete geometric embedding used for later selection.

### 4.5 Memory Categories

Micro-ACT-R distinguishes between:

Declarative / knowledge memory
- stable invariant structures
- rules, facts, abstract relations

Dynamic / contextual memory
- temporary states
- current context
- situation-specific activation

This distinction is important because the architecture treats memory as both structural and fluid.

## 5. Parsing-to-Topology Interpretation Flow

The full flow from input parsing to action selection can be expressed as:

1. Input Parser performs staged semantic analysis:
   - Agent and Subject Estimation
   - Context & Causality Inference
   - Modification Clarification
   - Argument Mapping
   - 5W1H Frame Extraction & Semantic Synthesis
2. Parsed semantic content is converted into particles.
3. Particles are organized into a topological graph of entities and events.
4. Spatial allocation assigns each particle a coordinate or memory neighborhood.
5. Continuous representations are quantized into memory chunks.
6. Match & Select compares candidate outcomes using potential-based compatibility.

This yields a coherent interpretation loop: language structure -> semantic particles -> topological relations -> spatial assignment -> quantized state -> selection and execution.

## 6. Match & Select Process

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

A useful conceptual extension is to treat quantized particles as analogues of quantum states, where entanglement-like compatibility stabilizes or destabilizes candidate selection. In this interpretation, related particles are not merely connected; their relations create a joint potential landscape for the final choice.

## 7. Data Flow Example

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

An example of the parser-to-particle transformation:

```text
Input: "I succeeded on the project, and you helped me."
  -> Stage 1: Agent and Subject Estimation
     - Agent: I
     - Secondary agent: you
  -> Stage 2: Context & Causality Inference
     - cause: your help
     - effect: I succeeded
  -> Stage 3: Modification Clarification
     - temporal/relational qualifiers resolved
  -> Stage 4: Argument Mapping
     - subject / predicate / object roles assigned
  -> Stage 5: 5W1H synthesis
     - who: I, you
     - what: succeeded, helped
     - why: collaborative project context
  -> Particle extraction:
     - p_agent_i
     - p_agent_you
     - p_event_succeeded
     - p_event_helped
     - p_relation_causal_support
```

## 8. Current Implementation Status

This repository currently provides the architectural specification and integration narrative rather than a full executable runtime.

Current status:

- conceptual design: complete
- prototype repo references: defined
- execution engine: pending / under design
- formal paper draft: in progress

Suggested status labels:

- Conceptual model: implemented
- Interface contracts: in design
- Runtime system: planned
- Validation: upcoming

## 9. Design Principles

- Continuous rather than purely discrete reasoning
- Memory as spatially organized structure
- Topology-aware matching
- Dynamic correction via mismatch feedback
- Goal-conditioned selection
- Multi-scale state representation

## 10. Recommended Next Steps

- Define a shared canonical data schema for particles and memory states
- Define an interface contract for each prototype repo
- Implement a minimal reference runtime
- Add simulation / toy tasks for validation
- Write tests around mismatch correction behavior
- Integrate the modules into a single cognitive loop

## 11. Example Minimal Runtime API

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

## 12. Notes

This document is intentionally higher-level than a traditional engineering spec. It should capture:

- the conceptual architecture
- subsystem boundaries
- implementation roadmap
- expected behavior of the cognitive loop

The long-term goal is not only to simulate reasoning, but to treat reasoning as a dynamical, spatial, and topological process rather than a pure symbolic production system.

In other words, the intended cognitive loop is:

raw language -> semantic parsing stages -> particleization -> topology formation -> spatial allocation -> quantization -> entanglement-like matching -> action selection

This direction makes the repository a conceptual bridge between linguistic analysis, memory representation, and dynamic cognitive control.

