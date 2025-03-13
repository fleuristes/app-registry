# Fleur App Registry

This repository serves as the official app registry for [Fleur](https://github.com/fleuristes/fleur), an open-source [Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) GUI client. It contains a curated list of MCP applications that can be integrated with Fleur to extend its capabilities.

## What is MCP?

Model Context Protocol (MCP) is a standardized way for language models to interact with external tools and data sources. MCPs enable models to:

- Access real-time information
- Interact with web services
- Manipulate files and data
- Connect to various APIs and platforms

## Available Apps

The registry currently includes apps for:

- Web browsing
- Time services
- Hacker News integration
- Linear project management
- Slack communication
- Obsidian note-taking
- Rember flashcards


## Contributing Your MCP

We welcome contributions from developers who want to add their MCP applications to the registry. To submit your MCP, please create a pull request following the guidelines below.

### MCP Schema

Each MCP in the registry must conform to the following JSON schema:

```json
{
  "name": "Your App Name",
  "description": "A concise description of what your app does and how it helps users",
  "icon": {
    "type": "url",
    "url": {
      "light": "URL to light mode icon (SVG or PNG recommended)",
      "dark": "URL to dark mode icon (SVG or PNG recommended)"
    }
  },
  "category": "Category of your app (e.g., Productivity, Communication, Utilities)",
  "price": "Free or pricing information",
  "developer": "Your name or organization",
  "sourceUrl": "URL to the source code repository",
  "config": {
    "mcpKey": "unique identifier for your MCP",
    "runtime": "runtime environment (e.g., npx, uvx)",
    "args": [
      "array of arguments needed to run your MCP",
      "--api-key=${API_KEY}",
      "--base-url=${BASE_URL}"
    ]
  },
  "features": [
    {
      "name": "Feature name",
      "description": "Brief description of the feature",
      "prompt": "Example prompt that users can use to trigger this feature"
    }
  ],
  "setup": [
    {
      "label": "API Key",
      "type": "input",
      "placeholder": "Enter your API key",
      "value": "",
      "key": "API_KEY"
    },
    {
      "label": "Base URL",
      "type": "input",
      "placeholder": "https://api.example.com",
      "value": "https://api.example.com",
      "key": "BASE_URL"
    }
  ]
}
```

### Schema Field Descriptions

| Field | Description | Required |
|-------|-------------|----------|
| `name` | The display name of your app | Yes |
| `description` | A brief description of what your app does | Yes |
| `icon` | Icon configuration with light and dark mode variants | Yes |
| `category` | The category your app belongs to | Yes |
| `price` | Pricing information (Free, Paid, etc.) | Yes |
| `developer` | Name of the developer or organization | Yes |
| `sourceUrl` | URL to the source code repository | Yes |
| `config` | Configuration details for running the MCP | Yes |
| `config.mcpKey` | Unique identifier for your MCP | Yes |
| `config.runtime` | Runtime environment (npx, uvx, etc.) | Yes |
| `config.args` | Arguments needed to run your MCP | Yes |
| `features` | Array of features your app provides | Yes |
| `features[].name` | Name of the feature | Yes |
| `features[].description` | Description of what the feature does | Yes |
| `features[].prompt` | Example prompt for users | Yes |
| `setup` | Array of setup instructions for configuration | No |
| `setup[].label` | Label for the configuration item | If setup is included |
| `setup[].type` | Type of input (input, select, etc.) | If setup is included |
| `setup[].placeholder` | Placeholder text | If setup is included |
| `setup[].value` | Default value or instructions | If setup is included |
| `setup[].key` | Environment variable key | If setup is included |

### Environment Variable Support

Fleur now supports using environment variables in your MCP configuration. This allows you to create more flexible and configurable MCPs without hardcoding sensitive information or user-specific settings.

#### Using Environment Variables in Args

You can include environment variables in your `args` array using the `${VARIABLE_NAME}` syntax. For example:

```json
"args": [
  "start",
  "--api-key=${API_KEY}",
  "--base-url=${BASE_URL}",
  "--port=${PORT}"
]
```

When the MCP is installed, Fleur will automatically replace these variables with their corresponding values from the user's configuration.

#### Environment Variable Features

- **Simple variables**: `--api-key=${API_KEY}`
- **Multiple variables in one argument**: `--connection=${HOST}:${PORT}`
- **Variables with surrounding text**: `--path=prefix_${PATH_VAR}_suffix`
- **Support for different value types**: Numbers, booleans, and strings are all supported
- **Path-like variables**: `--config=${CONFIG_DIR}/settings.json`

#### Setting Up Environment Variables

To make your MCP configurable, define the required environment variables in the `setup` array. Each entry should include:

1. A user-friendly label
2. The type of input
3. A placeholder or default value
4. The environment variable key that matches the one used in your `args`

This creates a seamless configuration experience for users while keeping sensitive information secure.

### Submission Guidelines

1. Fork this repository
2. Add your MCP to the `apps.json` file
3. If needed, add your app icon to the `assets` directory
4. Submit a pull request with a clear description of your MCP

### Icon Guidelines

- Icons should be in SVG format when possible (PNG is acceptable if SVG is not available)
- Include both light and dark mode variants if your icon has different appearances for different themes
- Place your icon in the `assets` directory and reference it in your MCP configuration

## License

This repository is licensed under the Apache License 2.0 - see the LICENSE file for details.

## Support

For questions or issues related to the Fleur App Registry, please open an issue in this repository.