# Functional Flow Artifact Diagram (FFAD) Specification
**Version 1.0 Draft**  
© 2025 DoNew Innovations
Licensed under CC BY 4.0

## 1. Introduction
- Purpose of FFAD
- Relation to other notations (SysML, UML, FFBD, DDD)
- Intended audience (systems engineers, software architects, multidisciplinary teams)
- Scope and limitations

## 2. What is an FFAD?
FFAD (Functional Flow Artifact Diagram) is a semi-formal diagram that shows how functions exchange explicit artifacts (data, energy, materials) via acyclic forward flows and explicit feedback channels, bridging functional and contextual modeling across disciplines. FFADs integrate functional flows with explicit artifact exchanges. In an FFAD, each block represents a function or capability (a noun phrase describing what the system does), and each directed arrow represents a flow labeled with both a verb and the artifact being produced, consumed, or reported (e.g., provides map, issues motor commands, reports status). Subgraphs group related functions into higher-level capabilities or contexts. Forward flows (e.g., provides, issues, powers, replenishes) are acyclic, while feedback flows (e.g., reports X) are explicitly distinguished. FFADs make visible not only the sequence of functions but also the tangible data, material, or energy artifacts exchanged across multidisciplinary boundaries, providing a lightweight, accessible, and domain-agnostic complement to notations such as SysML, UML, FFBD, and DDD context maps.

## 3. Relation to other notations
Traditional modeling languages like SysML and UML are powerful but often too general-purpose or software-centric for multi-domain systems. SysML inherits its foundations from UML, extending it with diagrams for requirements, parametrics, and physical structure, but functional flow modeling is split across multiple diagram types (activities, IBDs, sequence diagrams). UML activity diagrams emphasize control flow, while SysML internal block diagrams emphasize structure, meaning artifact exchanges across disciplines are either implicit or scattered. Classical functional flow block diagrams (FFBDs) capture sequencing of functions, and data-flow diagrams (DFDs) show information movement, but both typically omit explicit labeling of artifacts like energy or materials. Similarly, domain-driven design (DDD) context maps show high-level bounded contexts and relationships, but they deliberately abstract away the detailed flows of artifacts. As a result, none of these notations provides a lightweight, unified view that shows both functions and their cross-domain artifact exchanges in a single diagram.

In contrast, FFAD explicitly integrates function and artifact in one semi-formal notation. Blocks represent functions or capabilities (noun phrases), while arrows are always labeled with both a verb and an explicit artifact, clearly distinguishing forward flows (acyclic provisions, issues, powers) from feedback flows (reports). Subgraphs group functions into logical contexts, bridging strategic boundaries similar to DDD context maps while remaining concrete at the flow level. This dual focus allows FFAD to combine the sequencing awareness of FFBDs, the data sensitivity of DFDs, and the contextual grouping of DDD with a simple and consistent syntax. The result is a notation optimized for cross-domain functional-artifact reasoning: engineers and stakeholders can see not only what functions occur, but also the tangible data, material, or energy exchanged between them, without needing multiple overlapping diagrams as in SysML or UML.

## 4. Definitions
- **Function/Capability Block**: A noun phrase describing what the system does.
- **Artifact**: Explicit data, material, or energy item exchanged between functions.
- **Forward Flow**: Directed edge labeled with a verb + artifact, describing production or provision. Must be acyclic.
- **Feedback Flow**: Directed edge labeled “reports X,” describing monitoring, measurements, or feedback.
- **Subgraph**: Grouping of related functions/capabilities into a logical context.

## 5. Core Elements

### 5.1 Blocks
- Represented as nodes (rectangles in Mermaid).    
- Each block corresponds to a **single function, capability, or component**.
- Blocks are named with **nouns only** (no verbs).
- Each artifact has a **single owning block** (no duplication).
### 5.2 Flows
- Directed arrows between blocks.
- Must be labeled with **verb + artifact**.
- Categories of flows:
	- Forward Flows (acyclic only)
		- Allowed verbs: `provides`, `issues`, `powers`, `publishes`, `replenishes`, `shares`, `adopts`, `translates`.
	- Feedback Flows
		- Allowed form: `reports [artifact]`.
### 5.3 Subgraphs (Contexts)
- Logical grouping of blocks.
- Labeled with a higher-level capability, domain, or context.
- Styled consistently (e.g., gray background `#777777` with black border).
- A subgraph cannot have the same name as any block inside it.    

## 6. Diagram Rules
1. Forward flows must form an **acyclic graph**.    
2. Feedback flows may form cycles, but only with the `reports X` form.
3. Each artifact must be **unique and owned** by a single producing block.
4. Arrows must never omit the **artifact name**.
5. Blocks must be grouped into subgraphs where logical.
6. Diagram output must conform to **Mermaid syntax** with initialized font size and styling.
   
## 7. Example

``` mermaid 
%%{init: {"themeVariables": { "fontSize": "18px", "fontFamily": "Arial"}}}%%

graph TD

subgraph Plan
  Planner
end

subgraph Action
  Actuation
  Sensing
end

Planner -- issues motor commands --> Actuation
Actuation -- reports odometry --> Sensing
Sensing -- provides observations --> Planner

style Plan fill:#777777,stroke:black
style Action fill:#777777,stroke:black
```


## 7. Conformance

A tool or diagram conforms to FFAD v1.0 if:
- All blocks are nouns.    
- All flows are verb + artifact.
- Forward flows are acyclic and use only approved verbs.
- Feedback flows use only `reports X`.
- Each artifact has exactly one owner.
- Subgraphs are styled and named consistently.
- Specification licensed under CC BY 4.0.    
- Users must cite the spec when publishing diagrams or derivatives.
- Reference code implementations (if provided) licensed under GPL v3 (in the future)
