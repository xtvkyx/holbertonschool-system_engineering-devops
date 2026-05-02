```md
# Distributed Web Infrastructure

## Diagram

```mermaid
graph TD
    USER[User] --> BROWSER[Browser]
    BROWSER --> DNS[DNS]
    DNS --> LB[HAProxy Load Balancer]

    LB --> S1N[Nginx Server 1]
    LB --> S2N[Nginx Server 2]

    subgraph SERVER1 [Server 1]
        S1N --> S1A[Application Server 1]
        S1A --> S1C[Application Files]
        S1A --> DBP[(MySQL Primary)]
    end

    subgraph SERVER2 [Server 2]
        S2N --> S2A[Application Server 2]
        S2A --> S2C[Application Files]
        S2A --> DBR[(MySQL Replica)]
    end

    DBP -. Replication .-> DBR
