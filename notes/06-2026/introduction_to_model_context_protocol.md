# Introduction to Model Context Protocol

![primitive](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849326%2F09_-_011_-_MCP_Review_00.1749849326738.png)

## What is MCP?

**Model Context Protocol (MCP)** is a communication layer that provides Claude with context and tools without requiring you to write tedious integration code.

Instead of building custom schemas and functions for every service, MCP standardizes how Claude connects to external systems—making integrations faster, safer, and more maintainable.

---

## Why MCP Matters

### The Problem It Solves

Without MCP, connecting Claude to a service like GitHub means:

- Create schemas for every GitHub feature
- Write functions for every endpoint
- Maintain consistency across multiple clients
- Update code everywhere when the service changes

### The Solution

MCP provides:

- **Standard protocol** for client-server communication
- **Reusable servers** created by service providers (official or community)
- **Simplified client implementation** in your application
- **Centralized maintenance** — update the server once, all clients benefit

---

## Core Concepts

### Transport Agnostic

**Definition**: MCP clients and servers can communicate over *any* underlying protocol.

**Supported transports**:

- HTTP
- WebSockets
- Standard input/output (stdio)
- Various other network protocols

**Why it matters**: You choose the communication method best suited to your architecture—MCP handles the abstraction layer.

---

## The Basic Architecture

![MCP Client-Server Architecture](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849216%2F09_-_001_-_Introducing_MCP_01.1749849216723.png)

**Components**:

- **MCP Client**: Your application (Claude integration, web server, etc.)
- **MCP Server**: Service implementation (GitHub, Slack, database, etc.)
- **Communication**: Standardized messages over your chosen transport

---

## The Three Primitives: Tools, Resources, and Prompts

### 1. Tools (Model-Controlled)

**What**: Functions Claude can call to take actions

**Examples**:

- `search_github(query)`
- `create_issue(title, description)`
- `list_pull_requests(repo)`

**Control**: Claude decides when to call them based on the task

**Message types**:

- `ListToolsRequest` → Server responds with available tools
- `CallToolRequest` → Claude requests tool execution
- `CallToolResult` → Server returns tool result

![MCP Message Flow](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849232%2F09_-_002_-_MCP_Clients_19.1749849231568.png)

---

### 2. Resources (App-Controlled)

**What**: Data or content the application exposes to Claude

**Types**:

#### Direct Resources

- Specific, single items
- Example: A specific GitHub repository, a particular document file
- URI format: `github://user/repo`

#### Templated Resources

- Pattern-based collections
- Example: All files in a directory (`file://documents/*`)
- URI format: `file://documents/{filename}`

**Message types**:

- `ListResourcesRequest` → Get available resources
- `ResourcesResult` → Server provides resource list
- `ReadResourceRequest` → Claude reads a specific resource

![Resource Types](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849289%2F09_-_007_-_Defining_Resources_07.1749849289476.png)

---

### 3. Prompts (User-Controlled)

**What**: Reusable prompt templates that encode expertise or workflows

**Examples**:

- Code review prompt template (with parameters for language, file)
- Security analysis prompt (with scoping parameters)
- Documentation template (with project-specific context)

**Control**: User/application selects which prompt to use

**Benefits**:

- Consistency across multiple conversations
- Encode domain knowledge in one place
- Share expertise across team
- Update guidance centrally

---

## Building an MCP Server (Hands-on)

### Step 1: Setting Up the MCP Server

- Framework: Similar to FastAPI or Express
- Define your service capabilities
- Expose tools, resources, and/or prompts

### Step 2: Tool Definition

Use decorators to define tools Claude can call:

```python
@tool
def read_document(path: str) -> str:
    """Read the contents of a document file"""
    # Implementation here

@tool
def edit_document(path: str, content: str) -> bool:
    """Update document contents"""
    # Implementation here
```

**What gets created**:

- Tool schemas (name, description, parameters)
- Input validation
- Error handling

### Step 3: Testing with the Inspector

![Tool Definition Interface](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849221%2F09_-_004_-_Defining_Tools_with_MCP_00.1749849221750.png)

**MCP Inspector**:

