# LangAPI MCP Example: react-intl

Minimal example demonstrating LangAPI MCP server with react-intl (FormatJS).

## Project Structure

```
example-react-intl/
├── src/
│   └── lang/
│       ├── en.json      # Source locale (12 keys)
│       ├── de.json      # Partial target (3 keys)
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

Expected: Detects `react-intl` framework with `src/lang/*.json` pattern.

### 2. Check translation status
> "What translations are missing in German and French?"

Expected: Shows de missing 9 keys, fr missing all 12 keys.

### 3. Preview sync (dry run)
> "Show me what would be translated"

Expected: Shows delta preview with credit cost estimate.

### 4. Execute sync
> "Sync translations to German and French"

Expected: Translates missing keys and updates the JSON files.

## Framework Detection

This project is detected as `react-intl` because of:
- `src/lang/*.json` directory pattern
- Flat key structure with dot notation (`app.name`, `auth.login`)

## Key Structure

react-intl typically uses **flat keys** with dot notation:

```json
{
  "app.name": "My Application",
  "auth.login": "Log in"
}
```

This differs from nested structures used by other frameworks.
