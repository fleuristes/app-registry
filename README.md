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
      "array of arguments needed to run your MCP"
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
      "label": "Configuration Label",
      "type": "input",
      "placeholder": "Placeholder text for the input field",
      "value": "Default value or instructions",
      "key": "ENVIRONMENT_VARIABLE_KEY"
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