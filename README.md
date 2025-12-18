
# Claude Skills

A collection of specialized Claude skills for command-line productivity tools and workflows. These skills provide comprehensive reference guides for CLI tools like Google Calendar, Google Drive, Jira, and GitHub PR review workflows.

## What are Claude Skills?

Claude skills are detailed reference guides that help Claude Code understand and assist with specific tools and workflows. Each skill contains complete setup instructions, authentication details, common commands, and best practices.

## Available Skills

- **[gcalcli](skills/gcalcli/SKILL.md)** - Google Calendar CLI with meeting notes and attachment access
  - Based on: [insanum/gcalcli](https://github.com/insanum/gcalcli)
  - Custom fork: [shanemcd/gcalcli](https://github.com/shanemcd/gcalcli)
- **[gcmd](skills/gcmd/SKILL.md)** - Google Drive file management and markdown export
  - Repository: [shanemcd/gcmd](https://github.com/shanemcd/gcmd)
- **[jirahhh](skills/jirahhh/SKILL.md)** - Jira issue creation, updates, and management
  - Repository: [shanemcd/jirahhh](https://github.com/shanemcd/jirahhh)
- **[pr-review](skills/pr-review-skill/SKILL.md)** - GitHub PR review workflow with automated analysis
  - Uses: [GitHub CLI](https://cli.github.com/)

## Installation and Setup

### 1. Clone This Repository

```bash
git clone https://github.com/your-username/claude-skills.git
cd claude-skills
```

### 2. Install Claude Code CLI

Follow the official installation guide at [docs.anthropic.com/claude-code](https://docs.anthropic.com/en/docs/claude-code/quickstart).

### 3. Configure Skills for Claude Code

To make these skills available to Claude Code, you have several options:

#### Option A: Global Skills Directory (Recommended)

Copy or symlink the skills to your global Claude Code skills directory:

```bash
# Create the global skills directory
mkdir -p ~/.claude/skills

# Copy skills (or create symlinks)
cp -r /path/to/claude-skills/skills/* ~/.claude/skills/
# OR create symlinks:
# ln -s /path/to/claude-skills/skills/* ~/.claude/skills/
```

Claude Code will automatically discover and load these skills from `~/.claude/skills/`.

#### Option B: Project-Specific Skills

For project-specific access, create a `.claude/skills` directory in your project:

```bash
# In your project directory
mkdir -p .claude/skills
cp -r /path/to/claude-skills/skills/* .claude/skills/
# OR create symlinks:
# ln -s /path/to/claude-skills/skills/* .claude/skills/
```

#### Option C: Add to CLAUDE.md

If you have an existing project with a `CLAUDE.md` file, add a reference to these skills:

```markdown
# Skills Available

Claude has access to specialized skills from: `/path/to/claude-skills`

Available skills:
- gcalcli: Google Calendar management
- gcmd: Google Drive file operations  
- jirahhh: Jira issue management
- pr-review: GitHub PR review workflow

See individual SKILL.md files for complete documentation.
```

#### Option D: Use Skills Directly

Navigate to this repository and start Claude Code from here:

```bash
cd /path/to/claude-skills
claude
```

Claude Code will automatically read the `CLAUDE.md` file in this repository and understand the available skills.

### 4. Tool-Specific Setup

Each skill has specific setup requirements. Follow the setup sections in each SKILL.md file:

#### gcalcli Setup
- Install: `uvx --from "git+https://github.com/shanemcd/gcalcli@attachments-in-tsv-and-json" --with "google-api-core<2.28.0" gcalcli`
- Authenticate with Google Calendar on first use

#### gcmd Setup  
- Clone repository: `git clone https://github.com/shanemcd/gcmd.git`
- Configure OAuth credentials (see gcmd documentation)

#### jirahhh Setup
- Generate Jira API tokens for your environments
- Create config file at `~/.config/jirahhh/config.yaml`

#### PR Review Setup
- Requires `gh` CLI tool and Python with `uv`
- Scripts handle dependencies automatically

## Using Skills with Claude Code

Once configured, you can ask Claude Code to help with any of these tools:

### Example Interactions

```bash
# Start Claude Code
claude

# Example requests:
"Check my calendar for today and show any meetings with Gemini notes"
"Export that Google Doc to markdown so I can review it"  
"Create a Jira epic for the new feature with acceptance criteria"
"Review GitHub PR #123 and provide detailed feedback"
```

### Skill Discovery

Claude Code will automatically:
- Read the CLAUDE.md file to understand available skills
- Reference the appropriate SKILL.md files when you ask about specific tools
- Follow the documented workflows and best practices
- Use the correct authentication and configuration for each tool

## Skill Documentation Format

Each skill follows a consistent structure:

- **Overview**: Tool description and use cases
- **Setup**: Installation and authentication  
- **Commands**: Common operations with examples
- **Workflows**: Step-by-step processes
- **Tips**: Best practices and troubleshooting

## Contributing

To add a new skill:

1. Create a new directory: `skills/tool-name/`
2. Add a `SKILL.md` file with frontmatter:
   ```yaml
   ---
   name: tool-name
   description: Brief description
   ---
   ```
3. Follow the existing documentation patterns
4. Update this README and the main CLAUDE.md file

## Repository Structure

```
claude-skills/
├── README.md                    # This file
├── CLAUDE.md                   # Claude Code guidance  
└── skills/                     # Individual skill guides
    ├── gcalcli/SKILL.md       # Google Calendar
    ├── gcmd/SKILL.md          # Google Drive
    ├── jirahhh/SKILL.md       # Jira
    └── pr-review-skill/       # GitHub PR reviews
        ├── SKILL.md
        └── scripts/           # Python utilities
```

## Tool Repositories

These skills are based on the following open-source tools:

- **gcalcli**: Google Calendar command line interface
  - Original: [insanum/gcalcli](https://github.com/insanum/gcalcli)
  - Custom fork with attachment support: [shanemcd/gcalcli](https://github.com/shanemcd/gcalcli)
- **gcmd**: Google Drive command line tool
  - Repository: [shanemcd/gcmd](https://github.com/shanemcd/gcmd)
- **jirahhh**: Jira command line interface
  - Repository: [shanemcd/jirahhh](https://github.com/shanemcd/jirahhh)
- **GitHub CLI**: Official GitHub command line tool
  - Repository: [cli/cli](https://github.com/cli/cli)
  - Website: [cli.github.com](https://cli.github.com/)

## License

MIT License - See individual tool repositories for their specific licenses.
