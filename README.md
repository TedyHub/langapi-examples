# LangAPI MCP Server Examples

Example projects demonstrating the `@langapi/mcp-server` with different i18n frameworks.

## Examples

| Example | Framework | Pattern | Status |
|---------|-----------|---------|--------|
| [example-next-intl](./example-next-intl) | next-intl | `messages/*.json` | Ready |
| [example-i18next](./example-i18next) | i18next | `public/locales/*/*.json` | Ready |
| [example-react-intl](./example-react-intl) | react-intl | `src/lang/*.json` | Ready |
| [example-generic](./example-generic) | generic | `locales/*.json` | Ready |
| [example-vue-i18n](./example-vue-i18n) | vue-i18n | `src/locales/*.json` | Ready |
| [example-flutter-arb](./example-flutter-arb) | flutter | `lib/l10n/app_*.arb` | Ready |

## Quick Start

### 1. Install MCP Server

```bash
npm install -g @langapi/mcp-server
```

### 2. Get API Key

Sign up at [langapi.io](https://langapi.io) and get your API key from the dashboard.

### 3. Configure Your AI Tool

**Claude Desktop** (`~/.config/claude/claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "langapi": {
      "command": "npx",
      "args": ["@langapi/mcp-server"],
      "env": {
        "LANGAPI_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

**Cursor** (`.cursor/mcp.json` in project root):
```json
{
  "mcpServers": {
    "langapi": {
      "command": "npx",
      "args": ["@langapi/mcp-server"],
      "env": {
        "LANGAPI_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### 4. Try an Example

```bash
cd example-next-intl
```

Then ask your AI:
- "List the locale files in this project"
- "What translations are missing?"
- "Sync translations to German and French"

## MCP Tools

The server provides 3 tools:

| Tool | Description |
|------|-------------|
| `list_local_locales` | Scan project for locale files, detect framework |
| `get_translation_status` | Compare source vs target, show missing keys |
| `sync_translations` | Translate and sync missing keys (dry_run default) |

## Pricing

- **Free trial:** 2,000 credits (words)
- **Top-up:** $15 for 100,000 credits
- **No subscription, no expiry**

1 credit = 1 word translated

## Links

- [LangAPI Dashboard](https://langapi.io/dashboard)
- [MCP Server on npm](https://www.npmjs.com/package/@langapi/mcp-server)
- [Documentation](https://langapi.io/docs)

## License

MIT
