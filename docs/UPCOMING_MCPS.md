# Upcoming MCP Integrations

This document tracks planned MCP integrations that will be added once they become available.

## Digital Ocean MCP

**Status**: Awaiting official MCP release
**Purpose**: Cloud infrastructure management and deployment
**Expected Features**:
- Droplet management
- Spaces (S3-compatible storage)
- Kubernetes clusters
- Load balancers
- Database management

In the meantime, we are using direct API access or alternative solutions for specific needs:
- For PostgreSQL databases: Using the Supabase MCP with custom connection strings
- For object storage: Using direct S3-compatible API access
- For compute resources: Using direct API access

We will update this document and implement the Digital Ocean MCP integration once it becomes available on the official MCP registry.