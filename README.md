# Cursor AI Workspace Setup

Personal workspace configuration for Cursor AI, including MCP setup, project templates, and development tools.

## Prerequisites

Before you begin:
1. Install Cursor IDE from https://cursor.sh
2. Open Cursor IDE
3. Open the Command Palette (Cmd/Ctrl + Shift + P)
4. Type and run the command: `Run cinit`

This will initialize your Cursor AI workspace and display the complete setup documentation.

## Documentation

- [MCP Management](docs/MCP_MANAGEMENT.md) - Guide for adding and managing MCPs
- [Best Practices](docs/BEST%20PRACTICES.md) - Development and coding standards
- [Requirements Engineering](docs/Requirements%20Engineering.md) - Project specifications template

## Getting Help
Use these commands to get help at any time:
- `chelp` - Show quick reference of all available commands
- `chelp --docs` - Show this full documentation

## Authorization Requirements
- Cursor AI must ask for permission before updating any code
- Permission must be granted by the human using one of these exact phrases:
  - "authorized"
  - "Authorized"
  - "AUTHORIZED"
- No code changes will be made without this explicit authorization

## Quick Start

Note: Make sure you have git installed before proceeding with the setup.

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

- `cinit <project-name> [--type python|nextjs]` - Initialize a new project with documentation and structure
- `clink` - Create symbolic links to central documentation in current directory
- `cmcp [setup|status]` - Manage MCP configuration
- `chelp` - Show help and documentation

## Environment Variables and Security
- Sensitive credentials should be stored as environment variables
- Credentials should never be hardcoded in configuration files
- Environment variables should be stored in ~/.bashrc for persistence
- Configuration files should reference environment variables using $VARIABLE_NAME syntax

## Database Infrastructure

### Digital Ocean Managed PostgreSQL
Our database is managed through Digital Ocean's managed database service:
- Cluster Name: `as25-pg-cluster`
- Region: FRA1 (Frankfurt)
- Plan: Basic (db-s-1vcpu-1gb)
- PostgreSQL Version: 15

### Credential Management
#### Development Environment
- Development credentials should be stored in `.bashrc`:
  ```bash
  # Database credentials for development
  export PGPASSWORD="<your-database-password>"
  export MCP_DO_DATABASE_URL="postgresql://doadmin:<your-database-password>@as25-pg-cluster-do-user-18884019-0.l.db.ondigitalocean.com:25060/defaultdb?sslmode=require"
  ```
- Get these credentials from the Digital Ocean dashboard or team password manager

#### Production Security
- Production credentials managed via Digital Ocean dashboard
- Access control managed via DO firewall rules
- CI/CD credentials stored in GitHub Secrets
- Additional service credentials (e.g., Clerk) will follow similar pattern

### Security Measures
- SSL connections required (sslmode=require)
- IP-based firewall rules in Digital Ocean
- Regular security audits via DO dashboard
- Development access restricted to approved IPs

### Connection Details
- Host: Managed by Digital Ocean
- Port: 25060
- Database: defaultdb
- User: doadmin
- SSL Mode: require

### Backup & Recovery (Managed by DO)
- Automated daily backups
- 7-day backup retention
- Point-in-time recovery available
- Backup monitoring via DO dashboard

### Monitoring & Maintenance
- Resource usage tracked in DO dashboard
- Performance metrics available in real-time
- Automated updates handled by DO
- Scaling available through DO dashboard

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

## MCP Configuration Status
When properly configured, your MCP status should show:
✅ MCP configuration file exists
✅ MCP_SUPABASE_URL is configured
✅ MCP_FIGMA_API_KEY is configured
✅ GITHUB_PERSONAL_ACCESS_TOKEN is configured

## Contributing

While this is a personal workspace setup, you can:
1. Fork the repository
2. Make your changes
3. Submit a pull request
4. Describe your changes in detail

## License

MIT 
