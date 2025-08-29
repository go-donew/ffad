# Functional Flow Artifact Diagram (FFAD)

## What is an FFAD?
FFAD (Functional Flow Artifact Diagram) is a semi-formal diagram designed to describe complex technical systems. 

## What constitutes an FFAD?
FFAD (Functional Flow Artifact Diagram) is a semi-formal diagram that shows how functions exchange explicit artifacts (data, energy, materials) via acyclic forward flows and explicit feedback channels, bridging functional and contextual modeling across disciplines. FFADs integrate functional flows with explicit artifact exchanges. In an FFAD, each block represents a function or capability (a noun phrase describing what the system does), and each directed arrow represents a flow labeled with both a verb and the artifact being produced, consumed, or reported (e.g., provides map, issues motor commands, reports status). Subgraphs group related functions into higher-level capabilities or contexts. Forward flows (e.g., provides, issues, powers, replenishes) are acyclic, while feedback flows (e.g., reports X) are explicitly distinguished. FFADs make visible not only the sequence of functions but also the tangible data, material, or energy artifacts exchanged across multidisciplinary boundaries, providing a lightweight, accessible, and domain-agnostic complement to notations such as SysML, UML, FFBD, and DDD context maps.

## Show me examples

### Robot vaccum cleaner
``` mermaid
%%{init: {"themeVariables": { "fontSize": "18px", "fontFamily": "Arial"}}}%%
graph TD

subgraph Navigation
Mapping
PathPlanning
Localization
end

subgraph Cleaning
Suction
Brush
Dustbin
end

subgraph Power
Battery
ChargingDock
end

subgraph Perception
ObstacleDetection
DirtDetection
end

subgraph Control
MotionControl
end

Mapping -- provides map --> PathPlanning
Localization -- provides position --> PathPlanning
PathPlanning -- issues motor commands --> MotionControl
ObstacleDetection -- provides obstacle data --> PathPlanning
DirtDetection -- provides dirt locations --> PathPlanning
MotionControl -- powers movement --> Brush
MotionControl -- powers movement --> Suction
Suction -- provides suction --> Dustbin
Brush -- provides debris --> Dustbin
Battery -- powers Suction --> Suction
Battery -- powers Brush --> Brush
Battery -- powers MotionControl --> MotionControl
ChargingDock -- replenishes power --> Battery

MotionControl -- reports odometry --> Localization
Dustbin -- reports fill level --> PathPlanning
Battery -- reports charge level --> PathPlanning
ObstacleDetection -- reports environment status --> Mapping

style Navigation fill:#777777,stroke:black
style Cleaning fill:#777777,stroke:black
style Power fill:#777777,stroke:black
style Perception fill:#777777,stroke:black
style Control fill:#777777,stroke:black
```

### Customer Relationship Management (CRM) 
``` mermaid
%%{init: {"themeVariables": { "fontSize": "18px", "fontFamily": "Arial"}}}%%
graph TD
subgraph CustomerManagement
  ContactDatabase
  CustomerProfiles
  InteractionHistory
end
subgraph SalesManagement
  LeadTracking
  OpportunityPipeline
  QuotationEngine
end
subgraph MarketingAutomation
  CampaignManager
  EmailAutomation
  SocialMediaIntegration
end
subgraph ServiceManagement
  SupportTickets
  KnowledgeBase
  ChatSupport
end
subgraph AnalyticsandReporting
  ReportingEngine
  Dashboard
end
ContactDatabase -- provides customer records --> CustomerProfiles
CustomerProfiles -- provides customer insights --> LeadTracking
InteractionHistory -- provides engagement history --> OpportunityPipeline
LeadTracking -- provides lead data --> OpportunityPipeline
OpportunityPipeline -- provides deal updates --> QuotationEngine
CampaignManager -- provides campaign data --> EmailAutomation
CampaignManager -- provides posts --> SocialMediaIntegration
EmailAutomation -- reports open rates --> ReportingEngine
SocialMediaIntegration -- reports engagement metrics --> ReportingEngine
SupportTickets -- provides issue details --> ChatSupport
ChatSupport -- reports chat transcripts --> KnowledgeBase
KnowledgeBase -- provides solutions --> SupportTickets
ReportingEngine -- provides reports --> Dashboard
OpportunityPipeline -- reports pipeline status --> ReportingEngine
SupportTickets -- reports resolution status --> ReportingEngine
CampaignManager -- reports campaign performance --> ReportingEngine
style CustomerManagement fill:#777777,stroke:black
style SalesManagement fill:#777777,stroke:black
style MarketingAutomation fill:#777777,stroke:black
style ServiceManagement fill:#777777,stroke:black
style AnalyticsandReporting fill:#777777,stroke:black
```

## Creating an FFAD
To make it easy for you to use FFADs, here is a custom GPT you can use (free to use) to generate mermaid code for an FFAD. 

## Report an issue or a request
For issues or feature requests in the custom GPT or in the spec, please open a new issue in the Issues section of this repository. In case of any other questions, lease email us at ffad@godonew.com

## Acknowledgement of AI Use
While the authors have been using this format earlier, the inspiration to turn it into a specification came from AI's ability to generate code, especially Mermaid diagrams. This is what powers the AI powered FFAD creator tool (CustomGPT in OpenAI). While everything presented here are entirely the work of the authors, we acknowledge using an AI language model to help polish language, streamline structure, and explore alternative expressions. Any AI-generated text has been carefully reviewed, edited, and approved by the authors to ensure accuracy, clarity, and consistency with our scholarly intent.

## License
Functional Flow Artifact Diagram (FFAD)
**Copyright (c) 2025 DoNew Innovations**

All specifications, documentation, diagrams, and written artifacts in this repository are
**licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0).**

**You are free to:**
- Share: copy and redistribute the material in any medium or format
- Adapt: remix, transform, and build upon the material for any purpose, even commercially

**Under the following terms:**
- Attribution: You must give appropriate credit, provide a link to the license, and indicate if changes were made.
- No additional restrictions: You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

Full license text: https://creativecommons.org/licenses/by/4.0/

**Examples of attribution:**
If you use or reference the FFAD specification in research, documentation, or tools, you must provide attribution.

1. Always include the full project name: Functional Flow Artifact Diagram (FFAD) Specification
2. Credit the author(s) or organization: © 2025 [Your Name / Organization]
3. Include the license: CC BY 4.0
4. Provide a link to the official repository or spec release.
5. If adapted or modified, explicitly state: “Adapted from…”

In text:
“This work builds on the Functional Flow Artifact Diagram (FFAD) Specification © 2025 DoNew Innovations, licensed under CC BY 4.0.”

In a figure caption:
“Diagram adapted from FFAD Specification, © 2025 DoNew Innovations, CC BY 4.0.”

In academic papers:
- DoNew Innovations (2025). Functional Flow Artifact Diagram (FFAD) Specification, Version 1.0. Available at [https://github.com/go-donew/ffad](https://github.com/go-donew/ffad). Licensed under CC BY 4.0.
- [1] [DoNew Innovations], "Functional Flow Artifact Diagram (FFAD) Specification," Version 1.0, 2025. [Online]. Available: https://github.com/go-donew/ffad. Licensed under CC BY 4.0.

