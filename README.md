# 1. C# Language Fundamentals

## const vs readonly
- const: compile-time constant, must be assigned with literal or const expression.
- readonly: runtime constant; can be assigned in constructor.

## Common C# keywords (sealed, protected, internal, etc):

- sealed: prevents inheritance (sealed class) or prevents overriding (sealed override).
- protected: accessible within the class and derived classes.
- internal: accessible within the same assembly.
- protected internal: accessible via either protected OR internal.
- private protected: accessible via protected AND internal (same assembly + subclass).
- with: used for record non-destructive mutation.
- virtual, override, abstract: method polymorphism.
- static: belongs to the type, not instance.

## Value vs Reference types:

- Value types stored on stack; reference types on heap (conceptually).
- Copy semantics: value types copy data, reference types copy references.
- Structs are value types; classes are reference types.
- Immutable vs mutable behaviors.
- Passing by value vs by reference (ref, out, in).

## Type casting (is, as, implicit, explicit)

- is: type checking, pattern matching (x is MyType t).
- as: safe cast returning null instead of exception.
- Implicit: safe widening conversions.
- Explicit: narrowing conversions, may throw exceptions.
- Custom casting operators (implicit operator, explicit operator).

## Nullable types:

- Nullable<T> / T? for value types.
- Null-coalescing operator: ??, ??=.
- Null-conditional operator: ?..
- Nullable reference types (NRTs): string?, #nullable enable.

## Strings, StringBuilder:

- Strings are immutable.
- Common operations: interpolation, formatting, comparison.
- String interning.
- StringBuilder for performance in heavy concatenation.

## Collections & Generics

- Generic collections: List, Dictionary, HashSet, Queue, Stack.
- ObservableCollection, ConcurrentBag, ConcurrentDictionary.
- IEnumerable vs IQueryable.
- Constraints: where T : class, new(), etc.

## Enums, Structs, Tuples:

- Enums: underlying types, flags enum.
- Structs: lightweight, no inheritance, must avoid heavy logic.
- Tuples: ValueTuple, deconstruction, named members.

## Namespaces & Assemblies:

- Namespaces for organization.
- Assemblies: .dll, .exe; metadata, manifest.
- Using directives, global using.

## Dynamic & var:

- var: compile-time type inference.
- dynamic: runtime binding, possible exceptions.
- COM interop / JSON deserialization scenarios.

## Record types:

- Immutability, with expressions, value-based equality.

## Pattern matching:

- Type patterns, property patterns, switch expressions.

# 2. Object-Oriented Programming (OOP)

## Encapsulation:

- Access modifiers: private, protected, internal, public.
- Getters/setters; auto-properties; backing fields.

## Abstraction:

- Abstract classes, interfaces.
- Hiding implementation details.

## Inheritance:

- Base/derived classes, virtual/override.
- Sealed classes/methods.
- Constructor chaining.

## Polymorphism:

- Runtime polymorphism: virtual methods.
- Compile-time polymorphism: overloading.
- Interface-based polymorphism.

## Interfaces vs Abstract classes:

- Multiple interface inheritance vs single base class.
- When to choose which.
- Default interface methods.

## Method Overloading & Overriding:

- Overloading: same name, different signatures.
- Overriding: virtual, override, sealed override.
- Shadowing: new keyword.

## Interface vs Abstract class:

- Interface: only contracts; no fields; supports multiple inheritance; default interface methods allowed.
- Abstract class: can contain fields, constructors, shared code, non-abstract methods.
- Use interfaces for capabilities; abstract classes for shared base behavior.

## Inheritance vs Composition:

- Inheritance: “is-a” relationship, reuse via subclassing.
- Composition: “has-a” relationship, reuse by containing other objects.
- Prefer composition when possible to reduce coupling.

## Class, Struct, and Record:

- class: reference type, supports inheritance.
- struct: value type, lightweight, no inheritance except interfaces.
- record / record class: reference type with built-in value equality.
- record struct: value type with value equality.
- Great for immutable data.

## Static constructor:

