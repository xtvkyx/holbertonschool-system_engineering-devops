# Simple Web Stack

## Diagram

```mermaid
graph TD
    USER[User] --> BROWSER[Browser]
    BROWSER --> DNS[DNS www.foobar.com]
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
