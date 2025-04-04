# Supported MCP Services

This document lists all the Model Context Protocol (MCP) services supported in our setup.

## Available Services

### Supabase
- **Environment Variable**: `MCP_SUPABASE_URL`
- **Purpose**: Database operations and queries
- **Usage**: Enables database interactions and SQL queries through Cursor AI

### Figma
- **Environment Variable**: `MCP_FIGMA_API_KEY`
- **Purpose**: Figma design file access and asset management
- **Usage**: Allows fetching design assets and file information from Figma

### GitHub
- **Environment Variable**: `GITHUB_PERSONAL_ACCESS_TOKEN`
- **Purpose**: GitHub repository management and operations
- **Usage**: Enables repository operations, file management, and issue tracking

### Digital Ocean
- **Environment Variable**: `DIGITALOCEAN_API_KEY`
- **Purpose**: Cloud infrastructure management and deployment
- **Usage**: Manages Digital Ocean resources like droplets, spaces, and kubernetes clusters

## Setting Up Digital Ocean MCP

1. **Install the MCP Server**:
   ```bash
   npm install -g mcp-digitalocean-server
   ```

2. **Configure Environment**:
   Add to your `~/.bashrc`:
   ```bash
   export DIGITALOCEAN_API_KEY="your_api_key_here"
   ```

3. **Update MCP Configuration**:
   The following configuration is already added to your MCP setup:
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

4. **Verify Setup**:
   ```bash
   cmcp status
   cmcp setup
   ```

## Using Digital Ocean MCP

You can now use Cursor AI to manage your Digital Ocean resources. Example prompts:

- "Create a new droplet with Ubuntu 20.04"
- "List all active droplets"
- "Create a new Space for storage"
- "Configure a load balancer"
- "Set up a Kubernetes cluster"

## Security Notes

- The API key is stored locally in `~/.bashrc`
- Only the variable reference is stored in the MCP configuration
- No sensitive data is committed to the repository