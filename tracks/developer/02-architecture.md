# D2. Architecture Patterns

## Why Architecture Still Matters

AI can generate working code quickly. What it often lacks is architectural judgment:

- Where should this logic live?
- What should know about what?
- How should components communicate?
- What will be easy to change later?

Your role shifts from writing code to **guiding architectural decisions** and **recognising violations**.

## Patterns as Reasoning Tools

Architectural patterns aren't rules to memorise — they're **reasoning tools** for thinking about structure.

### Separation of Concerns (MVC and Friends)

The core insight: **different kinds of logic should live in different places**.

| Concern | Where It Lives | What It Does |
|---------|---------------|--------------|
| **Model** | Data layer | Represents state, business logic |
| **View** | Presentation layer | Renders data for users |
| **Controller** | Coordination layer | Handles input, orchestrates |

**Why this matters for AI:**
AI often generates code that works but violates boundaries:
- View logic mixed with data fetching
- Business rules scattered across controllers
- Database queries in presentation code

**Your job:** Recognise these violations and refactor (or ask AI to refactor with explicit guidance).

```
QUIZ:
AI generates an Express route handler that:
1. Validates input
2. Queries the database directly
3. Applies a discount calculation
4. Formats the response as HTML

What's the architectural problem?

* Nothing — it works
* It should use React
*! Multiple concerns are mixed: validation, data access, business logic, and presentation should be separated
* Express routes can't do all this
FEEDBACK:This handler mixes validation, data access, business logic (discount calculation), and presentation. Each should be in its own layer.
```

### Repository Pattern

**Insight:** Separate data access from business logic.

```
Business Logic → Repository Interface → Database
```

The business logic doesn't know (or care) whether data comes from PostgreSQL, an API, or a mock.

**Why this matters:**
- Testability (mock the repository)
- Flexibility (swap data sources)
- Clarity (business rules aren't tangled with SQL)

### Service Layer

**Insight:** Complex operations that span multiple entities belong in services.

```
Controller → Service → Repository(ies) → Database
```

A service might coordinate:
- Multiple repository calls
- Transactions
- Cross-cutting concerns

### Dependency Injection

**Insight:** Components receive their dependencies rather than creating them.

```python
# Tight coupling (hard to test/change)
class OrderService:
    def __init__(self):
        self.db = PostgresDatabase()  # Creates its own dependency

# Loose coupling (dependency injected)
class OrderService:
    def __init__(self, db):
        self.db = db  # Receives dependency
```

**Why this matters:**
- Testing: inject mocks
- Flexibility: swap implementations
- Clarity: dependencies are explicit

## Recognising AI Architectural Violations

Common patterns in AI-generated code that signal architectural issues:

| Smell | What It Looks Like | Better Approach |
|-------|-------------------|-----------------|
| **God object** | One class that does everything | Split into focused components |
| **Scattered logic** | Same business rule in multiple places | Centralise in service/model |
| **Leaky abstraction** | Database details in controller | Use repository pattern |
| **Tight coupling** | Direct instantiation everywhere | Dependency injection |
| **Mixed concerns** | HTML generation in data layer | Separate view from model |

### Example: Before and After

**AI-generated (works but problematic):**
```javascript
app.get('/orders/:id', async (req, res) => {
  const db = new Database();
  const order = await db.query(`SELECT * FROM orders WHERE id = ${req.params.id}`);
  if (order.total > 100) {
    order.discount = order.total * 0.1;  // Business rule here
  }
  res.send(`<h1>Order ${order.id}</h1><p>Total: ${order.total - (order.discount || 0)}</p>`);
});
```

**Problems:**
- SQL injection vulnerability
- Database created per-request
- Business rule (discount) in route handler
- HTML mixed with logic

**Refactored:**
```javascript
// orderRepository.js
class OrderRepository {
  constructor(db) { this.db = db; }
  async findById(id) {
    return this.db.query('SELECT * FROM orders WHERE id = $1', [id]);
  }
}

// orderService.js
class OrderService {
  constructor(orderRepo) { this.orderRepo = orderRepo; }
  async getOrderWithDiscount(id) {
    const order = await this.orderRepo.findById(id);
    if (order.total > 100) {
      order.discount = order.total * 0.1;
    }
    return order;
  }
}

// route
app.get('/orders/:id', async (req, res) => {
  const order = await orderService.getOrderWithDiscount(req.params.id);
  res.render('order', { order });
});
```

## Guiding AI Toward Good Architecture

Instead of accepting AI's first pass, specify architecture:

**Vague prompt:**
> "Create an API endpoint to get orders with discounts"

**Architecture-aware prompt:**
> "Create an API endpoint to get orders with discounts.
>
> Architecture requirements:
> - Use repository pattern for data access
> - Discount calculation should be in a service layer
> - Controller should only coordinate, not contain business logic
> - Use parameterised queries (no string interpolation)"

```
EXERCISE:
You're asking AI to build a user authentication system.

Write a prompt that specifies architectural requirements for:
- Separation of concerns
- Where password hashing belongs
- Where session management belongs
- How controllers should interact with these
```

## Complexity and Abstraction

### When to Abstract

Not everything needs layers. Consider:

| Situation | Approach |
|-----------|----------|
| Prototype / proof of concept | Simple is fine |
| Single use, simple logic | Direct implementation |
| Shared logic, multiple uses | Extract to service |
| Data access patterns | Repository pattern |
| Growing complexity | Refactor incrementally |

### The Cost of Abstraction

Every layer adds:
- Indirection (harder to follow flow)
- Files (more places to look)
- Maintenance (more to keep consistent)

Don't abstract prematurely. But recognise when it's time.

## Architecture Documentation

For AI to help maintain architectural consistency, document your patterns:

```markdown
# Architecture Overview

## Layers
- Controllers: Handle HTTP, validate input, return responses
- Services: Business logic, orchestration
- Repositories: Data access only
- Models: Data structures, simple computed properties

## Rules
- Controllers never access database directly
- Business rules live in services
- Repositories return domain objects, not raw DB results
- No circular dependencies between services
```

Include this in your AI context to get architecturally-consistent suggestions.

## Key Takeaways

- AI generates code that works but often violates architectural boundaries
- Patterns are reasoning tools, not rules to memorise
- Separation of concerns: different logic in different places
- Repository pattern separates data access from business logic
- Dependency injection enables testing and flexibility
- Learn to recognise architectural smells in AI output
- Guide AI with architecture-aware prompts
- Document architecture so AI can be consistent

---

Next: **D3. MCP & Tool Design** →