- Executes once per type, before first use.
- Cannot have parameters.
- Used to initialize static fields

# 3. Advanced C# Concepts

## Delegates & Events:

- Delegate types, multicast delegates.
- Events: publisher/subscriber model.
- EventHandler, EventArgs.

## Lambda Expressions:

- Syntax variations.
- Capture rules (closures).
- Expression-bodied members.

## Func, Action, Predicate:

- Func: returns value.
- Action: no return value.
- Predicate: returns bool.
- Common LINQ usage.

## LINQ (method + query syntax):

- Select, Where, GroupBy, Join, OrderBy.
- Deferred execution vs immediate execution.
- IQueryable vs IEnumerable.
- Projection and anonymous types.

## Extension methods:

- Static class + static method + this keyword.
- Best practices—don’t overuse.

## Reflection

- Getting types, properties, attributes at runtime.
- Activator.CreateInstance.
- Performance considerations.

## Iterators & yield:

- yield return, yield break.
- State machine compilation.

## Attributes

- Applying/custom attributes.
- Reading via reflection.

## Span<T>, Memory<T>:

- Stack-allocated slices.
- High-performance memory access.
- Avoiding allocations (e.g., Span<byte>).

# 4. Memory Management

## Stack vs Heap:

- Value vs reference storage.
- Execution context stack frames.
- Large object heap (LOH).

## Garbage Collector:

- Automatic memory management; frees unreachable objects
- Generations (0,1,2).
- Finalization queue.
- Server vs workstation GC.
- Forced GC: GC.Collect() (discouraged).
- Finalizers: ~ClassName(); used for unmanaged cleanup.
- IDisposable used for deterministic resource cleanup.

## IDisposable & using:

- Deterministic cleanup.
- IAsyncDisposable and await using.

## Boxing & Unboxing:

- Value type → object → value type.
- Performance cost and memory.

## Memory leaks (event handlers, static refs):

- Unsubscribed event handlers.
- Static collections holding references.
- Captured closures.

# 5. Exception Handling

## try / catch / finally:

- Multiple catch blocks.
- Catching base vs derived exceptions.
- Finally always executes.

## Custom exceptions:

- Derive from Exception.
- Add meaningful context.

## throw vs throw ex:

- throw preserves stack trace.
- throw ex resets stack trace.

## Global exception handling:

- ASP.NET Core: UseExceptionHandler, middleware.
- Unhandled exception handlers (AppDomain, TaskScheduler).

# 6. Multithreading & Asynchronous Programming

## async / await:

- State machine rewriting.
- Avoid blocking calls (.Result, .Wait()).
- ConfigureAwait.

## Task vs Thread vs ValueTask:

- Task: higher-level abstraction.
- Thread: low-level OS thread.
- ValueTask: reduces allocations.

## Multiple async tasks at onc

- Task.WhenAll

## TPL (Task Parallel Library):

- Task.Run, continuations.
- Parallel loops (Parallel.For / ForEach).

## Deadlocks & race conditions:

- UI context deadlock.
- Shared state modification.

## CancellationToken:

- Cooperative cancellation.
- Linked tokens.
- Throwing OperationCanceledException.

## Parallel LINQ (PLINQ):

- Parallel execution via .AsParallel().
- Degree of parallelism.

## Locking (Monitor, Mutex, SemaphoreSlim):

- lock keyword (Monitor).
- Mutex for cross-process locks.
- ReaderWriterLockSlim.
- Semaphore vs SemaphoreSlim.

# 7. ASP.NET Core

## Middleware:

- Request/response pipeline.
- Ordering is crucial—executed top to bottom.
- Use, UseWhen, Map, MapWhen.
- Short-circuiting the pipeline.
- Decorator-like behavior: middleware wraps the next component.

## Routing (attribute & conventional):

- MapControllerRoute, MapDefaultControllerRoute.
- Attribute routing with constraints.
- Endpoint routing pipeline.
- Route precedence & template matching.

## Controllers & Action Results:

- IActionResult, ActionResult<T>.
- Built-in results: JsonResult, FileResult, StatusCodeResult.
- FromBody, FromRoute, FromQuery binding.
- ControllerBase vs Controller.

