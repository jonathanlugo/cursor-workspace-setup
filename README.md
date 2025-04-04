# Cursor AI Workspace Setup

Personal workspace configuration for Cursor AI, including MCP setup, project templates, and development tools.

## Documentation

- [MCP Management](docs/MCP_MANAGEMENT.md) - Guide for adding and managing MCPs
- [Best Practices](docs/BEST%20PRACTICES.md) - Development and coding standards
- [Requirements Engineering](docs/Requirements%20Engineering.md) - Project specifications template

## Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/jonathanlugo/cursor-workspace-setup.git ~/.cursor-docs
   ```

2. Add the following to your `~/.bashrc`:
   ```bash
   # Add Cursor docs scripts to PATH
   export PATH="$HOME/.cursor-docs/bin:$PATH"
   
   # Cursor tool aliases
   alias cinit="cursor-init"
   alias clink="cursor-link-docs"
   alias chelp="cursor-help"
   alias cmcp="cursor-mcp"
   ```

3. Reload your shell configuration:
   ```bash
   source ~/.bashrc
   ```

4. Set up MCP configuration:
   ```bash
   cmcp setup
   ```

## Available Commands

- `cinit <project-name> [--type python|nextjs]` - Initialize a new project
- `clink` - Link documentation to current project
- `cmcp [setup|status]` - Manage MCP configuration
- `chelp` - Show help and documentation

## Directory Structure

```
~/.cursor-docs/
├── bin/                    # Executable scripts
│   ├── cursor-init        # Project initialization
│   ├── cursor-link-docs   # Documentation linking
│   ├── cursor-help        # Help system
│   └── cursor-mcp         # MCP configuration
├── templates/              # Project templates
│   ├── mcp.template.json  # MCP configuration template
│   └── docs/             # Documentation templates
└── docs/                  # Central documentation
    ├── BEST PRACTICES.md
    ├── MCP_MANAGEMENT.md
    └── Requirements Engineering.md
```

## Project Types

### Python Projects Include:
- FastAPI setup
- Docker configuration
- Testing setup with pytest
- Basic project structure
- Environment variable handling
- Development tools configuration

### Next.js Projects Include:
- TypeScript & Tailwind CSS
- Bun package manager
- Component structure
- ESLint configuration
- Environment setup
- Modern development practices

## Contributing

While this is a personal workspace setup, you can:
1. Fork the repository
2. Make your changes
3. Submit a pull request
4. Describe your changes in detail

## License

MIT