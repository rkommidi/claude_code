# Claude Code Configuration

Custom agents, commands, skills, and hooks for Claude Code CLI.

## Installation

Copy the `.claude` directory to your home directory or project root:

```bash
# Global installation (available in all projects)
cp -r .claude ~/.claude

# Or project-specific installation
cp -r .claude /path/to/your/project/.claude
```

## Contents

### Agents

Custom AI agents for specialized tasks:

| Agent | Description | Usage |
|-------|-------------|-------|
| `code-reviewer` | Reviews code for quality, security, and performance | Automatically used when reviewing PRs or code |
| `debugger` | Investigates errors, test failures, and bugs | Automatically used when debugging issues |

### Commands

Slash commands for common workflows:

| Command | Description | Usage |
|---------|-------------|-------|
| `/explain` | Explain a file or function in detail | `/explain src/utils.ts` |
| `/pr` | Create a PR with auto-generated description | `/pr` |
| `/quick-commit` | Stage all changes and commit with generated message | `/quick-commit` |
| `/test-this` | Generate unit tests for a file | `/test-this src/utils.ts` |

### Skills

Domain-specific capabilities:

| Skill | Description | When It's Used |
|-------|-------------|----------------|
| `api-designer` | REST API design with best practices | When designing API endpoints |
| `pdf` | PDF manipulation (extract, merge, split, forms) | When working with PDF files |
| `pptx` | PowerPoint creation and editing | When creating/editing presentations |
| `xlsx` | Excel spreadsheet operations | When working with spreadsheets |
| `webapp-testing` | Playwright-based web app testing | When testing web applications |

### Hooks

Automated actions that run after tool use:

- **Prettier formatting**: Automatically formats JS, TS, JSON, CSS, HTML, MD, and YAML files after edits

## Usage Examples

### Code Review
```
Review the changes in this PR
```
Claude will use the `code-reviewer` agent to analyze code quality, security, and best practices.

### Debugging
```
Why is this test failing?
```
Claude will use the `debugger` agent to investigate and fix the issue.

### Quick Commit
```
/quick-commit
```
Stages all changes and creates a commit with an appropriate message.

### Create PR
```
/pr
```
Pushes the branch and creates a PR with auto-generated title and description.

### Generate Tests
```
/test-this src/components/Button.tsx
```
Generates comprehensive unit tests for the specified file.

### Explain Code
```
/explain src/utils/parser.ts
```
Provides detailed explanation of what the code does and how it works.

## Customization

### Adding New Commands

Create a new `.md` file in `.claude/commands/`:

```markdown
---
description: Your command description
argument-hint: [optional-args]
---

Your command instructions here.
Use $ARGUMENTS to reference user-provided arguments.
```

### Adding New Skills

Create a new directory in `.claude/skills/` with a `SKILL.md` file:

```markdown
---
name: skill-name
description: When this skill should be used
---

Instructions for the skill...
```

### Modifying Hooks

Edit `.claude/settings.json` to add or modify hooks:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "your-command-here",
            "timeout": 30
          }
        ]
      }
    ]
  }
}
```

## Requirements

Some skills require additional dependencies:

- **pdf**: `pypdf`, `pdfplumber`, `reportlab`
- **xlsx**: `pandas`, `openpyxl`, LibreOffice (for formula recalculation)
- **pptx**: `pptxgenjs`, `playwright`, `sharp`, LibreOffice
- **webapp-testing**: `playwright`

## License

MIT
