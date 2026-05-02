# Simple Web Stack

## Diagram
```mermaid
graph TD
    USER[User] --> BROWSER[Browser]
    BROWSER --> DNS[DNS: foobar.com]
    DNS --> SERVER[Server 8.8.8.8]

    subgraph SERVER_STACK [Single Server]
        NGINX[Nginx Web Server]
        APP[Application Server]
        CODE[Application Files / Code Base]
        DB[(MySQL Database)]

        SERVER --> NGINX
        NGINX --> APP
        APP --> CODE
        APP --> DB
    end

    APP --> RESPONSE[HTTP Response]
    RESPONSE --> USER
Explanation
	•	One domain name foobar.com with www A record pointing to 8.8.8.8
	•	Nginx handles HTTP requests
	•	Application server processes logic
	•	MySQL stores data
Issues
	•	Single Point of Failure
	•	Downtime during maintenance
	•	Cannot scale efficiently
---

