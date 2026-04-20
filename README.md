# GameLabs Studio MCP - AI Sprite & Game Asset Toolkit

Generate production-ready 2D game assets — images, animations, and sprite sheets — directly from your AI coding assistant using the Model Context Protocol. Go from text prompt to game-ready sprite sheet without leaving your editor.

## Quick Start

Visit the setup guide at: **[https://gamelabstudio.co/blog/mcp-setup-guide](https://gamelabstudio.co/blog/mcp-setup-guide)******

The setup page provides:
- One-click configuration for your AI coding assistant
- Copy-paste config for every supported client
- Instant test to verify your connection

  <img width="1180" height="813" alt="image" src="https://github.com/user-attachments/assets/589d61a8-e56e-4993-83ae-6b364e42bd7d" />

## Use Cases

Build complete game art pipelines from a single conversation:

- **2D platformers** — generate characters, animate them, export spritesheets
- **Top-down RPGs** — create tilesets, items, and NPCs with isometric views
- **Visual novels** — produce character portraits in any art style
- **Mobile games** — generate transparent-background assets ready for any engine
- **Rapid prototyping** — go from idea to playable art in minutes, not days

## Supported AI Assistants

### Featured Clients
- **Cursor** — Full MCP integration
- **Claude Desktop** — Native MCP support
- **Claude Code** — CLI tool with MCP support
- **VS Code** — Native MCP support in v1.102+
- **Windsurf** — Full MCP integration
- **Gemini CLI** — Command-line AI assistant

### Additional Clients
- Zed
- Cline (VS Code extension)
- Continue
- BoltAI
- LM Studio
- And any other MCP-compatible client

## Available Tools

### Generate Image
Create game art in any style — pixel art, cartoon, photorealistic, isometric, and more:
```
generate_image(
  prompt="warrior character with a flaming sword, pixel art style",
  transparent_bg=True,
  centered=True
)
```
Supports reference images, custom dimensions, camera/subject orientation, chroma keying, and 2D/isometric modes.

### Generate Video / Animation
Animate any image into a loopable video clip:
```
generate_video(
  prompt="idle breathing animation",
  source_image_job_id="<job_id from generate_image>",
  loopable=True
)
```
Chain from a completed image job or upload your own source frame.

### Generate Spritesheet
Extract a spritesheet from any animation — game-engine ready:
```
generate_spritesheet(
  source_video_job_id="<job_id from generate_video>",
  fps=12,
  length_seconds=2
)
```
Configure rows, columns, padding, and chroma key settings for clean transparency.

### Project & Asset Management
Organize everything in your GameLabs Studio workspace:
```
list_projects()
create_project(name="My Platformer")
list_assets(project_id=1)
create_asset(project_id=1, name="Hero Character")
```
Assets are auto-created and linked when you generate — no manual setup required.

### Job Status & Downloads
Poll generation progress and retrieve finished artifacts:
```
get_job_status(job_id="...")
download_job_artifact(job_id="...", sequence=0)
download_owned_asset(asset_id=1, kind="spritesheet")
```

## Recommended Workflow

The full image-to-spritesheet pipeline in three steps:

1. **`generate_image`** — create the base artwork
2. **`generate_video`** — animate it using `source_image_job_id` from step 1
3. **`generate_spritesheet`** — extract frames using `source_video_job_id` from step 2

Pass the same `asset_id` across all three steps to keep everything organized under a single asset. If you omit `project_id` and `asset_id`, a default "MCP Creations" project and a new asset are created automatically.

## What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io) (MCP) is an open standard that lets AI assistants interact with external tools and services. GameLabs Studio's MCP server gives your assistant the ability to generate images, animate them, and export spritesheets — all through natural language within your code editor.

## Manual Configuration

Add this to your MCP client configuration:

```json
{
  "mcpServers": {
    "gamelabs": {
      "url": "https://mcp.gamelabstudio.co/sse",
      "transport": "sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Get your API key from your [GameLabs Studio dashboard](https://gamelabstudio.co/app/mcp).

## Getting Started

1. **Sign up** at [gamelabstudio.co](https://gamelabstudio.co) and grab your API key
2. **Pick your AI assistant** from the supported clients above
3. **Configure** using the [setup guide](https://gamelabstudio.co/blog/mcp-setup-guide) or the manual config
4. **Start generating** — ask your assistant to *"create a pixel art knight and animate a walk cycle"*

## Support & Community

- **FAQ**: [https://gamelabstudio.co/faq](https://gamelabstudio.co/faq)
- **Issues**: [GitHub Issues](https://github.com/macuseri686/gamelab-studio-mcp/issues)
- **MCP Protocol**: [modelcontextprotocol.io](https://modelcontextprotocol.io)

## License

Copyright © 2026 GameLabs Studio. All rights reserved.

---

Built for indie game developers, hobbyists, and anyone who wants to turn ideas into game-ready art with AI.
