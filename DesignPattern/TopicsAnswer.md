# .NET Senior Developer / Architect Interview Answers

This file contains detailed, example-driven answers for the design pattern and architecture checklist. Each section is written for easy memorization.

---

## ✅ 1. SOLID Principles (Must Know)

### Single Responsibility Principle (SRP)
- Definition: A class should have only one reason to change.
- Example: A `UserService` should handle user business rules, while `UserRepository` handles database access.
- Why it matters: Reduces bugs, improves testability, and makes code easier to refactor.
- Memorize: "One responsibility, one reason to change."

### Open/Closed Principle (OCP)
- Definition: Software entities should be open for extension but closed for modification.
- Example: Add a new payment method by implementing `IPaymentProcessor`, not by editing existing `switch` statements.
- Why it matters: Allows new features without breaking old code.
- Memorize: "Extend behavior, don’t edit existing code."

### Liskov Substitution Principle (LSP)
- Definition: Subtypes must be usable in place of their base types without altering correctness.
- Example: `Rectangle` and `Square` should not share a `setWidth`/`setHeight` contract if `Square` breaks it.
- Why it matters: Prevents fragile inheritance and runtime surprises.
- Memorize: "Subclasses must behave like parents."

### Interface Segregation Principle (ISP)
- Definition: Clients should not be forced to depend on interfaces they do not use.
- Example: Split `IPrinter` into `IPrint`, `IScan`, `IFax` rather than one large interface.
- Why it matters: Keeps components focused and easier to mock.
- Memorize: "Small interfaces for small needs."

### Dependency Inversion Principle (DIP)
- Definition: High-level modules should not depend on low-level modules; both should depend on abstractions.
- Example: `OrderService` depends on `IOrderRepository`, not on `SqlOrderRepository`.
- Why it matters: Enables swapping implementations and easier testing.
- Memorize: "Depend on interfaces, not implementations."

### Interview Notes
- Real example of SRP violation: A `CustomerController` that is also formatting emails and saving audit logs.
- DI supports DIP by injecting abstractions like `ILogger` or `IRepository`.
- Refactor a God Class by splitting responsibilities into focused classes and interfaces.

---

## ✅ 2. GoF Design Patterns

### Singleton
- Definition: Ensure one instance exists globally.
- Example: `ConfigurationManager.Instance` or a logging wrapper.
- When to use: One shared cache, one configuration provider.
- Pitfall: Global state, hard to test, thread-safety issues.
- Memory hint: "One and only one."

### Factory Method
- Definition: Define an interface for object creation, letting subclasses decide which class to instantiate.
- Example: `CreateVehicle()` returns `Car` or `Bike` depending on type.
- Benefit: Removes `switch` statements and centralizes creation.
- Memory hint: "Factory method creates."

### Abstract Factory
- Definition: Creates families of related objects without specifying concrete classes.
- Example: `UIFactory` produces `WinButton` and `WinTextbox` or `MacButton` and `MacTextbox`.
- Use when: You need consistent sets of related objects.
- Memory hint: "Factory of factories."

### Builder
- Definition: Build a complex object step by step.
- Example: `PizzaBuilder` sets dough, sauce, cheese, toppings.
- Benefit: Fluent API and immutable end object.
- Memory hint: "Construct complex objects cleanly."

### Prototype
- Definition: Clone objects rather than create new ones from scratch.
- Example: Copy a configured `ReportTemplate` and modify only a few fields.
- Use when: Object creation is expensive.
- Memory hint: "Clone instead of build."

### Adapter
- Definition: Translate one interface into another.
- Example: Wrap a legacy payment gateway so it looks like `IPaymentProcessor`.
- Benefit: Integrates third-party code.
- Memory hint: "Adapter plugs incompatible interfaces together."

### Facade
- Definition: Provide a simplified interface over a complex subsystem.
- Example: `OrderFacade` calls inventory, shipping, billing.
- Benefit: Reduces coupling and hides complexity.
- Memory hint: "Facade hides the details."

### Decorator
- Definition: Add responsibilities to objects dynamically.
- Example: Wrap a `Stream` in `BufferedStream`, then `CryptoStream`.
- Use for: Logging, caching, authorization layers.
- Memory hint: "Decorate behavior around the object."

### Proxy
- Definition: Control access to another object.
- Example: `LazyLoadingProxy` for EF Core entity loading.
- Benefit: Adds features like caching, access control, or remote access.
- Memory hint: "Proxy stands in for a real object."

