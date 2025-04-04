# Cursor AI Best Practices

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

## Teaching Approach
- Cursor AI will explain all actions and reasoning
- Explanations should be clear and educational
- The AI acts as a tutor, helping the human learn and understand
- Complex concepts should be broken down into digestible parts

## Environment Variables and Security
- Sensitive credentials should be stored as environment variables
- Credentials should never be hardcoded in configuration files
- Environment variables should be stored in ~/.bashrc for persistence
- Configuration files should reference environment variables using $VARIABLE_NAME syntax

## Project Setup Commands
### Quick Reference
- `cinit <project-name> [--type python|nextjs]` - Initialize a new project with documentation and structure
- `clink` - Create symbolic links to central documentation in current directory
- `chelp` - Show available commands and documentation

### Project Initialization Details
The `cinit` command creates a new project with:
- Git initialization
- Documentation links (BEST PRACTICES.md and Requirements Engineering.md)
- Project-specific structure based on type:
  - Python: src/, tests/, docs/, Dockerfile, requirements.txt
  - Next.js: pages/, components/, styles/, public/, tailwind config
- README.md template
- Environment setup (.env.example, .gitignore)

### Documentation Link Details
The `clink` command:
- Creates symbolic links to central documentation files
- Updates existing links if needed
- Can be run in any project directory
- Ensures documentation stays in sync with central versions

### Central Documentation Location
All central documentation is stored in `~/.cursor-docs/`:
- BEST PRACTICES.md - Development and coding standards
- Requirements Engineering.md - Project specifications and requirements
- Project initialization scripts and utilities
