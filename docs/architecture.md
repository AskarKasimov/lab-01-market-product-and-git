#### `## Product Choice`

Provide:

- Yandex Go
- [Link to the product's website](https://taxi.yandex.ru/ru_ru/)
- Service for ordering taxi all over the world

#### `## Main components`

1. Component Architecture

   <details><summary>Rendered image (click to open)</summary>

   ![Yandex Go Component Diagram](../docs/diagrams/out/yandex-go/architecture-component/Component%20Diagram.svg)

   </details>

1. [Yandex Go Component Diagram Code](../docs/diagrams/src/yandex-go/architecture-component.puml)

1. Components of the product from the component diagram:
    1. Mobile App - made for both iOS & Android to provide suitable interface to order taxi, cargo, eats, etc.
    1. Web App - made for all relevant Web Browsers to make possible ordering taxi etc. online without a mobile phone or a will to install native app.
    1. API Gateway - back-end entrypoint to access all other services.
    1. Yandex Pay - external service for paying bills.
    1. Yandex Maps - external service for reusing famous yandex's maps.

#### `## Data flow`

1. Sequence Diagram

   <details><summary>Rendered image (click to open)</summary>

   ![Yandex Go Sequence Diagram](../docs/diagrams/out/yandex-go/architecture-sequence/Sequence%20Diagram.svg)

   </details>
1. [Yandex Go Sequence Diagram Code](../docs/diagrams/src/yandex-go/architecture-sequence.puml)

1. Group of actions: Price Estimation
    1. User enters destination
    1. API Gateway calls Maps&Pricing service
    1. It fetches route & traffic from external Maps API
    1. It fetches tariff rules from Operational DB
    1. It checks surge from State Cache
    1. Sends info about route & price to user

#### `## Deployment`

1. Deployment Diagram

   <details><summary>Rendered image (click to open)</summary>

   ![Yandex Go Deployment Diagram](../docs/diagrams/out/yandex-go/architecture-deployment/Deployment%20Diagram.svg)

   </details>
2. [Yandex Go Deployment Diagram Code](../docs/diagrams/src/yandex-go/architecture-deployment.puml)
3. All of the server services are deployed on Yandex Cloud Infrastracture

#### `## Assumptions`

- I assume gRPC is used between API Gateway and services because of better perfomance & contract system comparing to HTTP
- I assume Kubernetes is used for its suitable pod horizontal scaling

#### `## Open questions`

- How is the surge exactly counted?
- How the infrastructure look like in different countries? Does Yandex Go have several data-centers across the world or only in Russia?
