# .NET Senior Developer / Architect Interview Preparation Checklist

## ✅ 1. SOLID Principles (Must Know)

### Principles
- Single Responsibility Principle (SRP)
- Open Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP)
- Dependency Inversion Principle (DIP)

### Interview Questions
- Real examples where SRP was violated
- How Dependency Injection supports DIP
- Refactoring a God Class using SOLID principles

## ✅ 2. GoF Design Patterns

### Creational Patterns
- Singleton
  - Singleton Pattern
  - Thread Safety
  - Lazy Initialization
  - Singleton vs DI Singleton
- Factory Method
  - Runtime Object Creation
  - Eliminating Switch Statements
- Abstract Factory
  - Family of Related Objects
- Builder
  - Complex Object Creation
  - Fluent Builder Pattern
- Prototype
  - Shallow Copy
  - Deep Copy

### Structural Patterns
- Adapter
  - Third-Party Integrations
- Facade
  - Simplifying Complex Subsystems
- Decorator
  - Logging
  - Caching
  - Authorization
- Proxy
  - Lazy Loading
  - EF Core Proxies
- Composite
  - Tree Structures
- Bridge
  - Decoupling Abstraction and Implementation

### Behavioral Patterns
- Strategy
  - Runtime Algorithm Selection
- Observer
  - Events and Delegates
- Mediator
  - MediatR
- Command
  - CQRS Commands
- Chain of Responsibility
  - ASP.NET Core Middleware
- State
  - Workflow Engines
- Template Method
  - Common Process Flows
- Visitor
  - Rare but Occasionally Asked
- Iterator
  - IEnumerable
  - IEnumerator
- Memento
  - Undo Functionality

## ✅ 3. Enterprise Application Patterns

- Repository Pattern
  - Repository Pattern

### Interview Questions
- Do we still need Repository with EF Core?
- Generic Repository: Pros & Cons

- Unit of Work
  - Unit of Work Pattern

### Interview Questions
- How EF Core implements Unit of Work

- Specification Pattern
  - Specification Pattern

### Interview Questions
- Dynamic Filtering
- Complex Querying

- Service Layer Pattern
  - Service Layer Pattern

### Interview Questions
- Domain Services vs Application Services

- Domain Model Pattern
  - Rich Domain Model
  - Anemic Domain Model

### Interview Questions
- Rich Domain Model vs Anemic Model

## ✅ 4. Dependency Injection

### Topics
- Constructor Injection
- Property Injection
- Method Injection

### Service Lifetimes
- Singleton
- Scoped
- Transient

### Interview Questions
- Memory Leaks with Singleton
- Captive Dependency Problem
- Circular Dependency

## ✅ 5. ASP.NET Core Internal Design Patterns

### Middleware
- Chain of Responsibility Pattern

### Filters
- Authorization Filter
- Action Filter
- Exception Filter
- Result Filter

### Other Topics
- Options Pattern
- Hosted Services
- Background Services
- Endpoint Filters (.NET 8+)
- Minimal APIs

### Interview Questions
- Request Pipeline
- Middleware Ordering

## ✅ 6. CQRS

### Topics
- Command
- Query
- Read Model
- Write Model

### Interview Questions
- CQRS vs CRUD
- When NOT to Use CQRS

## ✅ 7. MediatR

### Pattern
- Mediator Pattern

### Topics
- Commands
- Queries
- Notifications
- Pipeline Behaviors

### Interview Questions
- Pros and Cons
- Overuse Scenarios

## ✅ 8. Domain-Driven Design (DDD)

### Building Blocks
- Entity
- Value Object
- Aggregate
- Aggregate Root
- Domain Service
- Repository
- Domain Event

### Tactical DDD

### Interview Questions
- Aggregate Boundaries
- Transaction Boundaries

### Strategic DDD

### Interview Questions
- Bounded Context
- Context Mapping

## ✅ 9. Microservices Design Patterns

### Saga Pattern
- Choreography
  - Event → Event → Event Flow
- Orchestration
  - Central Coordinator

### Interview Questions
- Advantages & Disadvantages

### Compensating Transactions
- Rollback Logic Across Services

### Process Manager
- Long-Running Workflows

### API Gateway
- Examples
  - Ocelot
  - YARP

### Backend for Frontend (BFF)
- BFF Pattern

### Interview Questions
- Mobile API vs Web API

### Service Discovery
- Examples
  - Kubernetes
  - Consul

## ✅ 10. Messaging Patterns

- Publish/Subscribe
- Point-to-Point Queue
- Request/Reply
- Competing Consumers
- Fan-Out
- Event Streaming

### Interview Focus
- Kafka Concepts & Use Cases

## ✅ 11. Reliability Patterns

