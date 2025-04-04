# MCP Management Guide

## Adding New MCPs

When adding a new MCP service to your Cursor AI setup, follow these steps:

1. **Update MCP Template**
   - Edit `~/.cursor-docs/templates/mcp.template.json`
   - Add your new MCP configuration:
   ```json
   {
     "mcpServers": {
       "existing-mcp": { ... },
       "your-new-mcp": {
         "command": "command-to-run",
         "args": [
           "-y",
           "package-or-service",
           "--api-key=$YOUR_NEW_MCP_KEY"
         ]
       }
     }
   }
   ```

2. **Add Environment Variables**
   - Add to `~/.bashrc`:
   ```bash
   export YOUR_NEW_MCP_KEY="your_key_here"
   ```
   - Run `source ~/.bashrc` to load the new variable

3. **Verify Configuration**
   ```bash
   cmcp status    # Check if new variable is recognized
   cmcp setup     # Update MCP configuration
   ```

4. **Save Changes**
   ```bash
   cd ~/.cursor-docs
   git add templates/mcp.template.json
   git commit -m "Added new MCP for [service name]"
   git push origin main
   ```

## MCP Configuration Structure

Each MCP entry in `mcp.template.json` follows this pattern:
```json
{
  "mcpServers": {
    "mcp-name": {
      "command": "base-command",
      "args": [
        "arg1",
        "arg2",
        "--flag=$ENV_VARIABLE"
      ],
      "env": {                    // Optional environment section
        "ENV_NAME": "$ENV_VALUE"
      }
    }
  }
}
```

## Example: Adding a New Service

Adding an Azure AI MCP:
```json
{
  "mcpServers": {
    "azure-ai": {
      "command": "npx",
      "args": [
        "-y",
        "@azure/ai-service",
        "--api-key=$AZURE_AI_KEY",
        "--region=$AZURE_REGION"
      ],
      "env": {
        "AZURE_AI_KEY": "$AZURE_AI_KEY",
        "AZURE_REGION": "$AZURE_REGION"
      }
    }
  }
}
```

Required environment variables:
```bash
export AZURE_AI_KEY="your-azure-key"
export AZURE_REGION="your-region"
```

## Current MCP Services

1. **Supabase**
   - Environment: `MCP_SUPABASE_URL`
   - Purpose: Database connections

2. **Figma**
   - Environment: `MCP_FIGMA_API_KEY`
   - Purpose: Design integration

3. **GitHub**
   - Environment: `GITHUB_PERSONAL_ACCESS_TOKEN`
   - Purpose: Repository management

## Best Practices for MCPs

1. **Security**
   - Never commit API keys or tokens
   - Always use environment variables
   - Keep tokens with minimal permissions

2. **Maintenance**
   - Regularly update API keys
   - Remove unused MCPs
   - Document purpose of each MCP

3. **Testing**
   - Test new MCPs before committing
   - Verify environment variables
   - Check for conflicts with existing MCPs

## Troubleshooting MCPs

If an MCP isn't working:
1. Check `cmcp status` for environment variables
2. Verify `~/.cursor/mcp.json` configuration
3. Ensure variables are loaded (`source ~/.bashrc`)
4. Check service-specific requirements

## Using Cursor AI with MCPs

When asking Cursor AI to add a new MCP:
1. Provide the service name and purpose
2. Specify any special requirements
3. Request documentation updates
4. Ask for verification steps

Example prompt:
"Please add [Service Name] MCP to my configuration. It requires [specific details]. Update the documentation and show me how to verify it's working."

## Backing Up MCP Changes

After adding new MCPs:
1. Verify the configuration works
2. Commit changes to the repository
3. Update documentation if needed
4. Push changes to GitHub