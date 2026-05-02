```md
# Secured and Monitored Web Infrastructure

## Diagram
```mermaid
graph TD
    USER[User] --> HTTPS[HTTPS]
    HTTPS --> DNS[DNS]
    DNS --> FW1[Firewall]
    FW1 --> LB[HAProxy Load Balancer + SSL]

    LB --> FW2[Firewall]
    LB --> FW3[Firewall]

    subgraph SERVER1 [Primary Server]
        FW2 --> N1[Nginx]
        N1 --> A1[Application]
        A1 --> DBP[(MySQL Primary)]
        A1 --> M1[Monitoring Client]
    end

    subgraph SERVER2 [Replica Server]
        FW3 --> N2[Nginx]
        N2 --> A2[Application]
        A2 --> DBR[(MySQL Replica)]
        A2 --> M2[Monitoring Client]
    end

    LB --> MLB[Monitoring Client]
    DBP -. Replication .-> DBR

    M1 --> MON[Monitoring Service]
    M2 --> MON
    MLB --> MON
Explanation
	•	Firewalls secure traffic
	•	SSL certificate enables HTTPS
	•	Monitoring tracks logs, health, and QPS
Issues
	•	SSL termination risk
	•	Single writable DB
	•	Resource contention
---
