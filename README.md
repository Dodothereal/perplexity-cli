# Perplexity CLI

> A beautiful, feature-rich command-line interface for the Perplexity AI API

[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![CLI](https://img.shields.io/badge/interface-CLI-purple.svg)](https://github.com/Dodothereal/perplexity-cli)

![Demo](assets/demo.png)

## ✨ Features

- **Beautiful Terminal UI** - ASCII art banner, colored output, status bars, and formatted messages
- **Interactive Chat Mode** - Full REPL with slash commands and conversation history
- **Markdown Formatting** - Supports bold, italic, code blocks, headers, and lists
- **Rich Text Output** - Syntax highlighting, colored code blocks, and styled links
- **Real-time Streaming** - Watch answers generate with proper word wrapping
- **Conversation Persistence** - Save/load chats and export to Markdown
- **Custom System Prompts** - Create custom AI personas
- **Citations Support** - View source citations for research answers
- **Secure API Keys** - `.env` file support for secure API key management

## 🚀 Quick Start

```bash
# Install dependencies
pip install openai python-dotenv

# Copy the script
cp perplexity ~/.local/bin/perplexity
chmod +x ~/.local/bin/perplexity

# Add to PATH (if not already)
export PATH="$HOME/.local/bin:$PATH"

# Start chatting!
perplexity --chat
```

## ⚙️ Setup

### API Key

Get your API key from [perplexity.ai/settings/api](https://www.perplexity.ai/settings/api)

#### Option 1: Environment Variable
```bash
export PERPLEXITY_API_KEY="your-api-key-here"
```

#### Option 2: .env File (Recommended)
```bash
mkdir -p ~/.perplexity
cat > ~/.perplexity/.env << 'EOF'
PERPLEXITY_API_KEY=your-api-key-here
EOF
```

## 📖 Usage

### Interactive Chat

```bash
perplexity --chat      # or -c
perplexity --chat --stream
perplexity --chat --model sonar-medium-online
perplexity --chat --system "You are a sarcastic comedian"
```

### Single Query

```bash
perplexity "What is the capital of France?"
perplexity "Explain quantum physics" --stream
perplexity "Latest AI news" --search
perplexity "Debug this code" --system "You are a Python expert"
```

## 🎮 Interactive Commands

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

## 🔧 Options

| Option | Short | Description | Default |
|--------|-------|-------------|---------|
| `query` | - | Your question or search query | - |
| `--chat` | `-c` | Enter interactive chat mode | - |
| `--model` | - | Model to use | `sonar-pro` |
| `--search` | - | Use research-focused mode | - |
| `--stream` | - | Stream responses in real-time | - |
| `--system` | `-s` | Custom system prompt | - |
| `--api-key` | - | Override API key | - |
| `--no-color` | - | Disable colored output | - |

## 🤖 Available Models

| Model | Best For | Speed |
|-------|----------|-------|
| `sonar-pro` | General queries with web citations | ⭐⭐ |
| `sonar-medium-online` | Faster responses | ⭐⭐⭐ |
| `sonar-small-online` | Quick answers | ⭐⭐⭐⭐ |

## 💡 Examples

### Quick Question
```bash
$ perplexity "What is the capital of Australia?"

┌─ Perplexity ───────────────────────────────────────
│ Canberra, located in the Australian Capital Territory.
└─────────────────────────────────────────────────────
```

### Research with Citations
```bash
$ perplexity "Latest developments in AI agents" --search

┌─ Perplexity ───────────────────────────────────────
│ AI agents are evolving rapidly with new capabilities...

📚 Sources
  [1] https://perplexity.ai/blog/ai-agents
  [2] https://openai.com/research/agents
└─────────────────────────────────────────────────────
```

### Custom Persona
```bash
$ perplexity -s "You are a sarcastic pirate captain" "Tell me a joke"

┌─ Perplexity ───────────────────────────────────────
│ Arrr, why did the pirate go to medical school?
│ Because he wanted to study "arrr-thritis", ye scallywag!
└─────────────────────────────────────────────────────
```

## 💾 Conversation History

Conversations are saved automatically to `~/.cache/perplexity/` as JSON files.

### Managing Conversations

```bash
# List saved conversations
You: /history

📂 Saved Conversations
  • chat_20240203_153045.json (5 msgs) - 2024-02-03T15:30:45
  • chat_20240203_140000.json (12 msgs) - 2024-02-03T14:00:00

# Load a conversation
You: /load

[1] chat_20240203_153045.json (5 msgs)
[2] chat_20240203_140000.json (12 msgs)

Load which one? (number or 'cancel'): 1
✓ Loaded 5 messages.

# Export to Markdown
You: /export
Output filename (e.g. chat.md): my_research.md
✓ Exported to: my_research.md
```

## 🎨 Terminal Interface

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

## 📁 File Locations

| File/Folder | Location | Purpose |
|-------------|----------|---------|
| `.env` | `~/.perplexity/.env` | API key configuration |
| Conversations | `~/.cache/perplexity/` | Saved chat history |
| Script | `~/.local/bin/perplexity` | CLI executable |

## 💬 Tips & Tricks

- **Custom Personas**: Use `--system` to create different AI personalities
  - `"You are a sarcastic comedian"`
  - `"You are a senior code reviewer"`
  - `"You explain things like I'm 5"`

- **Faster Responses**: Use `sonar-small-online` for quick answers

- **Interrupting**: Press `Ctrl+C` to interrupt long responses

- **Research**: Use `--search` for complex topics requiring citations

- **Documentation**: Export chats to Markdown for documentation

## 🐛 Troubleshooting

### API Key Not Found
```bash
Error: API key not found. Set PERPLEXITY_API_KEY or create ~/.perplexity/.env
```
**Solution**: Create an `.env` file or set the environment variable.

### Module Not Found
```bash
ModuleNotFoundError: No module named 'openai'
```
**Solution**: Install dependencies with `pip install openai python-dotenv`

### Colors Not Showing
Colors are automatically disabled when piping to a file or using `--no-color`.

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Open an issue for bugs or feature requests
- Submit a pull request with improvements
- Share your creative prompt ideas

## 🙏 Credits

- Built with [Perplexity AI API](https://www.perplexity.ai/)
- Inspired by [Ollama CLI](https://ollama.com/)
- ASCII art generated with `figlet`

---

**Made with ♥ by [Dodothereal](https://github.com/Dodothereal)**
