# LangAPI MCP Example: next-intl

Minimal example demonstrating LangAPI MCP server with Next.js and next-intl.

## Project Structure

```
example-next-intl/
├── messages/
│   ├── en.json      # Source locale (14 keys)
│   ├── de.json      # Partial target (4 keys - missing 10)
│   └── fr.json      # Empty target (missing all 14)
├── next.config.js   # Next.js config with next-intl plugin
├── i18n.ts          # next-intl configuration
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

Expected: Detects `next-intl` framework with `messages/` directory pattern.

### 2. Check translation status
> "What translations are missing in de and fr?"

Expected: Shows de is missing 10 keys, fr is missing all 14 keys.

### 3. Preview sync (dry run)
> "Show me what would be translated to German and French"

Expected: Shows delta preview with credit cost estimate.

### 4. Execute sync
> "Sync the translations to German and French"

Expected: Translates missing keys and updates the JSON files.

## Framework Detection

This project is detected as `next-intl` because of:
- `messages/*.json` directory pattern
- `next.config.js` with next-intl plugin
- `i18n.ts` configuration file

## Translation Content

**Source (en.json):** 14 keys across 4 namespaces
- `app.*` - Application branding (2 keys)
- `auth.*` - Authentication UI (4 keys)
- `common.*` - Common actions (4 keys)
- `errors.*` - Error messages (4 keys)

**German (de.json):** 4 keys translated
- Missing: `app.tagline`, `auth.signup`, `auth.forgot_password`, all `common.*`, all `errors.*`

**French (fr.json):** Empty - all 14 keys missing
