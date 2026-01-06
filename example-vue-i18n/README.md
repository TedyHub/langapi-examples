# LangAPI MCP Example: vue-i18n

Minimal example demonstrating LangAPI MCP server with Vue 3 and vue-i18n.

## Project Structure

```
example-vue-i18n/
├── src/
│   └── locales/
│       ├── en.json      # Source locale (14 keys)
│       ├── de.json      # Partial target (4 keys)
│       └── fr.json      # Empty target
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

Expected: Detects `vue-i18n` framework with `src/locales/*.json` pattern.

### 2. Check translation status
> "What translations are missing in German and French?"

Expected: Shows de missing 10 keys, fr missing all 14 keys.

### 3. Preview sync (dry run)
> "Show me what would be translated"

Expected: Shows delta preview with credit cost estimate.

### 4. Execute sync
> "Sync translations to German and French"

Expected: Translates missing keys and updates the JSON files.

## Framework Detection

This project is detected as `vue-i18n` because of:
- `src/locales/*.json` directory pattern
- `vue-i18n` dependency in package.json

## Key Structure

vue-i18n typically uses **nested keys**:

```json
{
  "app": {
    "name": "My Application"
  },
  "auth": {
    "login": "Log in"
  }
}
```

This is the same nested structure used by next-intl and other frameworks.
