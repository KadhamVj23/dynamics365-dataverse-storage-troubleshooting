
# Dataverse Storage Troubleshooting Workflow

This flowchart represents the investigation process for a simulated Dynamics 365 CE / Dataverse storage capacity issue.

```mermaid
flowchart TD
    A([Customer reports storage issue]) --> B[Collect environment details and error message]
    B --> C[Open Power Platform Admin Center]
    C --> D[Go to Licensing → Dataverse]
    D --> E[Review database, file and log capacity]
    E --> F{Which storage category has high usage?}

    F -->|Database| G[Review database-consuming tables]
    F -->|File| H[Review file-consuming tables and attachments]
    F -->|Log| I[Review log consumption and retention]

    G --> J[Identify major storage consumers]
    H --> J
    I --> J

    J --> K[Check tenant capacity and environment allocation]
    K --> L[Review the exact failed operation and error details]
    L --> M{Is insufficient capacity confirmed?}

    M -->|No| N[Investigate other possible causes]
    N --> O[Gather additional logs and escalate if required]

    M -->|Yes| P[Prepare remediation recommendations]
    P --> Q{Approved remediation option?}

    Q -->|Data cleanup| R[Obtain approval and review retention requirements]
    Q -->|Capacity allocation| S[Allocate available tenant capacity]
    Q -->|Additional capacity| T[Evaluate eligible capacity options]

    R --> U[Recheck storage consumption]
    S --> U
    T --> U

    U --> V[Validate available capacity]
    V --> W[Retry the affected environment operation]
    W --> X{Operation successful?}

    X -->|Yes| Y[Document findings and resolution]
    X -->|No| Z[Continue investigation or escalate]

    Y --> AA([Close support case])
    O --> Z
```

**Note:** This is a simulated troubleshooting workflow. Actual investigation steps and remediation depend on the customer's tenant configuration, permissions and error details.
