```mermaid
flowchart LR

flowchart LR

A[Web Client (Customers)] --> G[API Gateway]
B[Admin UI (Internal Staff)] --> G

G --> U[User Service]
G --> O[Order Service]
G --> N[Notification Service]
G --> R[Reporting Service]

U <--> K[Identity Provider (Keycloak)]
U -. OAuth2/JWT .- K

O --> E((Event Bus))
E --> N
E --> R

U --> UDB[(User DB)]
O --> ODB[(Order DB)]
N --> NDB[(Notification DB)]
R --> RDB[(Reporting DB)]
