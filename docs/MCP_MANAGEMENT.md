# MCP Management Guide

## Current MCP Services

The following MCP services are currently configured:

### Supabase
- Environment Variable: `MCP_SUPABASE_URL`
- Purpose: Database operations and queries

### Figma
- Environment Variable: `MCP_FIGMA_API_KEY`
- Purpose: Figma design file access and asset management

### GitHub
- Environment Variable: `GITHUB_PERSONAL_ACCESS_TOKEN`
- Purpose: GitHub repository management and operations

### Digital Ocean
- Environment Variable: `DIGITALOCEAN_API_KEY`
- Purpose: Cloud infrastructure management and deployment

## Adding New MCPs

1. Update the MCP template at `~/.cursor-docs/templates/mcp.template.json`:
```json
{
    "mcpServers": {
        "service_name": {
            "command": "command_to_run",
            "args": [
                "required_args",
                "--api-key=$ENV_VAR"
            ],
            "env": {
                "ENV_VAR": "$ENV_VAR"
            }
        }
    }
}
```

2. Add environment variables to `~/.bashrc`:
```bash
export SERVICE_API_KEY="your_api_key_here"
```

3. Source your bashrc:
```bash
source ~/.bashrc
```

4. Verify configuration:
```bash
cmcp status
cmcp setup
```

## Example: Adding Digital Ocean MCP

1. Add to mcp.template.json:
```json
"digitalocean": {
    "command": "npx",
    "args": [
        "-y",
        "mcp-digitalocean-server",
        "--api-key=$DIGITALOCEAN_API_KEY",
        "--stdio"
    ],
    "env": {
        "DIGITALOCEAN_API_KEY": "$DIGITALOCEAN_API_KEY"
    }
}
```

2. Add to ~/.bashrc:
```bash
export DIGITALOCEAN_API_KEY="your_api_key_here"
```

## Best Practices

1. **Security**
   - Never commit actual API keys
   - Use environment variables for sensitive data
   - Keep your `~/.bashrc` file secure

2. **Maintenance**
   - Regularly update MCP servers
   - Test new configurations before committing
   - Keep documentation updated

3. **Troubleshooting**
   - Check environment variables are set
   - Verify MCP configuration
   - Test service connectivity

## Using Cursor AI with MCPs

To request Cursor AI to use an MCP, simply mention the service in your prompt:
"Please use the Digital Ocean MCP to create a new droplet"

## Backing Up MCP Changes

1. Verify your configuration works
2. Commit changes to the repository
3. Update documentation if needed
4. Push to GitHub