# Perplexity CLI

A beautiful, feature-rich command-line tool for querying the Perplexity API directly from your terminal.

![demo](https://img.shields.io/badge/interface-CLI-blue)
![python](https://img.shields.io/badge/python-3.8+-green)
![license](https://img.shields.io/badge/license-MIT-purple)

## Features

- **Beautiful Terminal UI** - ASCII art banner, colored output, status bars, and formatted messages
- **Interactive Chat Mode** - Full REPL with slash commands and conversation history
- **Markdown Formatting** - Supports bold, italic, code blocks, headers, and lists
- **Rich Text Output** - Syntax highlighting, colored code blocks, and styled links
- **Stream Responses** - Watch answers generate in real-time with word wrapping
- **Save/Load Conversations** - Persist chats in `~/.cache/perplexity/`
- **Export to Markdown** - Export conversations as clean `.md` files
- **Custom System Prompts** - Customize the assistant's behavior
- **Citations Support** - View source citations for research answers
- **Environment Variables** - Use `.env` file for secure API key management

## Installation

1. Copy the `perplexity` script to your local bin directory:
```bash
cp perplexity ~/.local/bin/
chmod +x ~/.local/bin/perplexity
```

2. Make sure `~/.local/bin` is in your PATH:
```bash
export PATH="$HOME/.local/bin:$PATH"
```

3. Install dependencies:
```bash
pip install openai python-dotenv
```

## Setup

### Option 1: Environment Variable
```bash
export PERPLEXITY_API_KEY="your-api-key-here"
```

### Option 2: .env File (Recommended)
Create `~/.perplexity/.env` with:
```bash
mkdir -p ~/.perplexity
cat > ~/.perplexity/.env << 'EOF'
PERPLEXITY_API_KEY=your-api-key-here
EOF
```

Get your API key from: https://www.perplexity.ai/settings/api

## Usage

### Interactive Chat Mode

Start an interactive chat session with a beautiful terminal interface:

```bash
perplexity --chat
# or
perplexity -c
```

**Slash Commands:**

| Command | Description |
|---------|-------------|
| `/help` | Show interactive help box |
| `/clear` | Clear conversation history |
| `/save` | Save current conversation |
| `/export` | Export conversation to Markdown |
| `/history` | List all saved conversations |
| `/load` | Load a saved conversation |
| `/status` | Show current session info |
| `/quit` | Exit chat mode |
| `/exit` | Exit chat mode |
| `/q` | Exit chat mode |

**Keyboard Shortcuts:**
- `Ctrl+C` - Interrupt current response
- `Ctrl+D` - Exit chat mode

### Single Query Mode

```bash
perplexity "your question here"
```

Examples:
```bash
perplexity "What is the capital of France?"
perplexity "Latest AI developments" --search
perplexity "Explain quantum computing" --stream
perplexity "Help debug my Python code" --system "You are a coding expert"
```

## Options

| Option | Short | Description |
|--------|-------|-------------|
| `query` | - | Your question or search query |
| `--chat` | `-c` | Enter interactive chat mode |
| `--model` | - | Model: `sonar-pro`, `sonar-medium-online`, `sonar-small-online` |
| `--search` | - | Use research-focused mode |
| `--stream` | - | Stream responses in real-time |
| `--system` | `-s` | Custom system prompt |
| `--api-key` | - | Override API key |
| `--no-color` | - | Disable colored output |

## Models

- **sonar-pro**: Best for general queries with web citations (default)
- **sonar-medium-online**: Faster responses
- **sonar-small-online**: Fastest responses

## Examples

### Quick Question
```bash
$ perplexity "What is the capital of Australia?"
```

### Research with Citations
```bash
$ perplexity "Latest developments in AI agents" --search
```

### Streaming Response
```bash
$ perplexity "Explain quantum entanglement" --stream
```

### Custom System Prompt
```bash
$ perplexity --chat --system "You are a sarcastic comedian"
```

### Interactive with Streaming
```bash
$ perplexity --chat --stream --model sonar-medium-online
```

## Conversation History

Conversations are saved to `~/.cache/perplexity/` as JSON files.

**Access during chat:**
```bash
You: /history

📂 Saved Conversations
  • chat_20240203_153045.json (5 msgs) - 2024-02-03T15:30:45
  • chat_20240203_140000.json (12 msgs) - 2024-02-03T14:00:00

You: /load

[1] chat_20240203_153045.json (5 msgs)
[2] chat_20240203_140000.json (12 msgs)

Load which one? (number or 'cancel'): 1
✓ Loaded 5 messages.
```

**Export Example:**
```bash
You: /export
Output filename (e.g. chat.md): my_research.md
✓ Exported to: my_research.md
```

## Terminal Interface

### Welcome Screen
```
   __  __                    _
  / / / /___  ____ ___  ____/ /___ _
 / /_/ / __ \/ __ `__ "/ __  / __ `/
/ __  / /_/ / / / / / / /_/ / /_/ /
/_/ /_/\____/_/ /_/ /_/\__,_/\__,_/

━━━  Model: sonar-pro                    2024-02-03 03:30 PM  ━━━

Commands:
  /help       Show this help
  /clear      Clear conversation history
  /save       Save current conversation
  /export     Export to Markdown
  /history    List saved conversations
  /load       Load a saved conversation
  /status     Show current session info
  /quit       Exit chat mode
```

### Styled Messages
```
┌─ You ───────────────────────────────────────────────
│ What is quantum computing?
└─────────────────────────────────────────────────────

┌─ Perplexity ───────────────────────────────────────
│ Quantum computing is a revolutionary field that uses
│ quantum mechanics to process information in ways
│ classical computers cannot...
└─────────────────────────────────────────────────────

📚 Sources
  [1] https://example.com/quantum-intro
  [2] https://example.com/qubits-explained
```

## Tips

- Use `--system` to create different AI personas (e.g., "You are a sarcastic comedian")
- In chat mode, press Ctrl+C to interrupt a long response
- Use `--stream` for a more interactive experience
- Chat with `--search` for complex research topics
- Type `/help` anytime during chat to see all commands

## Screenshots

Coming soon! Run `perplexity --chat` to see the beautiful interface in action.

## License

MIT

## Contributing

Contributions welcome! Feel free to open issues or pull requests.
