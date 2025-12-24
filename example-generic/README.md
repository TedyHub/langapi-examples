# LangAPI MCP Example: Generic JSON

Minimal example demonstrating LangAPI MCP server with generic JSON-based translations (framework-agnostic).

## Project Structure

```
example-generic/
├── locales/
│   ├── en.json      # Source locale (14 keys)
│   ├── de.json      # Partial target (4 keys)
│   └── fr.json      # Empty target
└── package.json
```

## Setup

1. Configure MCP server in Claude Desktop or Cursor:

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

2. Get your API key from [LangAPI Dashboard](https://langapi.io/dashboard/api-keys)

## Try It

Open this project in Cursor or use Claude Desktop, then try these prompts:

### 1. Detect locales
> "List the locale files in this project"

Expected: Detects `generic` framework with `locales/*.json` pattern.

### 2. Check translation status
> "What translations are missing?"

Expected: Shows de missing 10 keys, fr missing all 14 keys.

### 3. Preview sync (dry run)
> "Show me what would be translated to German and French"

Expected: Shows delta preview with credit cost estimate.

### 4. Execute sync
> "Sync translations"

Expected: Translates missing keys and updates the JSON files.

## Framework Detection

This project is detected as `generic` because of:
- `locales/*.json` directory pattern
- No framework-specific config files detected

## When to Use Generic

Use the generic pattern when:
- Building a custom i18n solution
- Using a framework not specifically supported
- Simple JSON-based translation needs
- Backend services with translation files

The MCP server will still detect languages from filenames and handle nested JSON structures correctly.