- Transactional Outbox
  - Prevent Dual Writes
- Inbox Pattern
  - Prevent Duplicate Processing
- Idempotency

### Interview Questions
- Handling Duplicate Messages

- Retry Pattern
  - Libraries
    - Polly
    - .NET Resilience

- Circuit Breaker
  - States
    - Open
    - Closed
    - Half-Open

### Other Reliability Patterns
- Bulkhead Pattern
- Timeout Pattern
- Fallback Pattern
- Dead Letter Queue (DLQ)

### Interview Questions
- DLQ Processing

## ✅ 12. Event-Driven Architecture

### Topics
- Domain Events
- Integration Events
- Event Versioning
- Event Ordering
- Event Replay
- Eventual Consistency

### Interview Questions
- Exactly-Once Delivery Myth
- At-Least-Once Delivery

## ✅ 13. Event Sourcing

### Topics
- Event Store
- Replay
- Snapshots

### Interview Questions
- Event Sourcing vs CRUD
- Event Sourcing + CQRS

## ✅ 14. Database Patterns

### EF Core
- Tracking vs NoTracking
- Compiled Queries
- Split Queries
- Lazy Loading
- Eager Loading
- Explicit Loading
- N+1 Problem
- Indexes
- Query Optimization

### Database Design
- Normalization
- Denormalization
- Partitioning
- Sharding

### Interview Questions
- Horizontal Scaling

## ✅ 15. Caching Patterns

- Cache Aside (Most Common)
  - Read Cache
  - Cache Miss
  - Read Database
  - Update Cache

### Other Caching Strategies
- Write Through
- Write Behind
- Distributed Cache

### Examples
- Redis

### Interview Questions
- Cache Invalidation

## ✅ 16. Concurrency Patterns

### Topics
- Optimistic Concurrency
- RowVersion
- Timestamp
- Pessimistic Locking
- Distributed Locking

### Examples
- Redis Locks

## ✅ 17. Security Architecture

### Authentication
- JWT
- OAuth2
- OpenID Connect

### Authorization
- Roles
- Claims
- Policies

### Security Topics
- Refresh Tokens
- API Security
- OWASP Top 10
- CSRF
- XSS
- SQL Injection

## ✅ 18. Cloud & Azure Topics

### Azure Services
- Azure App Service
- Azure Functions
- Azure Service Bus
- Event Grid
- Event Hub
- Storage Account
- Key Vault

### Containers
- Docker
- Kubernetes

### Interview Questions
- Scaling Microservices

## ✅ 19. System Design Topics

### Design These Systems
- E-Commerce System
  - Order
  - Payment
  - Inventory
  - Shipping
- Ride Booking System
- Food Delivery System
- Notification System
- URL Shortener
- High-Traffic API

### Interview Questions
- Scaling
- Reliability
- Fault Tolerance

## ✅ 20. Performance & Observability

### Logging
- Serilog

### Monitoring
- Application Insights
- Prometheus
- Grafana

### Distributed Tracing
- OpenTelemetry

### Interview Questions
- Trace Requests Across Microservices

## ✅ 21. Architecture Styles

### Monolithic Architectures
- Monolith
- Modular Monolith
- N-Tier Architecture

### Clean Architecture (Most Asked)
- Layers
  - Domain
  - Application
  - Infrastructure
  - Presentation

### Other Architecture Styles
- Onion Architecture
- Hexagonal Architecture
- Vertical Slice Architecture

## ✅ 22. End-to-End Architecture Scenario

Be able to confidently explain this flow:

Client
↓
API Gateway
↓
Microservice
↓
MediatR
↓
CQRS Command
↓
Domain Model
↓
Repository
↓
EF Core
↓
SQL Database
↓
Outbox Event
↓
Kafka / Service Bus
↓
Saga
↓
Other Services
↓
Cache Update
↓
Read Model Update

### Be Ready To Discuss
- Why each component exists
- Request lifecycle
- Failure handling
- Retry strategies
- Eventual consistency
- Scaling approach
- Monitoring and tracing
- Trade-offs and alternatives

## 🎯 High-Priority Topics (Most Likely to Differentiate Senior Candidates)

### Master These Thoroughly
- DDD (Tactical & Strategic)
- CQRS
- MediatR
- Saga Pattern
- Outbox & Inbox Patterns
- Messaging Reliability
- Event-Driven Architecture
- Event Sourcing
- Clean Architecture
- Performance Tuning
- Distributed Systems Trade-Offs
- Microservices Design
- Security Architecture
- Observability & OpenTelemetry

### Goal
Be able to explain each topic with:
- Definition
- Real project example
- Advantages
- Disadvantages
- When to use it
- When NOT to use it
- Common interview pitfalls
- Related patterns and trade-offs
