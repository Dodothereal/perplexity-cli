# Perplexity CLI

A feature-rich command-line tool for querying the Perplexity API directly from your terminal.

## Features

- **Single Query Mode**: Ask questions and get answers quickly
- **Interactive Chat Mode**: Full conversation support with message history
- **Colored Output**: Beautiful, readable formatted responses
- **Stream Responses**: Watch answers generate in real-time
- **Save/Load Conversations**: Persist your chats and resume later
- **Export to Markdown**: Save conversations as Markdown files
- **Custom System Prompts**: Customize the assistant's behavior
- **Citations Support**: View source citations for researched answers

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

3. Install the OpenAI Python client:
```bash
pip install openai
```

## Setup

Set your Perplexity API key as an environment variable:
```bash
export PERPLEXITY_API_KEY="your-api-key-here"
```

Get your API key from: https://www.perplexity.ai/settings/api

## Usage

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

### Interactive Chat Mode

Start an interactive chat session:

```bash
perplexity --chat
# or
perplexity -c
```

**Interactive Commands:**

| Command | Description |
|---------|-------------|
| `quit` / `exit` / `q` | Exit chat mode |
| `clear` | Clear conversation history |
| `save` | Save current conversation |
| `export` | Export conversation to Markdown |
| `history` | List all saved conversations |
| `load` | Load a saved conversation |

## Options

| Option | Short | Description |
|--------|-------|-------------|
| `query` | - | Your question or search query |
| `--chat` | `-c` | Enter interactive chat mode |
| `--model` | - | Model to use: `sonar-pro`, `sonar-medium-online`, `sonar-small-online` (default: sonar-pro) |
| `--search` | - | Use research-focused mode with citations |
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
$ perplexity "Review this code" -s "You are a senior code reviewer focusing on best practices" --chat
```

### Interactive Chat with Custom Model

```bash
$ perplexity --chat --model sonar-medium-online --stream
```

## Conversation History

Conversations are saved to `~/.cache/perplexity/` as JSON files. You can:

1. **Save** during chat by typing `save`
2. **List** all saved conversations with `history`
3. **Load** a previous conversation with `load`
4. **Export** to Markdown with `export`

### Export Example

```bash
You: export
Output filename (e.g. chat.md): my_research.md
Exported to: my_research.md
```

## Tips

- Use `--system` to customize the assistant's personality (e.g., "You are a sarcastic comedian")
- In chat mode, press Ctrl+C to interrupt a response
- Use `--stream` for a more interactive experience in both modes
- Chat with `--search` for complex research topics

## License

MIT