### Composite
- Definition: Treat individual objects and compositions uniformly.
- Example: A `Folder` contains files and other folders.
- Use when: Hierarchical tree structures.
- Memory hint: "Composite is leaf or branch."

### Bridge
- Definition: Separate abstraction from implementation.
- Example: `RemoteControl` and `TV` implementations.
- Benefit: Independent extension of both sides.
- Memory hint: "Bridge decouples abstraction."

### Strategy
- Definition: Define a family of algorithms and make them interchangeable.
- Example: `TaxCalculator` can use `USATaxStrategy` or `EUTaxStrategy`.
- Benefit: Choose behavior at runtime.
- Memory hint: "Strategy changes the algorithm."

### Observer
- Definition: Notify subscribers of state changes.
- Example: Event handlers invoked when an order status changes.
- Use for: Events and delegates.
- Memory hint: "Observers watch and respond."

### Mediator
- Definition: Encapsulate communication between objects.
- Example: `Mediator` coordinates UI controls.
- Modern example: MediatR in CQRS.
- Memory hint: "Mediator manages messaging."

### Command
- Definition: Encapsulate a request as an object.
- Example: `CreateOrderCommand` with `Execute()`.
- Use in: CQRS, undo/redo.
- Memory hint: "Command is an action object."

### Chain of Responsibility
- Definition: Pass requests along a chain until handled.
- Example: ASP.NET Core middleware pipeline.
- Benefit: Flexible request handling.
- Memory hint: "Request flows through handlers."

### State
- Definition: Change behavior based on internal state.
- Example: A `Payment` object behaves differently when pending, paid, or failed.
- Memory hint: "State changes behavior."

### Template Method
- Definition: Define skeleton of algorithm in base class, allow subclasses to fill steps.
- Example: `BaseReportGenerator` with `LoadData`, `Render`, `Export`.
- Memory hint: "Template defines flow."

### Visitor
- Definition: Add operations to object structure without changing classes.
- Example: Validation visitor on AST nodes.
- Use when: Operations need to vary frequently.
- Memory hint: "Visitor visits objects."

### Iterator
- Definition: Provide sequential access to a collection.
- Example: `IEnumerable` and `IEnumerator`.
- Memory hint: "Iterator walks through a collection."

### Memento
- Definition: Capture and restore object state.
- Example: Undo stack in an editor.
- Memory hint: "Memento restores state."

---

## ✅ 3. Enterprise Application Patterns

### Repository Pattern
- Definition: Encapsulates data access and exposes a collection-like interface.
- Example: `IProductRepository.GetById(id)`.
- Notes: EF Core already implements many repository concerns.
- When to use: Add a clean boundary when domain logic must stay separate from persistence.
- When not: Avoid generic repository over-abstraction if EF Core is sufficient.
- Memory hint: "Repository is a data collection gateway."

### Unit of Work
- Definition: Group changes into a single transaction.
- Example: `SaveChanges()` in EF Core commits multiple repository operations.
- Notes: EF Core `DbContext` is a Unit of Work.
- Memory hint: "Unit of Work commits one atomic transaction."

### Specification Pattern
- Definition: Encapsulate query criteria as objects.
- Example: `CustomerByStatusSpecification`.
- Benefit: Reuse filters and combine them.
- Memory hint: "Specification describes a query rule."

### Service Layer Pattern
- Definition: Organize business logic in services rather than UI/controllers.
- Example: `OrderService.PlaceOrder()`.
- Notes: Separates application orchestration from domain rules.
- Memory hint: "Service layer is business workflow."

### Domain Model Pattern
- Definition: Use rich domain objects with behavior, not just data.
- Example: `Order.AddItem()`, `Order.Cancel()`.
- Anemic model: Entities only hold data; rich model: entities own behavior.
- Memory hint: "Rich model holds logic in domain objects."

---

## ✅ 4. Dependency Injection

### Constructor Injection
- Definition: Provide dependencies via constructor parameters.
- Example: `public OrderService(IOrderRepository repo)`.
- Why: Makes dependencies explicit and immutable.
- Memory hint: "Constructor injects dependency."

### Property Injection
- Definition: Set dependencies through properties.
- Example: `public ILogger Logger { get; set; }`.
- Use when: Optional or circular dependencies.
- Memory hint: "Property is optional injection."

