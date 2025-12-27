# Nexus-AI

Nexus-AI is an intelligent automation platform powered by Claude AI.

## Requirements

- **Python** 3.9 or higher
- **Node.js** 16 or higher
- **npm** (comes with Node.js)
- **Claude API key** (for Claude integration)
- **OpenAI API key** (for OpenAI integration)

## Prerequisites & Installation

### 1. Install Python

Download and install Python from [python.org](https://www.python.org/downloads/) or use a package manager:

```bash
# macOS with Homebrew
brew install python3

# Verify installation
python3 --version
```

### 2. Install Node.js & npm

```bash
# macOS with Homebrew
brew install node

# Verify installation
node --version
npm --version
```

### 3. Install uv (Python package manager)

```bash
# macOS with Homebrew
brew install uv

# Verify installation
uv --version
```

### 4. Install Claude Desktop

Download and install Claude Desktop from [Claude.ai](https://claude.ai) or use Homebrew:

```bash
# macOS with Homebrew
brew install --cask claude
```

### 5. Generate API Keys

#### Claude API Key
1. Visit [console.anthropic.com](https://console.anthropic.com)
2. Generate a new API key and save it securely

#### OpenAI API Key (Optional)
1. Visit [platform.openai.com](https://platform.openai.com)
2. Generate a new API key and save it securely

### 6. Environment Setup

Create a `.env` file in the project root and add your API keys:

```bash
CLAUDE_API_KEY=your_claude_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
```



## Project Setup Workflow

### 1. Create and Initialize the Client Environment

```bash
mkdir client
cd client
uv init
uv venv
uv add "mcp[cli]"
source .venv/bin/activate
```

### 2. Add Your Code

- Implement your MCP client in `client.py`.
- Implement your MCP server in `weather.py`.

### 3. Run the Client

```bash
uv run client.py
```

### 4. (Optional) Install MCP Inspector for Debugging


```bash
npm install -g @modelcontextprotocol/inspector@0.18.0
```

To run the MCP Inspector with your server:

```bash
mcp dev local.py
```


### 5. Configure Claude Desktop to Use Your MCP Server

Instead of running `mcp dev`, you can configure Claude Desktop to launch your MCP server automatically. Add the following to your Claude MCP config and restart Claude Desktop:

```json
{
  "mcpServers": {
    "LocalNotes": {
      "command": "uv",
      "args": [
        "--directory",
        "<path-to-your-project>/mcp-deep-dive",
        "run",
        "local.py"
      ]
    }
  }
}
```

This will allow Claude Desktop to start and connect to your MCP server automatically.
