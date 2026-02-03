# Perplexity CLI

A simple command-line tool for querying the Perplexity API directly from your terminal.

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

To make this permanent, add it to your shell config (`~/.zshrc` or `~/.bashrc`).

Get your API key from: https://www.perplexity.ai/settings/api

## Usage

```bash
perplexity "your question here"
```

### Examples

```bash
perplexity "What is the capital of France?"
perplexity "Latest AI developments" --search
perplexity "Explain quantum computing" --model sonar-pro
perplexity "Climate change solutions" --stream
```

### Options

| Option | Description |
|--------|-------------|
| `query` | Your question or search query (required) |
| `--model` | Model to use: `sonar-pro`, `sonar-medium-online`, `sonar-small-online` (default: sonar-pro) |
| `--search` | Use research-focused mode with detailed citations |
| `--stream` | Stream the response as it comes in |
| `--api-key` | Override API key (defaults to PERPLEXITY_API_KEY env var) |

### Models

- **sonar-pro**: Best for general queries with web citations
- **sonar-medium-online**: Faster responses
- **sonar-small-online**: Fastest responses

## Example Output

```bash
$ perplexity "What is the capital of France?"

The capital of France is Paris. Paris is located in the north-central part of France along the Seine River...
```

## License

MIT
