# Infrastructure Setup

## Database: Digital Ocean Managed PostgreSQL

### Configuration
- **Plan**: Basic Tier (€15/month)
- **Specs**: 1 vCPU, 1 GB RAM, 10 GB Storage
- **Region**: Frankfurt (fra1)
- **Version**: PostgreSQL 15
- **Connection**: SSL-enabled

### Environment Setup
1. Add to `~/.bashrc`:
   ```bash
   export MCP_DO_DATABASE_URL="postgresql://user:pass@host:port/defaultdb?sslmode=require"
   ```

2. Reload environment:
   ```bash
   source ~/.bashrc
   ```

### Access Control
- Firewall rules configured for specific IPs
- SSL required for all connections
- Connection pooling enabled

### MCP Integration
The database is accessible through the Supabase MCP server configuration:
```json
"do_postgres": {
    "command": "npx",
    "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "$MCP_DO_DATABASE_URL"
    ]
}
```

### Management Commands
```bash
# Check database status
doctl databases get 9d479eb3-81f5-4010-a3b0-bb124fc90c8d

# List firewall rules
doctl databases firewalls list 9d479eb3-81f5-4010-a3b0-bb124fc90c8d

# Add IP to firewall
doctl databases firewalls append 9d479eb3-81f5-4010-a3b0-bb124fc90c8d --rule "ip_addr:YOUR_IP"
```

### Included Features
- Daily backups
- Point-in-time recovery
- Automated maintenance
- Monitoring dashboard
- SSL encryption
- Connection pooling

### Scaling Path
- Current: Shared CPU (€15/month)
- Next tier: Dedicated resources when needed
- Can scale vertically or add read replicas

### Monitoring
- CPU usage
- Memory usage
- Disk space
- Connection count
- Query performance

### Backup Strategy
- Automated daily backups (included)
- 7-day point-in-time recovery
- Manual backup before major changes