- Web-based testing interface
- Test tools without building a full client
- Verify tool schemas and responses
- Debug communication between client and server

**How to use**:

1. Start your MCP server
2. Launch the Inspector
3. Connect to your server
4. Test individual tools
5. Verify responses match expected format

---

## Building an MCP Client (Integration)

### Client Architecture

![Client Components](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749849286%2F09_-_006_-_Implementing_a_Client_02.1749849285884.png)

**Two main components**:

1. **Connection Management**
   - Establish transport (HTTP, WebSocket, stdio)
   - Manage client lifecycle
   - Handle reconnection/errors

2. **Request Handling**
   - Send tool/resource/prompt requests to server
   - Process responses
   - Pass results to Claude or application

### Client Workflow

```
Your Application
    ↓
MCP Client (connection logic)
    ↓
Network/Transport (HTTP, WebSocket, etc.)
    ↓
MCP Server
    ↓
Actual Service (GitHub, Slack, database, etc.)
```

---

## Message Types Summary

| Message Type | Direction | Purpose |
|---|---|---|
| `ListToolsRequest` | Client → Server | Get available tools |
| `ListToolsResult` | Server → Client | Return tool list and schemas |
| `CallToolRequest` | Client → Server | Execute a specific tool |
| `CallToolResult` | Server → Client | Return tool execution result |
| `ListResourcesRequest` | Client → Server | Get available resources |
| `ListResourcesResult` | Server → Client | Return resource list |
| `ReadResourceRequest` | Client → Server | Read specific resource |
| `ReadResourceResult` | Server → Client | Return resource content |
| `ListPromptsRequest` | Client → Server | Get available prompts |
| `ListPromptsResult` | Server → Client | Return prompt list |
| `GetPromptRequest` | Client → Server | Get specific prompt template |
| `GetPromptResult` | Server → Client | Return prompt with values |

---

## Key Benefits of MCP

### 1. Consistency

- Users get reliable results every time
- Tool behavior is predictable and documented
- Reduces hallucinations from unclear tool definitions

### 2. Expertise

- You encode domain knowledge into prompts
- Expertise travels with the service, not duplicated in each client
- Guidance stays updated centrally

### 3. Reusability

- Multiple client applications can use the same server
- Build once, integrate everywhere
- Team members share the same integrations

### 4. Maintainability

- Update prompts, tools, or resources in one place
- All clients automatically benefit from improvements
- Reduces scattered, outdated code

---

## When to Use MCP

### Perfect Fit ✅

- Integrating with popular services (GitHub, Slack, Asana, etc.)
- Multiple applications need same integration
- Integrations likely to evolve or grow
- Team collaboration on integrations

### Consider Alternatives ⚠️

- One-time, simple integration
- Very specific to single application
- Minimal tool/resource exposure needed

### Not Needed ❌

- Plain API calls to simple services
- No need for standardization

---

## Official MCP Servers (Examples)

Service providers offer official MCP implementations for:

- **GitHub**: Repository operations, issues, PRs
- **Slack**: Message sending, channel management
- **Asana**: Task and project management
- **Linear**: Issue tracking
- **Databases**: Query and data management
- **File systems**: Document access and editing

Community also creates MCP servers for other services.

---

## Test Preparation Summary

**Key Concepts to Know**:

1. MCP solves the integration complexity problem
2. Three primitives: Tools (Claude-controlled), Resources (app-controlled), Prompts (user-controlled)
3. Transport agnostic: Works over HTTP, WebSocket, stdio, etc.
4. Message types for each operation (List, Call, Read, etc.)
5. Benefits: Consistency, expertise encoding, reusability, maintenance
6. Inspector for testing servers before client integration
7. Client handles connection and request routing
8. Official servers available from service providers

**Quick Reference**:

- **Tools**: Functions Claude can call (ListToolsRequest, CallToolRequest)
- **Resources**: Data app exposes (ListResourcesRequest, ReadResourceRequest)
- **Prompts**: Expertise templates (ListPromptsRequest, GetPromptRequest)
- **Transport**: HTTP, WebSocket, stdio—MCP doesn't care
- **Message flow**: Client requests → Server processes → Server responds
