# Model Context Protocol: Advanced Topics

## Sampling

### Definition

**Sampling** is a way for **servers to access language models through connected MCP clients** — rather than the server needing its own direct API access to an LLM.

### What is Sampling?

Sampling lets an **MCP server** request an LLM completion **through the client** — instead of the server needing its own API key and paying for its own AI usage.

### How Sampling Works (Step-by-Step Flow)

1. **Server does its work** (e.g., fetching Wikipedia articles, reading files)
2. **Server creates a prompt** asking for text generation based on that work
3. **Server sends a sampling request** to the client
4. **Client calls Claude** with the provided prompt
5. **Client returns the generated text** to the server
6. **Server uses the generated text** in its final response to the user

```
Server                          Client                    Claude
  │                                │                         │
  │ 1. Fetch data (e.g. Wikipedia) │                         │
  │                                │                         │
  │ 2. Build a prompt              │                         │
  │                                │                         │
  │ 3. sampling/createMessage ────▶│                         │
  │                                │  4. Call Claude ───────▶│
  │                                │◀──── Generated text ────│
  │◀─── 5. Return generated text ──│                         │
  │                                │                         │
  │ 6. Use text in final response  │                         │
```

### When to Use Sampling

**Key use case**: Building **publicly accessible MCP servers**.

**Why it matters**:

- You don't want random users generating unlimited AI text at *your* expense
- With sampling, **each client pays for their own AI usage**
- Users still benefit from your server's functionality
- Protects server operators from unbounded API costs

### Implementation Steps

1. **Initial request**: Server calls `create_message()` to request a completion
2. **Client-side callback**: Define a `sampling_callback` function that handles the request
3. **Message format**: Structure the prompt/message properly for Claude
4. **Return generated text**: Callback returns Claude's response back to the server
5. **Connect the callback** when creating the client session:

    ```python
    async with ClientSession(
        read, write, sampling_callback=sampling_callback
    ) as session:
        # session now handles sampling requests automatically
        ...
    ```

6. **Getting a result**: Server receives the generated text and continues processing

---

## Logging and Progress Notifications

MCP servers can send real-time updates to clients about long-running operations.

### Available Notification Methods

- `info()` — General informational messages
- `warning()` — Non-critical issues worth flagging
- `debug()` — Detailed diagnostic information
- `error()` — Something went wrong
- `report_progress()` — Numeric/percentage progress updates

### How Different Client Types Handle Notifications

| Client Type | How It Displays Updates |
|---|---|
| **CLI applications** | Simply print messages and progress to the terminal |
| **Web applications** | Use WebSockets, server-sent events (SSE), or polling to push updates to the browser |
| **Desktop applications** | Update progress bars and status displays in the UI |

**Why this matters**: Long-running server operations (large file processing, multi-step workflows) feel more responsive when users see live progress instead of silent waiting.

---

## Roots

### What Are Roots?

Roots define **which directories/files a server is allowed to access** — a security and scoping boundary set by the client, not the server.

### How Roots Work

1. **Server calls `list_roots()`** to discover what directories/paths it's permitted to access
2. **Server explores accessible directories** (e.g., listing files) within those approved boundaries
3. **Server validates any file request** against the approved roots before acting

### Access Validation Pattern

A typical `is_path_allowed()` function:

- Takes a requested file path
- Gets the list of approved roots (from the client)
- Checks if the requested path falls within one of those approved roots
- Returns `true`/`false` for access permission

```python
def is_path_allowed(requested_path: str, approved_roots: list[str]) -> bool:
    for root in approved_roots:
        if requested_path.startswith(root):
            return True
    return False
```

**Why this matters**: Roots prevent a server from accessing files outside the boundaries the *user/client* has explicitly approved — a critical safety mechanism, especially for file-system-accessing servers.

---

## Transports and Communication

MCP uses **JSON-RPC messages** to handle all communication between clients and servers, regardless of the underlying transport method.

### Transport Options

- **STDIO transport**: For local processes (client and server on the same machine)
- **Streamable HTTP transport**: For remote/networked servers

---

### STDIO Transport

![Stdio Transport](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749747951%2F006_-_The_Stdio_Transport_02.1749747951605.png)

**How it works**: The client launches the server as a subprocess and communicates via standard input/output streams.

**MCP Connection Sequence**:

![Connection Sequence](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749747952%2F006_-_The_Stdio_Transport_07.1749747952662.png)

**Message Types and Flow**:

![Message Types and Flow](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749747953%2F006_-_The_Stdio_Transport_13.1749747953112.png)