### Method Injection
- Definition: Pass dependencies into a method call.
- Example: `Process(order, ILogger logger)`.
- Use when: dependency only needed for one operation.
- Memory hint: "Method receives dependency."

### Service Lifetimes
- Singleton: One instance for the app.
- Scoped: One instance per request.
- Transient: New instance every time.
- Interview pitfalls: Singleton can capture scoped services and cause memory leaks. Scoped in background tasks may be wrong.

---

## ✅ 5. ASP.NET Core Internal Design Patterns

### Middleware
- Pattern: Chain of Responsibility.
- Example: Logging middleware, authentication middleware.
- Important: Order matters. Request flows top-down; response flows bottom-up.
- Memory hint: "Middleware is a request chain."

### Filters
- Authorization Filter: Check permissions before action executes.
- Action Filter: Runs before/after action execution.
- Exception Filter: Catches unhandled exceptions.
- Result Filter: Runs before/after result execution.
- Memory hint: "Filters are stage checkpoints."

### Other Topics
- Options Pattern: Bind configuration sections to typed classes.
- Hosted Services & Background Services: Long-running tasks.
- Endpoint Filters: Lightweight filters for minimal APIs.
- Minimal APIs: Simplified route handlers.

---

## ✅ 6. CQRS

### What it means
- Command: change state.
- Query: read state.
- Read Model: optimized for queries.
- Write Model: optimized for updates.
- Example: `CreateOrderCommand` updates data; `GetOrderSummaryQuery` reads data.
- When to use: complex domains, scaling read/write separately.
- When not: simple CRUD apps.
- Memory hint: "Write and read are separate concerns."

---

## ✅ 7. MediatR

### Mediator Pattern
- Definition: Decouple sender and receiver through a mediator.
- Example: `IMediator.Send(new CreateOrderCommand())`.
- Benefit: Keeps controllers thin and centralizes handlers.
- Pitfall: Overuse can turn code into a call graph with poor traceability.
- Memory hint: "MediatR is the messaging hub."

### Topics
- Commands: write-side operations.
- Queries: read-side operations.
- Notifications: publish events to multiple handlers.
- Pipeline Behaviors: cross-cutting concerns like logging, validation, and retry.

---

## ✅ 8. Domain-Driven Design (DDD)

### Building Blocks
- Entity: Identity-based object.
- Value Object: Immutable attribute object.
- Aggregate: Cluster of domain objects.
- Aggregate Root: Entry point for aggregate modifications.
- Domain Service: Business logic not belonging to an entity.
- Repository: Access aggregate roots.
- Domain Event: Something important that happened in the domain.
- Memory hint: "Entities have identity; value objects do not."

### Tactical vs Strategic
- Tactical: Entities, aggregates, events, value objects.
- Strategic: Bounded contexts, context mapping.
- Interview focus: Know aggregate boundaries and transaction boundaries.
- Memory hint: "Tactical is code, strategic is context."

---

## ✅ 9. Microservices Design Patterns

### Saga Pattern
- Choreography: services publish/subscribe events.
- Orchestration: central coordinator executes steps.
- Example: Order service emits `OrderPlaced`, then Payment service consumes it.
- Use when: distributed transactions across services.
- Memory hint: "Saga manages distributed business processes."

### Compensating Transactions
- Definition: Undo work when later steps fail.
- Example: refund payment if order shipment fails.
- Memory hint: "Compensate when commit cannot happen."

### Process Manager
- Definition: Long-running workflow coordinator.
- Use when: multi-step process spans time.
- Memory hint: "Process manager drives state transitions."

### API Gateway
- Role: single entry point, authentication, routing.
- Examples: Ocelot, YARP.
- Memory hint: "Gateway is the front door."

### Backend-for-Frontend (BFF)
- Definition: API tailored to a specific client type.
- Example: separate mobile and web APIs.
- Memory hint: "BFF optimizes API per client."

### Service Discovery
- Examples: Kubernetes DNS, Consul.
- Memory hint: "Discovery finds services at runtime."

---

## ✅ 10. Messaging Patterns

### Publish/Subscribe
- Definition: broadcast events to multiple subscribers.
- Example: `OrderCreated` event sent to inventory and notification services.
- Memory hint: "Publish once, many receive."

