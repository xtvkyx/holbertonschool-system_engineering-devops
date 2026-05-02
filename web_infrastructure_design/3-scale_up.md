
---
### `3-scale_up.md`

# Scale Up Infrastructure

## Diagram

```mermaid

graph TD
    USER[User] --> DNS[DNS]
    DNS --> LB[HAProxy Cluster]

    LB --> LB1[HAProxy Load Balancer 1]
    LB --> LB2[HAProxy Load Balancer 2]

    LB1 <--> LB2

    LB1 --> WEB1[Nginx Web Server 1]
    LB2 --> WEB2[Nginx Web Server 2]

    WEB1 --> APP1[Application Server 1]
    WEB2 --> APP2[Application Server 2]

    APP1 --> DB[Dedicated MySQL Database Server]
    APP2 --> DB
```
## Explanation

* Two clustered load balancers improve redundancy
* Separate web tier handles HTTP traffic
* Separate app tier handles business logic
* Dedicated database tier improves performance
* Infrastructure supports scaling by tier

## Benefits

* High availability
* Better scalability
* Easier maintenance
* Improved security
* Tier isolation
