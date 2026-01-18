# D3. MCP & Tool Design

## What is MCP?

**Model Context Protocol (MCP)** is a standard for connecting AI models to external tools and data sources.

Think of it as:
- A way to give AI "hands" — the ability to take actions
- A standard interface between AI and capabilities
- A trust boundary — you control what AI can do

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│     AI      │────▶│   MCP       │────▶│   Tools     │
│   Model     │◀────│  Protocol   │◀────│  & APIs     │
└─────────────┘     └─────────────┘     └─────────────┘
```

## MCP Core Concepts

### Tools
Actions the AI can take. Examples:
- `search_documents` — query a knowledge base
- `send_email` — send an email (with approval)
- `run_query` — execute a database query
- `create_file` — write a file to disk

### Resources
Data the AI can access. Examples:
- Files on disk
- Database contents
- API responses
- System information

### Prompts
Pre-configured instruction templates. Examples:
- "Analyse this codebase"
- "Summarise these documents"
- "Review this PR"

## Designing Good MCP Tools

### Principle 1: Clear, Descriptive Names

**Bad:** `do_thing`, `process`, `handle`
**Good:** `search_knowledge_base`, `create_calendar_event`, `get_user_profile`

The AI reads the tool name to understand what it does.

### Principle 2: Explicit Parameter Schemas

Every parameter should have:
- **Name:** Descriptive
- **Type:** Explicit (string, integer, array, etc.)
- **Description:** What it's for
- **Required:** Whether it's mandatory
- **Constraints:** Valid values, ranges, formats

```json
{
  "name": "search_documents",
  "description": "Search the knowledge base for documents matching a query",
  "parameters": {
    "query": {
      "type": "string",
      "description": "Search terms to find relevant documents",
      "required": true
    },
    "limit": {
      "type": "integer",
      "description": "Maximum number of results to return",
      "required": false,
      "default": 10,
      "minimum": 1,
      "maximum": 100
    },
    "category": {
      "type": "string",
      "description": "Filter to specific document category",
      "required": false,
      "enum": ["technical", "policy", "general"]
    }
  }
}
```

### Principle 3: Structured Responses

Return data that's easy for AI to parse and reason about:

**Hard to parse:**
```
"Found 3 documents. The first is titled 'Getting Started' and was updated yesterday..."
```

**Easy to parse:**
```json
{
  "count": 3,
  "results": [
    {
      "id": "doc-123",
      "title": "Getting Started",
      "updated": "2024-01-15",
      "relevance_score": 0.95
    }
  ]
}
```

### Principle 4: Informative Errors

Errors should tell the AI what went wrong and what to do:

**Bad error:**
```json
{"error": "Failed"}
```

**Good error:**
```json
{
  "error": {
    "code": "INVALID_QUERY",
    "message": "Query cannot be empty",
    "suggestion": "Provide at least one search term"
  }
}
```

```
EXERCISE:
Design an MCP tool for managing a todo list with these operations:
- Add a todo item
- Mark item complete
- List all items (with optional filter)

For each operation, specify:
- Tool name
- Parameters (with types and descriptions)
- Response format
- Possible errors
```

## Tool Granularity

### Fine-Grained Tools
Many small, focused tools:
- `get_user`
- `update_user_email`
- `update_user_name`
- `delete_user`

**Pros:** Composable, clear scope, easier to audit
**Cons:** More tools to manage, AI must know to combine them

### Coarse-Grained Tools
Fewer, multi-purpose tools:
- `manage_user` (with action parameter: get, update, delete)

**Pros:** Fewer tools, powerful operations
**Cons:** Complex parameters, harder to audit

### Recommendation
Start fine-grained. AI can compose small tools. Combine only when patterns emerge.

## Tool Safety

### Categories of Risk

| Risk Level | Examples | Mitigation |
|------------|----------|------------|
| **Read-only** | Search, query, get | Generally safe |
| **Create** | Add items, send messages | May need approval |
| **Modify** | Update records, edit files | Usually needs approval |
| **Delete** | Remove items, drop tables | Always needs approval |
| **External** | Send emails, API calls | Careful about scope |

### Human-in-the-Loop for Risky Operations

```json
{
  "name": "send_email",
  "description": "Send an email (requires user confirmation)",
  "requires_confirmation": true,
  "parameters": { ... }
}
```

The AI should present the action for approval before executing.

### Scope Boundaries

Tools should have explicit boundaries:
- Which databases/tables are accessible
- Which directories can be read/written
- Which APIs can be called
- What rate limits apply

```
QUIZ:
You're designing a tool that lets AI query a database. Which approach is safest?

* Let AI write arbitrary SQL queries
*! Provide specific query templates with parameter substitution
* Only allow read operations with row limits
* All of the above combined, with b+c as the base
FEEDBACK:Combining parameterised queries (no SQL injection) with read-only access and row limits provides multiple safety layers.
```

## Testing MCP Tools

### Unit Test the Tool
- Does it do what the description says?
- Does it handle edge cases?
- Does it return the documented format?
- Does it fail gracefully?

### Test AI Understanding
- Give AI only the tool schema
- Ask it to explain what the tool does
- Ask it to describe when it would use the tool
- If AI misunderstands, improve the description

### Integration Test
- Can AI complete realistic tasks using the tool?
- Does AI use the tool appropriately (not over/under-using)?
- Does the tool + AI combination produce correct results?

## MCP Tool Documentation Template

```markdown
# Tool: [name]

## Purpose
What this tool does and when to use it.

## Parameters
| Name | Type | Required | Description |
|------|------|----------|-------------|
| ... | ... | ... | ... |

## Response Format
```json
{
  "example": "response"
}
```

## Errors
| Code | Meaning | Resolution |
|------|---------|------------|
| ... | ... | ... |

## Examples
### Example 1: Basic usage
Input: ...
Output: ...

### Example 2: With optional parameters
Input: ...
Output: ...

## Security Considerations
- What this tool can/cannot access
- Approval requirements
- Rate limits
```

## Key Takeaways

- MCP connects AI to external capabilities (tools, resources, prompts)
- Good tool design: clear names, explicit schemas, structured responses, informative errors
- Start with fine-grained tools; AI can compose them
- Risky operations need human-in-the-loop
- Test both the tool AND AI's understanding of it
- Document tools thoroughly — AI reads the documentation

---

Congratulations! You've completed the Developer Track.

Consider also:
- **Enterprise Track** — For governance and compliance context
- **Academic Track** — For research and writing workflows
