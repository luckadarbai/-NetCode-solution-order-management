```mermaid
flowchart LR

%% Clients
A[Web Client (Customers)] --> G[API Gateway]
B[Admin UI (Internal Staff)] --> G

%% Gateway to services
G --> U[User Service]
G --> O[Order Service]
G --> N[Notification Service]
G --> R[Reporting Service]

%% IAM
U <--> |OAuth2/JWT| K[Identity Provider (Keycloak)]

%% Order events
O --> E[(Event Bus)]
E --> N
E --> R

%% Databases
U --> UDB[(User DB)]
O --> ODB[(Order DB)]
N --> NDB[(Notification DB)]
R --> RDB[(Reporting DB)]
