# AI-DLC Workflow Dependencies

Stage dependency graph. Solid arrows = always flows. Dashed arrows = conditional flows.

```mermaid
flowchart TD
    Start(["User Request"])

    subgraph INCEPTION["INCEPTION PHASE"]
        WD["Workspace Detection"]
        RE["Reverse Engineering"]
        RA["Requirements Analysis"]
        Stories["User Stories"]
        WP["Workflow Planning"]
        AppDesign["Application Design"]
        UnitsG["Units Generation"]
    end

    subgraph CONSTRUCTION["CONSTRUCTION PHASE"]
        FD["Functional Design"]
        NFRA["NFR Requirements"]
        NFRD["NFR Design"]
        ID["Infrastructure Design"]
        CG["Code Generation"]
        BT["Build and Test"]
    end

    subgraph OPERATIONS["OPERATIONS PHASE"]
        OPS["Operations"]
    end

    Start --> WD
    WD -.-> RE
    WD --> RA
    RE --> RA
    RA -.-> Stories
    RA --> WP
    Stories --> WP
    WP -.-> AppDesign
    WP -.-> UnitsG
    AppDesign -.-> UnitsG
    UnitsG --> FD
    FD -.-> NFRA
    NFRA -.-> NFRD
    NFRD -.-> ID
    WP --> CG
    FD --> CG
    NFRA --> CG
    NFRD --> CG
    ID --> CG
    CG -.->|Next Unit| FD
    CG --> BT
    BT -.-> OPS
    BT --> End(["Complete"])
```

## User's Role

- Answer questions in dedicated files using `[Answer]:` tags with letter choices
- Review and approve each stage's completion message before proceeding
- Option X (Other) is always available for custom responses
