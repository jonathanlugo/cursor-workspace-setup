# Database Setup Guide

## Digital Ocean Managed PostgreSQL

### Current Configuration
- **Plan**: Basic Tier (€15/month)
- **Specs**:
  - 1 vCPU (shared)
  - 1 GB RAM
  - 10 GB Storage
  - Daily backups
  - Point-in-time recovery

### Features
- MongoDB-compatible JSON/BSON storage
- SQL capabilities
- Automated maintenance
- Encryption at rest and in transit
- Connection pooling
- Monitoring dashboard

### Connection Setup
1. **Environment Variable**:
   ```bash
   # Add to ~/.bashrc
   export MCP_DO_DATABASE_URL="postgresql://doadmin:password@host:port/defaultdb?sslmode=require"
   ```

2. **MCP Configuration**:
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

### Security Best Practices
1. **Firewall Rules**:
   - Add only necessary IP addresses
   - Use SSL mode for all connections
   - Regular audit of allowed IPs

2. **Access Management**:
   - Use connection pooling
   - Create separate users per application
   - Regular password rotation

### MongoDB Migration
When migrating from MongoDB:
1. Use JSONB data type for document storage
2. Create appropriate indexes on JSON fields
3. Use PostgreSQL's JSON operators for queries

### Scaling Guidelines
- Monitor connection count
- Watch for storage usage
- Set up alerts at 80% resource utilization
- Plan for vertical scaling when needed

### Backup Strategy
- Daily automated backups (included)
- Point-in-time recovery up to 7 days
- Regular backup verification
- Document recovery procedures

### Monitoring
- Set up alerts for:
  - CPU usage > 80%
  - Storage usage > 80%
  - Unusual connection patterns
  - Failed connection attempts

### Development Guidelines
1. **Local Development**:
   - Use connection pooling
   - Set appropriate timeouts
   - Handle connection errors gracefully

2. **Production**:
   - Use environment variables
   - Implement retry logic
   - Monitor query performance

3. **JSON Document Storage**:
   ```sql
   CREATE TABLE documents (
     id SERIAL PRIMARY KEY,
     collection VARCHAR(255) NOT NULL,
     data JSONB NOT NULL,
     created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP,
     updated_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
   );
   ```