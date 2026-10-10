# Visual map

Read the pictures first. Open a leaf only when a phase needs it.

## Which track

```mermaid
flowchart TB
  Q{What did the user ask?}
  Q -->|make me an app / screens / mockup / feel| S[Track S · design-studio]
  Q -->|existing CRM / web / shared DB| P[Track P · M0-M10]
  Q -->|existing system + new look| B[Track BOTH]
  S --> DNA[Feeling + DNA Card]
  B --> DNA
  P --> DNA
  DNA --> OUT[Unique UI + system]
```

## Who talks to what

```mermaid
flowchart LR
  subgraph People
    STAFF[Store staff]
    HQ[Head office]
  end
  subgraph Clients
    WEB[Web app]
    IOS[iOS]
    AND[Android]
  end
  subgraph System
    API[Existing backend]
    DB[(Existing database)]
  end
  STAFF --> IOS
  STAFF --> AND
  STAFF --> WEB
  HQ --> WEB
  HQ --> IOS
  IOS --> API
  AND --> API
  WEB --> API
  API --> DB
```

## Agent session

```mermaid
sequenceDiagram
  participant U as User
  participant A as Any AI agent
  participant S as SKILL_ROOT
  participant W as WORKSPACE
  U->>A: Follow Monzer
  A->>S: Read SKILL.md
  A->>A: Print SKILL_ROOT and WORKSPACE
  A->>W: Create docs/PROGRESS.md
  loop M0 to M10
    A->>S: Load only the leaf this phase needs
    A->>W: Write docs + app code
    A->>W: Mark the PROGRESS row DONE
  end
  A->>U: HANDOVER.md
```

## Phase → leaf

```mermaid
flowchart TB
  M0[M0 Discover] --> M1[M1 Journeys]
  M1 --> M2[M2 Design]
  M2 --> M3[M3 Architecture]
  M3 --> M4[M4 Features]
  M4 --> M5[M5 Backend]
  M5 --> M6[M6 Security]
  M6 --> M7[M7 Tests]
  M7 --> M8[M8 Perf]
  M8 --> M9[M9 Release]
  M9 --> M10[M10 Demo]
  M1 -.-> MD[skills/mobile-design]
  M2 -.-> FD[skills/frontend-design]
  M2 -.-> DS[skills/expo-design-system]
  M3 -.-> DF[skills/expo-data-fetching]
  M7 -.-> T[skills/react-native-testing]
  M7 -.-> Q[skills/quality]
  M10 -.-> Q
  M8 -.-> P[skills/react-native-best-practices]
  M9 -.-> EAS[skills/eas-app-stores]
```

## Where files go

```mermaid
flowchart LR
  subgraph Skill folder
    SKILL[SKILL.md]
    LEAVES[skills/*]
    TPL[references/*]
  end
  subgraph Product repo
    DOCS[docs/*.md]
    APP[src app code]
  end
  SKILL -->|read| LEAVES
  SKILL -->|copy templates| DOCS
  SKILL -->|build| APP
```

## Who is credited

```mermaid
flowchart LR
  M[Monzer · author]
  C[Cursor · contributor]
  A[Claude · Codex · Copilot · Windsurf]
  M --> SKILL[SKILL.md]
  C --> SKILL
  A --> SKILL
```

Posters live in [images/](images/). Full names: [CONTRIBUTORS.md](../CONTRIBUTORS.md).
