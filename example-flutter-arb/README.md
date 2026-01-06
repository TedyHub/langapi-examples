# LangAPI MCP Example: Flutter ARB

Minimal example demonstrating LangAPI MCP server with Flutter's ARB (Application Resource Bundle) localization format.

## Project Structure

```
example-flutter-arb/
├── lib/
│   └── l10n/
│       ├── app_en.arb    # Source locale (14 keys)
│       ├── app_de.arb    # Partial target (4 keys)
│       └── app_fr.arb    # Empty target
├── l10n.yaml
└── pubspec.yaml
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

Expected: Detects `flutter` framework with `lib/l10n/app_*.arb` pattern.

### 2. Check translation status
> "What translations are missing in German and French?"

Expected: Shows de missing 10 keys, fr missing all 14 keys.

### 3. Preview sync (dry run)
> "Show me what would be translated"

Expected: Shows delta preview with credit cost estimate.

### 4. Execute sync
> "Sync translations to German and French"

Expected: Translates missing keys and updates the ARB files.

## Framework Detection

This project is detected as `flutter` because of:
- `lib/l10n/app_*.arb` directory pattern
- `l10n.yaml` configuration file
- `flutter_localizations` dependency in pubspec.yaml

## Key Structure

Flutter ARB uses **flat keys** with camelCase naming:

```json
{
  "@@locale": "en",
  "appName": "My Application",
  "@appName": {
    "description": "The application name"
  },
  "authLogin": "Log in"
}
```

ARB files support metadata entries prefixed with `@` for descriptions and placeholders.
