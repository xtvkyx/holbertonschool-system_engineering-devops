# Secured and Monitored Web Infrastructure

## Diagram
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

* Firewalls secure network layers
* SSL enables HTTPS encryption
* Monitoring tracks performance and health
* Replication improves database reliability
* Security and observability are enhanced

## Issues

* SSL termination at load balancer can be risky
* Primary DB remains writable SPOF
* Monitoring consumes resources
* More infrastructure complexity

