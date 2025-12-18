# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of Claude skills - specialized reference guides for command-line tools and workflows. Each skill contains comprehensive documentation for specific tools like gcalcli (Google Calendar), gcmd (Google Drive), jirahhh (Jira), and pr-review (GitHub PR reviews).

## Repository Structure

```
claude-skills/
├── README.md                         # Basic repo description
└── skills/                          # Individual skill directories
    ├── gcalcli/SKILL.md            # Google Calendar CLI reference
    ├── gcmd/SKILL.md               # Google Drive CLI reference  
    ├── jirahhh/SKILL.md            # Jira CLI reference
    └── pr-review-skill/            # GitHub PR review workflow
        ├── SKILL.md                # PR review process guide
        ├── README.md               # Additional documentation
        └── scripts/                # Python utilities for PR review
            ├── summarize-pr.py     # GraphQL-based PR summary tool
            └── prepare-worktree.py # Git worktree setup for PR review
```

## Key Components

### Skill Documentation Format
All skills follow a consistent frontmatter format:
```yaml
---
name: skill-name
description: Brief description
---
```

### Skills Available

1. **gcalcli** - Google Calendar CLI integration
   - Uses custom fork with attachment support for meeting notes
   - JSON/TSV output formats for programmatic access
   - Commands for agenda viewing, searching, and accessing Gemini notes

2. **gcmd** - Google Drive file management
   - Export Google Docs to markdown
   - Search and list Drive files
   - View file permissions and comments
   - Located at `/Users/ben/git/gcmd`

3. **jirahhh** - Jira issue management
   - Create, update, view, and search Jira issues
   - Markdown to Jira wiki markup conversion
   - Support for custom fields (acceptance criteria, epic links)
   - Environment switching between stage and prod

4. **pr-review** - GitHub PR review workflow
   - Comprehensive PR analysis using GraphQL
   - Git worktree management for clean review environments
   - Structured review notes with progress tracking

### Python Scripts

The PR review skill includes two key Python utilities:

- `scripts/summarize-pr.py` - Comprehensive PR summary using GitHub GraphQL API
- `scripts/prepare-worktree.py` - Creates isolated git worktrees for PR review

Both scripts use `uv` for dependency management with inline dependency declarations.

## Common Development Tasks

### Working with Skills
- Skills are reference documents - no compilation or building required
- Each skill is self-contained with complete setup and usage instructions
- When referencing skills, use the file paths: `skills/{skill-name}/SKILL.md`

### Using PR Review Scripts
```bash
# Generate PR summary
scripts/summarize-pr.py OWNER REPO PR_NUMBER

# Create review worktree
WORKTREE_PATH=$(scripts/prepare-worktree.py /path/to/repo PR_NUMBER)
cd "$WORKTREE_PATH"
```

### External Tool Locations
- gcmd repository: `/Users/ben/git/gcmd`
- All other tools are accessed via `uvx` (no local installation needed)

## Architecture Notes

- **Documentation-centric**: Primary focus is comprehensive CLI tool documentation
- **Self-contained skills**: Each skill includes complete setup, authentication, and usage instructions
- **Tool integration**: Skills cover complex workflows like calendar + drive + jira integration
- **Environment awareness**: Many tools support multiple environments (stage/prod)
- **Automation-friendly**: Emphasis on programmatic access (JSON output, APIs, etc.)

The repository serves as a centralized knowledge base for command-line productivity workflows, with particular emphasis on Google Workspace, Jira, and GitHub integrations.