## Filters

- Types: Authorization, Resource, Action, Exception, Result filters.
- Execution pipeline (pre → action → post).
- Filter order & dependencies.
- Decorator-style layering of cross-cutting concerns.

## Model binding & validation:

- Built-in binders: simple types, complex objects, collections.
- Validation attributes (DataAnnotations).
- Custom model binders.
- ModelState and automatic 400 responses.

## Minimal APIs:

- MapGet, MapPost, MapPut, etc.
- Typed results & parameter binding.
- Filters in minimal APIs.
- Custom endpoint conventions.

## REST principles

- Statelessness, resource representation.
- Proper HTTP verb usage.
- Idempotency and safety.
- Pagination, sorting, filtering patterns.

## Swagger / OpenAPI

- Swagger UI configuration.
- XML comments for method documentation.
- Grouping endpoints by version.
- Request/response examples.


## Dependency Injection (Built-in DI Container)

- Constructor injection.
- Lifetimes: Singleton, Scoped, Transient.
- Options pattern (IOptions, IOptionsSnapshot, IOptionsMonitor).
- Registering services, factories, HttpClient, typed clients.

## Decorator Pattern in ASP.NET Core

- Middleware as decorators (wrapping RequestDelegate).
- Filters as decorators on controller actions.
- HttpClient handler pipeline:
- - DelegatingHandler for retry, logging, caching.
- - Typed clients + custom handlers.
- DI decorator pattern using Scrutor or manual registration.

## HttpClient & DelegatingHandlers:

- Typed and named HttpClient.
- Retry, timeout, and fallback policies.
- Polly integration for resilience.
- Message handler pipeline (decorator chain).

## gRPC:

- gRPC services for high-performance binary communication.
- Unary, streaming, bidirectional calls.
- Protobuf contracts.

## SignalR

- Real-time messaging.
- Hubs and strongly typed hub clients.
- Scaling with Redis backplane.

## Hosted Services & Background Tasks:

- IHostedService, BackgroundService.
- Long-running tasks.
- Timer services.
- Queue-based background workers.

## File Uploads & Downloads

- Streaming upload.
- Large file handling.
- Range responses for downloads.

## Health Checks

- liveness vs readiness probes.
- Custom health checks.
- HealthCheck UI integration.

## Globalization & Localization:

- Resource files (.resx).
- Culture providers.
- Localization middleware.

## Rate Limiting Middleware

- Fixed window, sliding window.
- Per-user / per-IP limits.
- Named policy configuration.

## Security: 

### Authentication & Authorization:

- Cookie auth, JWT auth.
- Policy-based authorization.
- Role and claims-based access.

### JWT:

- Token validation parameters.
- Signing credentials & lifetime.
- Access vs refresh tokens.

### Cookies:

- HttpOnly, Secure, SameSite.
- Cookie policy middleware.

### Identity:

- User store, role store.
- Token providers (confirmation, reset).
- Customizing password & lockout policies.

### CORS:

- Preflight vs simple requests.
- AllowOrigin, AllowHeaders, AllowMethods.
- Per-endpoint CORS policies.

## Caching:

- In-memory, distributed (Redis), response caching.
- Cache invalidation strategies.
- Output caching (ASP.NET Core 7+).

## Logging:

- ILogger<T>.
- Log levels and filtering.
- Structured logging (Serilog, Seq, App Insights).
- Logging scopes & correlation IDs.

## Configuration providers:

- appsettings.json hierarchy.
- Environment-specific config.
- Azure Key Vault, secrets manager.
- Custom providers.

# 8. Entity Framework Core

## Code-first

- Fluent API vs DataAnnotations.
- DbSet, DbContext.
- Configurations via IEntityTypeConfiguration<T>.
- Value converters & value objects.
- Backing fields.

## Migrations

- Add-Migration, Update-Database.
- Up/Down methods.
- Seeding (HasData).
- Handling migration conflicts.
- Generating SQL scripts from migrations.
- Applying migrations at runtime

