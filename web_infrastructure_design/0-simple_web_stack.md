# Simple Web Stack

## Diagram

```mermaid
graph TD
    USER[User] --> BROWSER[Browser]
    BROWSER --> DNS[DNS www.foobar.com]
    DNS --> SERVER[Server 8.8.8.8]

    subgraph SERVER_STACK [Single Server]
        SERVER --> NGINX[Nginx Web Server]
        NGINX --> APP[Application Server]
        APP --> CODE[Application Files / Code Base]
        APP --> DB[(MySQL Database)]
    end

    APP --> RESPONSE[HTTP Response]
    RESPONSE --> USER
```
## Explanation

* One domain name (foobar.com) points to the server IP
* Nginx handles HTTP requests
* Application server processes logic
* MySQL stores application data
* Single server hosts all components

## Issues

* Single Point of Failure (SPOF)
* Downtime during maintenance
* Cannot scale easily
* Security limitations
