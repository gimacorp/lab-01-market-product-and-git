## Product Choice

Product name: Wildberries
Link to the product's website: https://www.wildberries.ru/
Short description of the product: The largest Russian international marketplace (online platform) and online store of clothing, shoes, electronics, household goods and other categories. Founded in 2004 by Tatiana Bakalchuk, it has a wide network of pick-up points with fitting rooms, which makes it convenient to try on goods before paying.
## Main components

![Wildberries Component Diagram](./diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)

Wildberries Component Diagram Code

Here are **7 components** selected from the diagram, with brief explanations of what they do:

1. **Customer Mobile App**
   This is the main client application used by customers to browse products, place orders, and track deliveries. It communicates with backend services through APIs.

2. **API Gateway Layer (Storefront Gateway)**
   This gateway acts as a single entry point for client requests, routing them to the correct backend services. It also handles concerns like authentication, rate limiting, and request aggregation.

3. **Cart & Checkout Service**
   This service manages the user’s shopping cart and the checkout flow, including adding/removing items and preparing orders for payment. It ensures pricing, discounts, and availability are applied correctly.

4. **Catalog & Search Service**
   This component is responsible for storing product information and enabling fast search and filtering. It integrates with search indexes to provide relevant product results to users.

5. **Order Management Service (OMS)**
   OMS handles the lifecycle of an order after checkout, such as order creation, status updates, and coordination with logistics. It acts as a central point for order-related business logic.

6. **Fintech & Payment Service**
   This service processes payments, refunds, and financial transactions. It integrates with external payment providers to securely complete customer payments.

7. **Warehouse Management (WMS)**
   WMS manages inventory inside warehouses, including picking, packing, and stock updates. It ensures orders are fulfilled efficiently and inventory data stays accurate across the system.

## Data flow
![Wildberries Sequence Diagram](./diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)

Group 2: “Checkout (Reservation & Payment)”
1. What happens in this group of steps

In this phase, the user confirms the purchase and starts payment.
The system creates an order, temporarily reserves inventory, and initiates the payment process (including 3-D Secure if required), ensuring stock is held while the user completes payment with the bank.

2. Components involved and how they communicate

WB Mobile App → Storefront Gateway
The mobile app sends a createOrder(cart_id, payment_method) request when the user clicks “Pay Now”. This request contains cart details and the selected payment method.

Storefront Gateway → Order (OMS)
The gateway forwards the request to the Order Management Service to initialize a new order and orchestrate the checkout process.

Order (OMS) → Inventory Service
OMS requests stock reservation for the ordered SKUs. The Inventory Service decrements available stock and returns a reservation ID with a temporary hold (e.g., 15 minutes).

Inventory Service → Data Layer (Redis / Shared DB)

3. Data exchanged

Cart ID, SKU IDs, quantities, and payment method

Stock reservation details (reservation ID, hold time)

Order status (PENDING_PAYMENT)

Payment transaction data (payment URL, 3DS redirect info)


## Deployment
![Wildberries Deployment Diagram](./diagrams/out/wildberries/architecture-deployment/Deployment%20Diagram.svg)

Client Applications (Customer Mobile App, Partner App, Web Browser)
These components are deployed on user-owned devices (smartphones and personal computers). They communicate with Wildberries infrastructure over the public internet using HTTPS / GraphQL.

Edge / Ingress Layer (Storefront, Partner, Internal Ops Gateways)
These gateways are deployed at the edge of the Wildberries global infrastructure, typically behind load balancers in the primary data center or Kubernetes ingress. They terminate TLS and route traffic to internal services.

Core Microservices (E-commerce, Logistics, Support Pods)
Services such as Cart & Checkout, OMS, Payment, WMS, and Notifications are deployed as containerized microservices inside a Kubernetes compute cluster in the Wildberries primary data center.

## Assumptions
1) I assume the Order Management Service (OMS) acts as the central orchestrator during checkout, coordinating inventory reservation, payment initiation, and order state transitions.

2) I assume the Inventory Service supports temporary stock reservations with TTL (e.g., 10–15 minutes) to prevent overselling while the user completes payment.
## Open questions

1) How are traffic spikes during major sales (e.g., flash sales or seasonal events) handled at the ingress and gateway level—auto-scaling, request shedding, or priority queues?

2) What exact caching strategies are used across Redis, CDN, and application-level caches to balance freshness and performance under very high load?