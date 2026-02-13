# Craft Agents

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)

## How it Works (Video)
To understand what Craft Agents does and how it works watch this video.

[![Demo Video](https://img.youtube.com/vi/xQouiAIilvU/hqdefault.jpg)](https://www.youtube.com/watch?v=xQouiAIilvU)

[Click Here (or on the image above) to watch the video on YouTube →](https://www.youtube.com/watch?v=xQouiAIilvU)

## Installation

### One-Line Install (Recommended)

**macOS / Linux:**
```bash
curl -fsSL https://agents.craft.do/install-app.sh | bash
```

**Windows (PowerShell):**
```powershell
irm https://agents.craft.do/install-app.ps1 | iex
```

### Build from Source (Modified Version)

This version includes **support for custom OpenAI-compatible LLM providers** (Z.ai, DeepSeek, Groq, Together AI, etc.) through the Codex/OpenAI backend.

#### Quick Start (Windows)

```powershell
git clone https://github.com/lukilabs/craft-agents-oss.git
cd craft-agents-oss

# Automated build and install
.\scripts\build-and-install.bat
```

#### Manual Build

**Prerequisites:**
- **Bun** (JavaScript runtime) - [Install Bun](https://bun.sh)
- **Git** - [Install Git](https://git-scm.com/downloads)

**Windows:**
```powershell
git clone https://github.com/lukilabs/craft-agents-oss.git
cd craft-agents-oss
bun install
bun run electron:dist:win
.\install\install-local.ps1
```

**macOS:**
```bash
git clone https://github.com/lukilabs/craft-agents-oss.git
cd craft-agents-oss
bun install
bun run electron:dist:mac
# Open release/Craft-Agent-$(uname -m).dmg and drag to Applications
```

**Linux:**
```bash
git clone https://github.com/lukilabs/craft-agents-oss.git
cd craft-agents-oss
bun install
bun run electron:dist:linux
chmod +x release/Craft-Agent-x64.AppImage
./release/Craft-Agent-x64.AppImage
```

#### Development Mode

For development with hot reload:
```bash
git clone https://github.com/lukilabs/craft-agents-oss.git
cd craft-agents-oss
bun install
bun run electron:dev
```

### OpenAI-Compatible LLM Providers

This modified version adds support for **custom OpenAI-compatible endpoints** through the Codex/OpenAI provider. Configure providers like Z.ai, DeepSeek, Groq, and Together AI directly in the UI.

#### Setting Up a Custom Provider

1. **Launch Craft Agents** after installation
2. **Click "Set up your Agent"** or go to **Settings → AI Settings**
3. **Select "Codex"** from provider tabs (Claude, Codex, GitHub Copilot)
4. **Select "Codex · OpenAI API Key"** option
5. **Click "Endpoint" dropdown** and select **"Custom OpenAI-Compatible"**
6. **Enter your base URL** and **API key**
7. **Enter default model** and test the connection

#### Supported Providers

| Provider | Base URL | Default Models |
|----------|-----------|---------------|
| **Z.ai** | `https://api.z.ai/api/coding/paas/v4` | `glm-5`, `glm-4` |
| **DeepSeek** | `https://api.deepseek.com` | `deepseek-chat`, `deepseek-coder` |
| **Groq** | `https://api.groq.com/openai/v1` | `llama-3.3-70b-versatile` |
| **Together AI** | `https://api.together.xyz/v1` | Various (check docs) |
| **Any OpenAI-compatible API** | Your endpoint URL | Your model IDs |

#### Example: Z.ai GLM-5

```
Endpoint: https://api.z.ai/api/coding/paas/v4
Model: glm-5
```

#### Example: DeepSeek

```
Endpoint: https://api.deepseek.com
Model: deepseek-chat
```

#### Example: Groq

```
Endpoint: https://api.groq.com/openai/v1
Model: llama-3.3-70b-versatile
```

#### Multiple Models

You can specify multiple models as a comma-separated list. The first is the default, and the last is used for summarization:
```
glm-5, glm-4, glm-4-flash
```

**Documentation:** See `INSTALL.md` for complete setup guide, troubleshooting, and advanced configuration.

---

## Why Craft Agents was built
Craft Agents is a tool we built so that we (at craft.do) can work effectively with agents. It enables intuitive multitasking, no-fluff connection to any API or Service, sharing sessions, and a more document (vs code) centric workflow - in a beautiful and fluid UI.

It uses the Claude Agent SDK and Codex app-server side by side—building on what we found great and improving areas where we've desired improvements.

It's built with Agent Native software principles in mind, and is highly customisable out of box. One of the first of its kind.

Craft Agents is open source under the Apache 2.0 license - so you are free to remix, change anything. And that's actually possible. We ourselves are building Craft Agents with Craft Agents only - no code editors - so really, any customisation is just a prompt away.

We built Craft Agents because we wanted a better, more opinionated (and preferably non-CLI way) of working with the most powerful agents in the world. We'll continue to improve it, based on our experiences and intuition.

<img width="1578" height="894" alt="image" src="https://github.com/user-attachments/assets/3f1f2fe8-7cf6-4487-99ff-76f6c8c0a3fb" />

## Things that are hard to believe "just work"

**How do I connect to Linear, Gmail, Slack...?**
Tell the agent "add Linear as a source." It finds public APIs and MCP servers, reads their docs, sets up credentials, and configures everything. No config files, no setup wizards.

[Check out how I just connected to Slack →](https://agents.craft.do/s/DRNQEiy8w2e1v5LPgKl8b)

**I already have my MCP config JSON.**
Paste it. The agent handles the rest.

**What about local MCPs?**
Fully supported. Stdio-based MCP servers run as local subprocesses on your machine. Point it at an npx command, a Python script, or any local binary. It just works.

**Can it handle custom APIs?**
Yes. Paste an OpenAPI spec, some endpoint URLs, screenshots of docs, whatever you have. It figures it out and guides you through the rest.

**APIs too? Not just MCPs?**
Craft Agents connects to anything. We have it hooked up to a direct Postgres DB behind a jumpbox. Skills + Sources = magic.

**How do I import my Claude Code skills and MCPs?**
Tell the agent you want to import your skills from Claude Code. It handles the migration.

[Here I imported all my skills in one go →](https://agents.craft.do/s/gWCFqwhObFWaNJIEJmd6j)

**How do I create a new skill?**
Describe what the skill should do, give it context. The agent takes care of the rest.

**Do I need to restart after changes?**
No. Everything is instant. Mention new skills or sources with `@`, even mid-conversation.

**So I can just ask it anything?**
Yes. That's the core idea behind agent-native software. You describe what you want, and it figures out how. That's a good use of tokens.

## Features

- **Multi-Session Inbox**: Desktop app with session management, status workflow, and flagging
- **Claude Code Experience**: Streaming responses, tool visualization, real-time updates
- **Multiple LLM Connections**: Add multiple AI providers and set per-workspace defaults
- **Codex / OpenAI Support**: Run Codex-backed sessions alongside Anthropic
- **Craft MCP Integration**: Access to 32+ Craft document tools (blocks, collections, search, tasks)
- **Sources**: Connect to MCP servers, REST APIs (Google, Slack, Microsoft), and local filesystems
- **Permission Modes**: Three-level system (Explore, Ask to Edit, Auto) with customizable rules
- **Background Tasks**: Run long-running operations with progress tracking
- **Dynamic Status System**: Customizable session workflow states (Todo, In Progress, Done, etc.)
- **Theme System**: Cascading themes at app and workspace levels
- **Multi-File Diff**: VS Code-style window for viewing all file changes in a turn
- **Skills**: Specialized agent instructions stored per-workspace
- **File Attachments**: Drag-drop images, PDFs, Office documents with auto-conversion
- **Hooks**: Event-driven automation — run commands or create sessions on label changes, schedules, tool use, and more

## Quick Start

1. **Launch app** after installation
2. **Choose API Connection**: Use Anthropic (API key or Claude Max) or Codex (OpenAI OAuth)
3. **Create a workspace**: Set up a workspace to organize your sessions
4. **Connect sources** (optional): Add MCP servers, REST APIs, or local filesystems
5. **Start chatting**: Create sessions and interact with Claude

## Desktop App Features

### Session Management

- **Inbox/Archive**: Sessions organized by workflow status
- **Flagging**: Mark important sessions for quick access
- **Status Workflow**: Todo → In Progress → Needs Review → Done
- **Session Naming**: AI-generated titles or manual naming
- **Session Persistence**: Full conversation history saved to disk

### Sources

Connect external data sources to your workspace:

| Type | Examples |
|------|----------|
| **MCP Servers** | Craft, Linear, GitHub, Notion, custom servers |
| **REST APIs** | Google (Gmail, Calendar, Drive), Slack, Microsoft |
| **Local Files** | Filesystem, Obsidian vaults, Git repos |

### Permission Modes

| Mode | Display | Behavior |
|------|---------|----------|
| `safe` | Explore | Read-only, blocks all write operations |
| `ask` | Ask to Edit | Prompts for approval (default) |
| `allow-all` | Auto | Auto-approves all commands |

Use **SHIFT+TAB** to cycle through modes in the chat interface.

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Cmd+N` | New chat |
| `Cmd+1/2/3` | Focus sidebar/list/chat |
| `Cmd+/` | Keyboard shortcuts dialog |
| `SHIFT+TAB` | Cycle permission modes |
| `Enter` | Send message |
| `Shift+Enter` | New line |

## Architecture

```
craft-agent/
├── apps/
│   └── electron/              # Desktop GUI (primary)
│       └── src/
│           ├── main/          # Electron main process
│           ├── preload/       # Context bridge
│           └── renderer/      # React UI (Vite + shadcn)
└── packages/
    ├── core/                  # Shared types
    └── shared/                # Business logic
        └── src/
            ├── agent/         # CraftAgent, permissions
            ├── auth/          # OAuth, tokens
            ├── config/        # Storage, preferences, themes
            ├── credentials/   # AES-256-GCM encrypted storage
            ├── sessions/      # Session persistence
            ├── sources/       # MCP, API, local sources
            └── statuses/      # Dynamic status system
```

## Development

```bash
# Hot reload development
bun run electron:dev

# Build and run
bun run electron:start

# Type checking
bun run typecheck:all

# Debug logging (writes to ~/Library/Logs/Craft Agents/)
# Logs are automatically enabled in development
```

### Environment Variables

OAuth integrations (Slack, Microsoft) require credentials baked into the build. Create a `.env` file:

```bash
MICROSOFT_OAUTH_CLIENT_ID=your-client-id
SLACK_OAUTH_CLIENT_ID=your-slack-client-id
SLACK_OAUTH_CLIENT_SECRET=your-slack-client-secret
```

**Note:** Google OAuth credentials are NOT baked into the build. Users provide their own credentials via source configuration. See the [Google OAuth Setup](#google-oauth-setup-gmail-calendar-drive) section below.

### Google OAuth Setup (Gmail, Calendar, Drive)

Google integrations require you to create your own OAuth credentials. This is a one-time setup.

#### 1. Create a Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a new project (or select an existing one)
3. Note your Project ID

#### 2. Enable Required APIs

Go to **APIs & Services → Library** and enable the APIs you need:
- **Gmail API** - for email integration
- **Google Calendar API** - for calendar integration
- **Google Drive API** - for file storage integration

#### 3. Configure OAuth Consent Screen

1. Go to **APIs & Services → OAuth consent screen**
2. Select **External** user type (unless you have Google Workspace)
3. Fill in required fields:
   - App name: e.g., "My Craft Agent"
   - User support email: your email
   - Developer contact: your email
4. Add scopes (optional - can leave default)
5. Add yourself as a test user (required for External apps in testing mode)
6. Complete the wizard

#### 4. Create OAuth Credentials

1. Go to **APIs & Services → Credentials**
2. Click **Create Credentials → OAuth Client ID**
3. Application type: **Desktop app**
4. Name: e.g., "Craft Agent Desktop"
5. Click **Create**
6. Note the **Client ID** and **Client Secret**

#### 5. Configure in Craft Agent

When setting up a Google source (Gmail, Calendar, Drive), add these fields to your source's `config.json`:

```json
{
  "api": {
    "googleService": "gmail",
    "googleOAuthClientId": "your-client-id.apps.googleusercontent.com",
    "googleOAuthClientSecret": "your-client-secret"
  }
}
```

Or simply tell the agent you want to connect Gmail/Calendar/Drive - it will guide you through entering your credentials.

#### Security Notes

- Your OAuth credentials are stored encrypted alongside other source credentials
- Never commit credentials to version control
- For production use, consider getting your OAuth consent screen verified by Google

## Configure Third-Party Providers (OpenRouter, Vercel AI Gateway, Ollama, etc.)

Third-party and self-hosted LLM providers are supported through different backends depending on the API format:

### Claude Backend (Anthropic-Compatible)

For Anthropic-compatible APIs (OpenRouter, Vercel AI Gateway, Ollama), select **Anthropic API Key** during setup:

| Provider | Endpoint | Notes |
|----------|----------|-------|
| **OpenRouter** | `https://openrouter.ai/api` | Access Claude, GPT, Llama, Gemini, and hundreds of other models through a single API key. Use `provider/model-name` format (e.g. `anthropic/claude-opus-4.6`). |
| **Vercel AI Gateway** | `https://ai-gateway.vercel.sh` | Route requests through Vercel's AI Gateway with built-in observability and caching. |
| **Ollama** | `http://localhost:11434` | Run open-source models locally. No API key required. |
| **Custom Anthropic-Compatible** | Any URL | Any Anthropic-compatible endpoint using `/v1/messages`. |

### Codex Backend (OpenAI-Compatible)

**This modified version adds support for OpenAI-compatible APIs through the Codex provider.** Select **Codex · OpenAI API Key** during setup, then choose **"Custom OpenAI-Compatible"** from the Endpoint dropdown:

| Provider | Endpoint | Notes |
|----------|----------|-------|
| **Z.ai** | `https://api.z.ai/api/coding/paas/v4` | GLM-5, GLM-4 models |
| **DeepSeek** | `https://api.deepseek.com` | DeepSeek-Chat, DeepSeek-Coder |
| **Groq** | `https://api.groq.com/openai/v1` | Llama 3, Mixtral, Gemma |
| **Together AI** | `https://api.together.xyz/v1` | Various open-source models |
| **Custom OpenAI-Compatible** | Any URL | Any OpenAI-compatible endpoint using `/chat/completions`. |

### Why Two Backends?

Craft Agents uses two different agent backends:

- **Claude** — powered by [Claude Agent SDK](https://www.npmjs.com/package/@anthropic-ai/claude-agent-sdk), which natively supports custom base URLs and provider routing. Use this for Anthropic-compatible APIs.
- **Codex** — powered by [Codex app-server](https://github.com/lukilabs/craft-agents-codex), which communicates via JSON-RPC over stdio. **This modified version extends Codex to support custom OpenAI-compatible endpoints.**

Choose the appropriate backend based on your provider's API format:
- **Anthropic format** (`/v1/messages`) → Use **Claude** provider
- **OpenAI format** (`/chat/completions`) → Use **Codex** provider with **Custom OpenAI-Compatible** endpoint

## Configuration

Configuration is stored at `~/.craft-agent/`:

```
~/.craft-agent/
├── config.json              # Main config (workspaces, LLM connections)
├── credentials.enc          # Encrypted credentials (AES-256-GCM)
├── preferences.json         # User preferences
├── theme.json               # App-level theme
└── workspaces/
    └── {id}/
        ├── config.json      # Workspace settings
        ├── theme.json       # Workspace theme override
        ├── hooks.json       # Event-driven automation hooks
        ├── sessions/        # Session data (JSONL)
        ├── sources/         # Connected sources
        ├── skills/          # Custom skills
        └── statuses/        # Status configuration
```

### Hooks (Automation)

Hooks let you automate workflows by triggering actions when events happen — labels change, sessions start, tools run, or on a cron schedule.

**Just ask the agent:**
- "Set up a daily standup briefing every weekday at 9am"
- "Notify me when a session is labelled urgent"
- "Log all permission mode changes to a file"
- "Every Friday at 5pm, summarise this week's completed tasks"

Or configure manually in `~/.craft-agent/workspaces/{id}/hooks.json`:

```json
{
  "version": 1,
  "hooks": {
    "SchedulerTick": [
      {
        "cron": "0 9 * * 1-5",
        "timezone": "America/New_York",
        "labels": ["Scheduled"],
        "hooks": [
          { "type": "prompt", "prompt": "Check @github for new issues assigned to me" }
        ]
      }
    ],
    "LabelAdd": [
      {
        "matcher": "^urgent$",
        "permissionMode": "allow-all",
        "hooks": [
          { "type": "command", "command": "osascript -e 'display notification \"Urgent session\" with title \"Craft Agent\"'" }
        ]
      }
    ]
  }
}
```

**Two hook types:**
- **Command hooks** — run shell commands with event data as environment variables (`$CRAFT_LABEL`, `$CRAFT_SESSION_ID`, etc.)
- **Prompt hooks** — create a new agent session with a prompt (supports `@mentions` for sources and skills)

**Supported events:** `LabelAdd`, `LabelRemove`, `PermissionModeChange`, `FlagChange`, `TodoStateChange`, `SchedulerTick`, `PreToolUse`, `PostToolUse`, `SessionStart`, `SessionEnd`, and more.

See the [Hooks documentation](https://agents.craft.do/docs/hooks/overview) for full reference.

## Advanced Features

### Large Response Handling

Tool responses exceeding ~60KB are automatically summarized using Claude Haiku with intent-aware context. The `_intent` field is injected into MCP tool schemas to preserve summarization focus.

### Deep Linking

External apps can navigate using `craftagents://` URLs:

```
craftagents://allSessions                      # All sessions view
craftagents://allSessions/session/session123   # Specific session
craftagents://settings                         # Settings
craftagents://sources/source/github            # Source info
craftagents://action/new-chat                  # Create new session
```

## Tech Stack

| Layer | Technology |
|-------|------------|
| Runtime | [Bun](https://bun.sh/) |
| AI | [@anthropic-ai/claude-agent-sdk](https://www.npmjs.com/package/@anthropic-ai/claude-agent-sdk) |
| AI (OpenAI) | Craft Agents Codex fork (app-server) |
| Desktop | [Electron](https://www.electronjs.org/) + React |
| UI | [shadcn/ui](https://ui.shadcn.com/) + Tailwind CSS v4 |
| Build | esbuild (main) + Vite (renderer) |
| Credentials | AES-256-GCM encrypted file storage |

## Troubleshooting

### Debug Mode

To launch the packaged app with verbose logging enabled, use `-- --debug` (note the double dash separator):

**macOS:**
```bash
/Applications/Craft\ Agents.app/Contents/MacOS/Craft\ Agents -- --debug
```

**Windows (PowerShell):**
```powershell
& "$env:LOCALAPPDATA\Programs\@craft-agentelectron\Craft Agents.exe" -- --debug
```

**Linux:**
```bash
./craft-agents -- --debug
```

Logs are written to:
- **macOS:** `~/Library/Logs/@craft-agent/electron/main.log`
- **Windows:** `%APPDATA%\@craft-agent\electron\logs\main.log`
- **Linux:** `~/.config/@craft-agent/electron/logs/main.log`

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

### Third-Party Licenses

This project uses [Claude Agent SDK](https://www.npmjs.com/package/@anthropic-ai/claude-agent-sdk), which is subject to [Anthropic's Commercial Terms of Service](https://www.anthropic.com/legal/commercial-terms).

Craft Agents also bundles a custom Codex app-server fork to support OpenAI/Codex connections:

- https://github.com/lukilabs/craft-agents-codex

### Trademark

"Craft" and "Craft Agents" are trademarks of Craft Docs Ltd. See [TRADEMARK.md](TRADEMARK.md) for usage guidelines.

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Security

### Local MCP Server Isolation

When spawning local MCP servers (stdio transport), sensitive environment variables are filtered out to prevent credential leakage to subprocesses. Blocked variables include:

- `ANTHROPIC_API_KEY`, `CLAUDE_CODE_OAUTH_TOKEN` (app auth)
- `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_SESSION_TOKEN`
- `GITHUB_TOKEN`, `GH_TOKEN`, `OPENAI_API_KEY`, `GOOGLE_API_KEY`, `STRIPE_SECRET_KEY`, `NPM_TOKEN`

To explicitly pass an env var to a specific MCP server, use the `env` field in the source config.

To report security vulnerabilities, please see [SECURITY.md](SECURITY.md).