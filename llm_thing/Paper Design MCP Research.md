---
date: '2026-06-27T19:32:34.871146-04:00'
model: 'Claude 3.5 Sonnet'
---

# Paper Design MCP Research

# Paper Design MCP Research & Implementation Guide

*Researched: 2026-06-27 | Model: Claude*

---

## What is Paper Design MCP?

The **Paper MCP server** is a bridge that connects AI agents to your Paper.design files, allowing them to read and write design content via the Model Context Protocol (MCP). Paper is a design canvas where everything is built with real HTML/CSS — not a proprietary format. This makes it uniquely "agent-ready" because LLMs are excellent at understanding the DOM.

- **Website:** [paper.design](https://paper.design/)
- **MCP Docs:** [paper.design/docs/mcp](https://paper.design/docs/mcp)
- **Status:** Open alpha
- **MCP transport:** Streamable HTTP at `http://127.0.0.1:29979/mcp`
- **Requires:** Paper Desktop app installed + a file open

---

## How It Works

The Paper Desktop app automatically starts an MCP server in the background when you open a file. Any MCP-compatible AI agent (Cursor, Claude Code, Codex, Copilot, OpenCode, etc.) can then connect to this local server to read your design files and write changes back.

### Architecture
```
┌─────────────────┐     Streamable HTTP      ┌──────────────────┐
│  AI Agent       │ ───────────────────────▶ │  Paper Desktop   │
│  (Cursor, etc.) │ ◀─────────────────────  │  MCP Server      │
│                 │   JSON-RPC / MCP         │  (port 29979)    │
└─────────────────┘                          └──────────────────┘
                                                      │
                                                      ▼
                                             ┌──────────────────┐
                                             │  Your Design File │
                                             │  (HTML/CSS canvas)│
                                             └──────────────────┘
```

---

## Available MCP Tools

### Read Tools
- `get_basic_info` — File name, page name, node count, artboard list
- `get_selection` — Currently selected nodes (IDs, names, types, size)
- `get_node_info` — Node details by ID (size, visibility, lock, parent, children, text)
- `get_children` — Direct children of a node
- `get_tree_summary` — Compact subtree hierarchy summary (optional depth limit)
- `get_screenshot` — Screenshot of a node by ID (base64 image; 1x or 2x scale)
- `get_jsx` — JSX for a node and descendants (Tailwind or inline-styles format)
- `get_computed_styles` — Computed CSS styles for one or more nodes
- `get_fill_image` — Image data from a node with image fill (base64 JPEG)
- `get_font_family_info` — Check if a font family is available
- `get_guide` — Retrieve guided workflows (e.g., figma-import)
- `export` — Export nodes as PNG, JPG, SVG, MP4, etc. with scale overrides

### Write Tools
- `create_artboard` — Create a new artboard (optional name and styles)
- `write_html` — Parse HTML and add/replace nodes (insert-children or replace mode)
- `set_text_content` — Set text content of one or more Text nodes
- `rename_nodes` — Rename one or more layers
- `duplicate_nodes` — Deep-clone nodes; returns new IDs
- `move_nodes` — Reposition or reparent nodes
- `update_styles` — Update CSS styles on one or more nodes
- `delete_nodes` — Delete one or more nodes
- `finish_working_on_nodes` — Clear working indicator from artboards

---

## Connection Configuration for Various Agents

### Cursor (Plugin)
```
/add-plugin paper-desktop
```
Or search "paper" in Cursor Marketplace.

### Claude Code CLI (Plugin)
```bash
/plugin marketplace add paper-design/agent-plugins
/plugin install paper-desktop@paper
```

### Claude Code CLI (Manual)
```bash
claude mcp add paper --transport http http://127.0.0.1:29979/mcp --scope user
```

### Claude Desktop (Manual)
```json
"mcpServers": {
  "paper": {
    "command": "npx",
    "args": ["mcp-remote", "http://127.0.0.1:29979/mcp"]
  }
}
```

### Codex (Manual)
Settings > MCP Servers > Add custom > "Streamable HTTP" tab:
- Name: `paper`
- URL: `http://127.0.0.1:29979/mcp`

### VS Code Copilot
`.vscode/mcp.json`:
```json
{
  "servers": {
    "paper": {
      "type": "http",
      "url": "http://127.0.0.1:29979/mcp"
    }
  }
}
```

### OpenCode
`opencode.json`:
```json
{
  "mcp": {
    "paper": {
      "type": "remote",
      "url": "http://127.0.0.1:29979/mcp",
      "enabled": true
    }
  }
}
```

### Antigravity
`mcp_config.json`:
```json
{
  "mcpServers": {
    "paper": {
      "serverUrl": "http://127.0.0.1:29979/mcp"
    }
  }
}
```

---

## Community MCP Server (GitHub: ripgrim/paper-mcp)

A community-built MCP server also exists that connects to Paper via WebSocket API (not requiring the desktop app).

- **Repo:** [github.com/ripgrim/paper-mcp](https://github.com/ripgrim/paper-mcp)
- **Language:** TypeScript
- **Auth:** Requires extracting cookies from browser (F12 > Application > Cookies)
- **Tools:**
  - `list_user_documents` — List recent Paper documents
  - `list_pages`, `list_nodes` — List pages and canvas nodes
  - `get_node` — Get node details by ID
  - `create_node` — Create shapes (Rectangle, Frame, Ellipse) with position, size, color
  - `update_node` — Update node attributes
  - `delete_node` — Delete a node
  - `take_screenshot` — Capture a page screenshot
- **Config format:**
  ```json
  {
    "mcpServers": {
      "paper": {
        "command": "node",
        "args": ["/path/to/paper-mcp/dist/index.js"],
        "env": {
          "PAPER_COOKIES": "cookie1=value1; cookie2=value2",
          "PAPER_DOCUMENT_ID": "your-doc-id",
          "DEBUG": "false"
        }
      }
    }
  }
  ```

---

## Key Workflows & Use Cases

### 1. Design to Code (Design → Website)
- Select a frame in Paper with flex layouts
- Ask agent: *"Build a website using the hero section I selected in Paper. Use React and Tailwind."*
- Agent reads the design via MCP tools (read-only), then generates code in your project folder

### 2. Sync Design Tokens from Figma
- Install both Paper MCP and Figma MCP in the same agent
- Select an element with a variable/style in Figma
- Ask agent: *"Create a design system in Paper that matches my Figma file"*
- Note: Figma MCP is read-only; Paper MCP can write

### 3. Pull Real Content from Notion
- Install both Paper MCP and Notion MCP in the same agent
- Ask agent: *"Sync content from my Notion Testimonials database with this frame"*
- Agent reads from Notion, writes to Paper — replacing placeholder text

### 4. AI-Driven Design Creation
- Ask agent: *"Create a red rectangle in Paper"* (verification test)
- Agent writes directly to your Paper canvas via `write_html` or `create_artboard`

### 5. Rapid Prototyping
- Describe UI requirements to the agent
- Agent creates frames, sets styles, places elements on the canvas

---

## Implementing as a Custom Agent (General MCP Architecture)

### MCP Protocol Overview
MCP uses a **client-server architecture** with JSON-RPC 2.0 messages:
- **Host:** AI application (e.g., Cursor, Claude)
- **Client:** Manages connection to servers
- **Server:** Provides tools, resources, and prompts

### Building a Custom MCP Server (Python SDK)

```python
from mcp import FastMCP

mcp = FastMCP("my-design-agent")

@mcp.prompt()
def system_prompt():
    return """You are a design agent that helps users create and modify 
    designs in Paper. Use the available tools to read and write to 
    Paper design files."""

@mcp.tool()
def get_paper_info():
    """Get basic info about the currently open Paper file."""
    # Implementation that calls Paper's MCP server
    pass

@mcp.tool()
def create_rectangle(color: str, x: int, y: int, width: int, height: int):
    """Create a rectangle on the Paper canvas.
    
    Args:
        color: CSS color string (e.g., "red", "#ff0000")
        x: X position on canvas
        y: Y position on canvas
        width: Width in pixels
        height: Height in pixels
    """
    pass

mcp.run(transport="stdio")
```

### Building a Custom Agent (OpenAI Agents SDK Example)

```python
from agents import Agent, McpServerStdio
from openai import OpenAI

# Load MCP server
paper_server = McpServerStdio(
    name="paper",
    command="uv",
    args=["run", "mcp_server/paper_agent.py"]
)

# Get system prompt from MCP
instructions = get_system_prompt()

# Create agent
agent = Agent(
    name="Paper Design Agent",
    instructions=instructions,
    mcp_servers=[paper_server]
)

# Interact with agent
result = agent.run("Create a modern login form in Paper")
print(result)
```

### Key Design Principles for MCP Tools
1. **Write tool descriptions for agents, not humans** — explain when and why to use each tool
2. **Group tools by workflow, not API structure** — agents think in tasks
3. **Use consistent naming patterns** — `search_*`, `get_*`, `create_*`
4. **Include dependency tools** — provide the full chain (search → get → create → validate)
5. **Avoid "everything" toolsets** — focused toolsets prevent decision paralysis
6. **Provide workflow context in descriptions** — tell agents what comes before/after

---

## Pebble Watch Integration Considerations

Since Pebble watches have limited display and input, a custom agent using Paper MCP should:

1. **Use voice-driven prompts** — the agent interprets natural language requests
2. **Focus on high-level commands** — "make the header blue", "add a login form"
3. **Leverage read-only tools for status** — `get_basic_info`, `get_selection`, `get_screenshot` (view on phone)
4. **Use write tools for actions** — `write_html`, `update_styles`, `set_text_content`
5. **Chain with other MCPs** — Paper MCP is most powerful when combined with Figma MCP, Notion MCP, or other data sources
6. **Keep the Paper Desktop app running** — the MCP server is embedded in it

### Practical Pebble Workflow
```
Pebble Voice Command → Phone Agent → Paper MCP (localhost:29979) → Paper Desktop
     "Add a blue button"             
```

The phone acts as the MCP client/host, connecting to Paper Desktop's local MCP server. The Pebble initiates commands via voice or text input through the watch assistant.

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| MCP server not detected | Restart the agent (Cursor/Claude/etc.) |
| Agent says it can't access MCP | Restart agent session; toggle MCP off/on |
| Tool calling errors | Restart everything — LLMs occasionally hallucinate tool params |
| Windows WSL can't connect | Enable mirrored mode networking in WSL settings |
| MCP limits not reset after upgrade | Update Paper Desktop + restart app |
| Long-running sessions fail | Let agent sessions complete; start fresh sessions |

---

## Pricing

- **Free tier:** Limited MCP tool calls
- **Pro ($16/mo or $144/yr):** 1M MCP tool calls/week, 100x more image generations, video export, unlimited storage

---

## Sources
- [Paper MCP Official Docs](https://paper.design/docs/mcp)
- [GitHub: ripgrim/paper-mcp](https://github.com/ripgrim/paper-mcp)
- [Banani Blog: Paper.design Review](https://www.banani.co/blog/paper-design-mcp-review)
- [MCP Architecture](https://modelcontextprotocol.io/docs/learn/architecture)
- [MCP Specification](https://modelcontextprotocol.io/specification/2025-11-25)
- [SlideSpeak: Best Design MCP Servers](https://slidespeak.co/blog/best-design-mcp-servers)
- [YouTube: How to Build Custom AI Agents with MCP](https://www.youtube.com/watch?v=w-Ml3NivoFo)
- [Speakeasy: Design MCP Tools](https://www.speakeasy.com/mcp/tool-design)