### Point-to-Point Queue
- Definition: one message consumed by one consumer.
- Example: task queue with worker processing.
- Memory hint: "One message, one receiver."

### Request/Reply
- Definition: caller waits for response.
- Example: payment request with confirmation response.
- Memory hint: "Message asks and gets answer."

### Competing Consumers
- Definition: multiple workers consume from the same queue.
- Example: scale background jobs.
- Memory hint: "Consumers compete for work."

### Fan-Out
- Definition: send same message to many receivers.
- Example: publish event to multiple queues.
- Memory hint: "Fan out to many."

### Event Streaming
- Definition: append events to a stream, consumers read at their own pace.
- Example: Kafka.
- Memory hint: "Stream events in order."

---

## ✅ 11. Reliability Patterns

### Transactional Outbox
- Definition: save events and database changes in one transaction.
- Example: write order row and event row in same DB transaction.
- Benefit: avoids dual-write inconsistency.
- Memory hint: "Outbox makes writes atomic."

### Inbox Pattern
- Definition: record processed messages to avoid duplicates.
- Example: ignore duplicate `OrderPaid` events.
- Memory hint: "Inbox deduplicates received messages."

### Idempotency
- Definition: repeated requests produce same result.
- Example: API with idempotency key for charge requests.
- Memory hint: "Retry safely without side effects."

### Retry Pattern
- Use: transient failures.
- Libraries: Polly, .NET resilience.
- Memory hint: "Retry, then fail gracefully."

### Circuit Breaker
- States: Open (stop calls), Closed (allow calls), Half-Open (test calls).
- Example: open circuit when remote service fails repeatedly.
- Memory hint: "Breaker protects under failure."

### Other patterns
- Bulkhead: isolate failures into compartments.
- Timeout: fail quickly when service is slow.
- Fallback: use backup behavior.
- Dead Letter Queue: store messages that cannot be processed.
- Memory hint: "Protect, isolate, recover."

---

## ✅ 12. Event-Driven Architecture

### Key concepts
- Domain Events: internal changes in the domain.
- Integration Events: published between services.
- Event Versioning: evolve event schema safely.
- Event Ordering: preserve sequence where needed.
- Event Replay: rebuild state from history.
- Eventual Consistency: data eventually converges.
- Memory hint: "Events are facts, not commands."

### Interview notes
- Exactly-once delivery is usually a myth; at-least-once is common.
- Design for idempotency and deduplication.

---

## ✅ 13. Event Sourcing

### What it is
- Store every state change as an event.
- Example: `OrderCreated`, `OrderShipped`, `OrderCancelled`.
- Replay: rebuild current state from event history.
- Snapshot: save point-in-time state to speed recovery.
- When to use: auditability, complex workflows, temporal queries.
- When not: simple CRUD systems.
- Memory hint: "Events are the source of truth."

---

## ✅ 14. Database Patterns

### EF Core
- Tracking vs NoTracking: tracking for updates, no-tracking for reads.
- Compiled Queries: faster repeated queries.
- Split Queries: avoid large joins with multiple queries.
- Lazy Loading: load related data on access.
- Eager Loading: fetch related data upfront.
- Explicit Loading: load related data manually.
- N+1 Problem: avoid repeated queries for collections.
- Indexes: speed lookups.
- Query Optimization: use projections and filters.
- Memory hint: "Choose the right loading strategy."

### Database Design
- Normalization: reduce redundancy.
- Denormalization: improve read performance.
- Partitioning: split large tables.
- Sharding: distribute data across servers.
- Memory hint: "Normalize for writes, denormalize for reads."

---

## ✅ 15. Caching Patterns

### Cache Aside
- Definition: app loads from cache first; on miss, read DB and populate cache.
- Example: `GetProduct()` checks Redis, then SQL.
- Memory hint: "Cache aside lets app manage cache."

### Other strategies
- Write Through: write cache and DB together.
- Write Behind: write cache first, persist later.
- Distributed Cache: shared cache like Redis.
- Memory hint: "Cache strategy depends on consistency needs."

### Interview note
- Invalidation is the hardest part; design TTLs or update cache after writes.

---

## ✅ 16. Concurrency Patterns

### Optimistic Concurrency
- Uses version or timestamp to detect conflicts.
- Example: `RowVersion` column in EF Core.
- Memory hint: "Assume no conflict, detect later."

