# Cursor AI Workspace Setup

Personal workspace configuration for Cursor AI, including MCP setup, project templates, and development tools.

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

## Maintenance and Updates

### Local Changes
When you make changes to your setup:
1. Edit files in `~/.cursor-docs/`
2. Test your changes locally
3. Commit and push to GitHub:
   ```bash
   cd ~/.cursor-docs
   git add .
   git commit -m "Description of your changes"
   git push origin main
   ```

### Syncing Multiple Machines
If you use multiple computers:
1. Push changes from machine A
2. On machine B, pull the latest changes:
   ```bash
   cd ~/.cursor-docs
   git pull origin main
   source ~/.bashrc  # Apply any new aliases or PATH changes
   ```

### System Recovery
If you need to set up a new machine:
1. Clone the repository
2. Set up aliases in `.bashrc`
3. Configure environment variables:
   ```bash
   export MCP_SUPABASE_URL="your_url"
   export MCP_FIGMA_API_KEY="your_key"
   export GITHUB_PERSONAL_ACCESS_TOKEN="your_token"
   ```
4. Run `cmcp setup` to verify configuration

## Security

### Repository Access
- This repository is public (readable by anyone)
- Only the owner (you) can write to it
- Others can:
  - View and clone the repository
  - Fork it to their own account
  - Submit pull requests for your review
- No sensitive data is stored in the repository
  - MCP configuration uses environment variables
  - Credentials are stored locally in `~/.bashrc`

### Best Practices
- Never commit sensitive data or credentials
- Use environment variables for all secrets
- Keep your GitHub token secure
- Regularly update your access tokens
- Review public repository content

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

## Documentation

- [Best Practices](docs/BEST%20PRACTICES.md)
- [Requirements Engineering](docs/Requirements%20Engineering.md)

## Contributing

While this is a personal workspace setup, you can:
1. Fork the repository
2. Make your changes
3. Submit a pull request
4. Describe your changes in detail

## License

MIT