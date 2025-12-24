# LangAPI MCP Example: i18next

Minimal example demonstrating LangAPI MCP server with i18next (next-i18next).

## Project Structure

```
example-i18next/
├── public/
│   └── locales/
│       ├── en/
│       │   ├── common.json    # 6 keys
│       │   └── home.json      # 8 keys (including nested)
│       ├── de/
│       │   └── common.json    # 2 keys (missing 4)
│       └── fr/                # Empty - all missing
├── next-i18next.config.js
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

Expected: Detects `i18next` framework with `public/locales/*/*.json` pattern.

### 2. Check translation status
> "What translations are missing?"

Expected: Shows de and fr are missing multiple keys across namespaces.

### 3. Preview sync (dry run)
> "Preview what would be translated"

Expected: Shows delta with namespace breakdown and credit cost.

### 4. Execute sync
> "Sync all translations"

Expected: Creates missing namespace files and translates all keys.

## Framework Detection

This project is detected as `i18next` because of:
- `public/locales/*/*.json` directory pattern (namespace-based)
- `next-i18next.config.js` configuration file

## Namespace Structure

i18next uses **namespaces** (separate files per feature):

| Namespace | Keys | Purpose |
|-----------|------|---------|
| `common` | 6 | Shared UI strings |
| `home` | 8 | Home page content |

**Note:** Nested keys like `features.heading` are flattened for translation.