### Pessimistic Locking
- Locks rows for exclusive access.
- Example: `FOR UPDATE` in SQL.
- Memory hint: "Lock first, modify safely."

### Distributed Locking
- Use Redis or ZooKeeper for locks across services.
- Example: ensure only one service processes a job.
- Memory hint: "One lock across nodes."

---

## ✅ 17. Security Architecture

### Authentication
- JWT: token-based auth.
- OAuth2: delegated authorization.
- OpenID Connect: identity on top of OAuth2.
- Memory hint: "Authentication proves who you are."

### Authorization
- Roles: coarse-grained.
- Claims: fine-grained.
- Policies: rule-based.
- Memory hint: "Authorization decides what you can do."

### Security topics
- Refresh Tokens: renew access without login.
- API Security: validate tokens and throttle.
- OWASP Top 10: injection, auth flaws, XSS, CSRF.
- Memory hint: "Protect data and trust boundaries."

---

## ✅ 18. Cloud & Azure Topics

### Azure Services
- App Service: managed web hosting.
- Functions: serverless compute.
- Service Bus: reliable messaging.
- Event Grid: event routing.
- Event Hub: high-throughput event ingestion.
- Storage Account: blobs, queues, tables.
- Key Vault: secrets and keys.
- Memory hint: "Use Azure building blocks for scale."

### Containers
- Docker: package apps.
- Kubernetes: orchestrate containers.
- Memory hint: "Containers unify deployment."

---

## ✅ 19. System Design Topics

### Common system examples
- E-Commerce: order, payment, inventory, shipping.
- Ride Booking: matching riders and drivers.
- Food Delivery: orders, restaurants, delivery status.
- Notification System: real-time and batch.
- URL Shortener: fast lookup and analytics.
- High-Traffic API: caching, throttling, autoscaling.
- Memory hint: "Think in services, data flows, and failure modes."

### Interview focus
- Scaling: vertical vs horizontal.
- Reliability: retries, fallback, redundancy.
- Fault tolerance: graceful degradation.

---

## ✅ 20. Performance & Observability

### Logging
- Use structured logging like Serilog.
- Memory hint: "Logs tell the story."

### Monitoring
- Application Insights: app telemetry.
- Prometheus/Grafana: metrics and dashboards.
- Memory hint: "Watch health and performance."

### Distributed Tracing
- OpenTelemetry: trace requests across services.
- Memory hint: "Tracing connects the call path."

---

## ✅ 21. Architecture Styles

### Monolithic Architectures
- Monolith: single deployable app.
- Modular Monolith: well-separated modules in one app.
- N-Tier: separate UI, business, data layers.
- Memory hint: "Monolith is one app, layered internally."

### Clean Architecture
- Layers: Domain, Application, Infrastructure, Presentation.
- Principle: dependencies point inward.
- Memory hint: "Core logic is independent."

### Other styles
- Onion Architecture: concentric rings around domain.
- Hexagonal Architecture: ports and adapters.
- Vertical Slice Architecture: feature-based slices.
- Memory hint: "Architecture is about boundaries and dependencies."

---

## ✅ 22. End-to-End Architecture Scenario

### Flow explanation
- Client: user or frontend sends request.
- API Gateway: accepts request, handles auth and routing.
- Microservice: business logic service.
- MediatR: dispatches command/query to handler.
- CQRS Command: updates write model.
- Domain Model: business rules and aggregates.
- Repository: persist data.
- EF Core: ORM for SQL database.
- SQL Database: durable storage.
- Outbox Event: store event for messaging.
- Kafka / Service Bus: deliver integration events.
- Saga: coordinate long-running distributed work.
- Other Services: consume events and react.
- Cache Update: update read cache.
- Read Model Update: update query-optimized data.

### Discussion points
- Why each component exists: separation of concerns and reliability.
- Request lifecycle: from client to final data and events.
- Failure handling: retries, transactions, compensation.
- Retry strategies: exponential backoff, circuit breakers.
- Eventual consistency: acceptable delay between write and read.
- Scaling approach: scale services independently.
- Monitoring and tracing: visibility across components.
- Trade-offs: complexity vs flexibility, consistency vs scalability.

---

## Memorization Tips
- Use acronyms: SOLID, CQRS, DDD.
- Pair pattern names with concrete examples.
- Remember one strong use case per pattern.
- Keep the problem and solution in one sentence.
- Link architecture flow to a real system: order placement, payment, and shipping.