## LINQ queries

- Translation to SQL & client-evaluation rules.
- Tracking vs NoTracking queries (AsNoTracking).
- Compiled queries.
- IQueryable vs IEnumerable.
- Projection best practices (selecting DTOs).
- Filtered include (Include(p => p.Items.Where(...))).
- Pagination (Skip/Take) and pitfalls.

## Relationships & navigation properties

- One-to-many, many-to-many.
- Shadow properties.
- Foreign key conventions.
- Join tables for many-to-many relationships.
- Optional vs required relationships.
- Owned entities & owned collections.

## Eager loading

- Include / ThenInclude.
- Filtered Include (Include(x => x.Items.Where(...))).
- Multiple Includes.
- Single Query vs Split Query (EF Core 5+): AsSingleQuery(), AsSplitQuery() and Handling cartesian explosion.

## Lazy loading

- Lazy loading proxies.
- Requirements (virtual properties, proxies enabled).
- N+1 problem dangers.

## Explicit loading

- context.Entry(entity).Collection(...).Load()
- context.Entry(entity).Reference(...).Load()

## Global query filters

- Temporal tables & time travel queries.
- Execute raw SQL (FromSql, ExecuteSql).
- Interceptors (logging, soft delete, multi-tenancy).
- Query tags (TagWith).
- Batching vs non-batching behavior.

## Transactions

- BeginTransaction.
- SaveChanges + rollback patterns.
- Ambient transactions (TransactionScope).
- Execution strategies & resiliency (connection retries).

## Repository & Unit of Work patterns

- Abstraction over EF Core.
- Why over-abstracting can be harmful.
- When repositories still make sense (DDD aggregates).
- CQRS and EF Core.

## Performance & optimization

- Change tracker behavior (AutoDetectChangesEnabled).
- Using AsNoTracking for read-heavy scenarios.
- Compiled queries.
- Bulk operations (via EFPlus or Dapper).
- Index configuration.
- Avoiding cartesian joins with Includes.

## Concurrency & locking

- Concurrency tokens ([Timestamp], IsRowVersion).
- Optimistic concurrency exceptions.
- Handling concurrency conflicts (client wins/server wins).

## DbContext management

- Scoped lifetime in ASP.NET Core DI.
- Disposing contexts.
- Pooling DbContexts (AddDbContextPool).

# 9. Design Patterns

## Creational:

### Singleton:

### Factory:

### Builder:

## Structural:

### Adapter:

### Decorator:

### Facade:

## Behavioral:

### Strategy: 

### Observer:

### Command: 

# 10. Testing

## xUnit

- Facts vs Theories.
- Test fixtures.
- Assertions.

## Moq, NSubstitute

- Mocking interfaces.
- Verifying calls.
- Setup/Returns patterns.

## Unit testing best practices

- Arrange-Act-Assert.
- Test isolation.
- Avoid hitting real DB/services.

## Integration testing

- WebApplicationFactory.
- TestServer.
- In-memory DB.

# 11. SOLID Principles

## S — Single Responsibility Principle:

- A class should have only one reason to change.
- Improves readability and reduces coupling.
- Example

## O — Open/Closed Principle:

- Open for extension, closed for modification.
- Achieved via interfaces, inheritance, strategy pattern.
- Reduces code changes that risk breaking existing behavior.

## L — Liskov Substitution Principle:

- Subtypes must be substitutable for their base types.
- Avoid violating expected behavior (e.g., throwing unexpected exceptions).
- Ensures reliable polymorphism.

## I — Interface Segregation Principle:

- Prefer smaller, more specific interfaces over large “fat” ones.
- Prevents classes from being forced to implement unused members.
- Encourages cleaner abstractions.

## D — Dependency Inversion Principle:

- High-level modules should not depend on low-level modules; depend on abstractions.
- Inversion of control (IoC) containers help enforce this.
- Promotes testability and loose coupling.


# 12. Performance Profiling

- dotnet-trace
- dotnet-dump
- PerfView
- BenchmarkDotNet
- Profiling memory leaks & CPU issues