**Four Communication Scenarios**:

| Scenario | Direction | Mechanism |
|---|---|---|
| Client → Server request | Client sends request | Client writes to **stdin** |
| Server → Client response | Server replies | Server writes to **stdout** |
| Server → Client request | Server initiates (e.g., sampling) | Server writes to **stdout** |
| Client → Server response | Client replies | Client writes to **stdin** |

**Key insight**: Communication is bidirectional — either side can *initiate* a request (not just client → server). This is how sampling requests flow from server to client.

**Best for**: Local development, CLI tools, desktop app integrations where client and server run on the same machine.

---

### Streamable HTTP Transport

![Streamable HTTP Sequence](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749747953%2F007_-_The_StreamableHTTP_Transport_19.1749747952895.png)

**Why it exists**: STDIO only works when client and server share a machine. Streamable HTTP enables **remote** MCP servers accessible over a network.

**Tool Calls and Dual SSE Connections**:

![SSE Connections](https://everpath-course-content.s3-accelerate.amazonaws.com/instructor%2Fa46l9irobhg0f5webscixp0bs%2Fpublic%2F1749747953%2F008_-_StreamableHTTP_in_Depth_08.1749747953358.png)

- Uses a single HTTP endpoint that can be upgraded to a **Server-Sent Events (SSE)** stream
- Enables the server to push messages (like sampling requests or progress updates) back to the client asynchronously, not just respond to requests

**Stateless HTTP**

- An alternative mode where each request is independent, with no persistent connection maintained between calls
- Simpler to scale horizontally (no server-side session affinity needed)
- Trade-off: Can't push unsolicited messages (like sampling requests) to the client as easily as a persistent SSE connection

**Key Flags (Python SDK / FastMCP)**:

| Flag | Purpose |
|---|---|
| `stateless_http=True` | Enables stateless mode — no session persistence between requests |
| `json_response=True` | Returns plain JSON instead of upgrading to an SSE stream |

**For "simpler HTTP responses without streaming, just the final result as plain JSON"** — enable **both** flags together:

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP(
    "StatelessServer",
    stateless_http=True,   # no session persistence
    json_response=True     # no SSE stream, just plain JSON
)

mcp.run(transport="streamable-http")
```

- `stateless_http=True` alone removes session persistence but can still use SSE
- `json_response=True` is the flag that specifically skips the SSE stream and returns a plain JSON result
- Together, they give you the simplest possible request/response cycle — ideal for serverless deployments (e.g., AWS Lambda) where persistent connections aren't practical

---

## Transport Comparison Summary

| Feature | STDIO | Streamable HTTP |
|---|---|---|
| **Location** | Local (same machine) | Remote (over network) |
| **Setup complexity** | Simple | More complex |
| **Bidirectional messaging** | Yes (via stdin/stdout) | Yes (via SSE upgrade) |
| **Best for** | CLI tools, local dev, desktop apps | Web services, cloud-hosted servers, multi-user scenarios |
| **Stateless option** | No | Yes |

---

## Assessment Prep Summary

**Key Concepts to Know**:

1. **Sampling**: Lets servers request LLM completions *through the client*, so each client pays for their own AI usage — critical for public MCP servers
2. **Sampling flow**: Server does work → builds prompt → sends sampling request → client calls Claude → returns text → server uses it
3. **sampling_callback**: The client-side function that handles incoming sampling requests
4. **Logging methods**: `info()`, `warning()`, `debug()`, `error()`, `report_progress()`
5. **Roots**: Client-approved directory/file boundaries that constrain what a server can access
6. **is_path_allowed()**: Validates a requested path against approved roots
7. **Transports**: STDIO (local, stdin/stdout) vs Streamable HTTP (remote, SSE-based)
8. **STDIO four scenarios**: Both client and server can initiate requests or send responses
9. **Streamable HTTP**: Uses SSE upgrade for server-initiated messages; supports stateless mode too
10. **`json_response=True`**: The specific flag for plain JSON responses with no SSE streaming
11. **`stateless_http=True`**: The flag for no session persistence between requests (can be used with or without `json_response`)

**Quick Reference — Who Initiates What**:

- Sampling requests: **Server → Client** (reversed from typical tool calls)
- Roots requests: **Server → Client** (server asks what it's allowed to access)
- Tool calls: **Client → Server** (standard direction)

**Common Test Trap**: Remember that MCP communication isn't strictly one-directional. Both **Sampling** and **Roots** involve the **server** initiating a request **to the client** — the reverse of the typical tool-call pattern.
