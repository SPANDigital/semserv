# sem-serv-docs
Semantic Service Naming Documentation

This repository contains the documentation for semantic service naming conventions and guidelines.

## Prerequisites

This documentation site is built with [Hugo](https://gohugo.io/), a fast and modern static site generator.

## Installing Hugo

### macOS

#### Using Homebrew (Recommended)
```bash
brew install hugo
```

#### Using MacPorts
```bash
sudo port install hugo
```

### Linux

#### Ubuntu/Debian
```bash
sudo apt install hugo
```

#### Fedora/CentOS/RHEL
```bash
sudo dnf install hugo
```

#### Arch Linux
```bash
sudo pacman -S hugo
```

#### Alpine Linux
```bash
doas apk add --no-cache --repository=https://dl-cdn.alpinelinux.org/alpine/edge/community hugo
```

#### Using Snap (Universal)
```bash
sudo snap install hugo
```

### Windows

#### Using Chocolatey
```bash
choco install hugo-extended
```

#### Using Winget
```bash
winget install Hugo.Hugo.Extended
```

#### Using Scoop
```bash
scoop install hugo-extended
```

### From Source (All Platforms)

If you have Go installed, you can build Hugo from source:

```bash
CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
```

## Verify Installation

After installation, verify that Hugo is installed correctly:

```bash
hugo version
```

This should display the Hugo version information.

## Running the Documentation Site

### Preview the Site Locally

To preview the documentation site locally with live reload:

```bash
hugo serve
```

The site will be available at `http://localhost:1313`. The server will automatically rebuild and refresh the browser when you make changes to the content.

### Additional Server Options

#### Include Draft Content
To preview draft content that isn't ready for publication:

```bash
hugo serve --buildDrafts
# or
hugo serve -D
```

#### Navigate to Changed Pages
Automatically navigate to the last modified page when changes are detected:

```bash
hugo serve --navigateToChanged
```

#### Custom Port and Host
To run the server on a different port or bind to all interfaces:

```bash
hugo serve --port 8080 --bind 0.0.0.0
```

### Building for Production

To build the static site for deployment:

```bash
hugo
```

This generates the static files in the `public/` directory, which can be deployed to any web server.

## Project Structure

```
├── config.yml          # Hugo configuration
├── content/            # Documentation content
│   ├── en/            # English content
│   └── es/            # Spanish content
├── layouts/           # HTML templates
├── static/           # Static assets (images, etc.)
└── public/           # Generated site (created by Hugo)
```

## Contributing

1. Make your changes to the content files in the `content/` directory
2. Preview your changes with `hugo serve`
3. Commit and push your changes

For more information about Hugo, visit the [official documentation](https://gohugo.io/documentation/).

## AI Assistant Integration with Ruler

This documentation project is optimized for AI-assisted development using [Ruler](https://github.com/intellectronica/ruler), which centralizes AI coding assistant instructions across multiple tools.

### About Ruler

Ruler provides a single source of truth for AI agent instructions, automatically distributing them to the configuration files of supported AI coding assistants. This ensures consistent guidance across all AI tools and eliminates the need to maintain separate configuration files.

### Supported AI Assistants

The following AI assistants are configured to work with this project:

| Assistant        | Configuration File                    | Purpose                          |
|------------------|---------------------------------------|----------------------------------|
| GitHub Copilot   | `.github/copilot-instructions.md`    | VS Code integration             |
| Claude Code      | `CLAUDE.md`                          | Anthropic's coding assistant    |
| Junie           | `.junie/guidelines.md`               | JetBrains AI assistant          |
| Gemini CLI      | `GEMINI.md`                          | Google's AI assistant           |

### Setting Up Ruler

#### Prerequisites

Node.js 18.x or higher is required.

#### Installation

Install Ruler globally for CLI usage:

```bash
npm install -g @intellectronica/ruler
```

Or use it directly with npx:

```bash
npx @intellectronica/ruler apply
```

#### Project Initialization

1. Navigate to this project's root directory
2. Initialize Ruler configuration:

```bash
ruler init
```

This creates:
- `.ruler/` directory for centralized AI instructions
- `.ruler/instructions.md` - starter file for coding guidelines
- `.ruler/ruler.toml` - configuration for Ruler behavior
- `.ruler/mcp.json` - Model Context Protocol server settings

#### Basic Configuration

Edit `.ruler/ruler.toml` to specify which AI assistants to target:

```toml
# Default agents to configure
default_agents = ["copilot", "claude", "junie", "gemini-cli"]

# GitHub Copilot configuration
[agents.copilot]
enabled = true
output_path = ".github/copilot-instructions.md"

# Claude Code configuration  
[agents.claude]
enabled = true
output_path = "CLAUDE.md"

# Junie configuration
[agents.junie]
enabled = true
output_path = ".junie/guidelines.md"

# Gemini CLI configuration
[agents.gemini-cli]
enabled = true
output_path = "GEMINI.md"

# Disable all other agents
[agents.aider]
enabled = false

[agents.amp]
enabled = false

[agents.augmentcode]
enabled = false

[agents.cline]
enabled = false

[agents.codex]
enabled = false

[agents.cursor]
enabled = false

[agents.firebase]
enabled = false

[agents.goose]
enabled = false

[agents.jules]
enabled = false

[agents.kilocode]
enabled = false

[agents.opencode]
enabled = false

[agents.openhands]
enabled = false

[agents.windsurf]
enabled = false
```

#### Writing AI Instructions

Create focused instruction files in the `.ruler/` directory to provide project-specific context and guidelines. The existing `.ruler/instructions.md` file contains comprehensive guidelines for this Hugo-based documentation site.

You can add additional instruction files as needed:

**`.ruler/team_guidelines.md`:**
```markdown
# Team Development Guidelines

## Code Review Process
- All changes require review before merging
- Test documentation builds locally first
- Verify multilingual content consistency

## Release Process
- Update version information in data/versions.yaml
- Create version-specific content files
- Test all language variants
```

### Applying AI Instructions

#### Update All Configured Assistants

```bash
ruler apply
```

#### Target Specific Assistants

For GitHub Copilot and Claude only:
```bash
ruler apply --agents copilot,claude
```

For Junie and Gemini only:
```bash
ruler apply --agents junie,gemini-cli
```

For all configured assistants:
```bash
ruler apply --agents copilot,claude,junie,gemini-cli
```

#### Verbose Output

See detailed information about what Ruler is doing:
```bash
ruler apply --verbose
```

### Common Workflows

#### Daily Development

1. Update AI instructions as needed in `.ruler/` files
2. Apply changes: `ruler apply`
3. Continue development with consistent AI assistance

#### Team Onboarding

1. Clone the repository
2. Install Ruler: `npm install -g @intellectronica/ruler`
3. Apply configurations: `ruler apply`
4. AI assistants now have project-specific context

#### Updating Instructions

1. Edit files in `.ruler/` directory
2. Apply changes: `ruler apply`
3. All configured AI assistants receive updates automatically

### Reverting Changes

If you need to remove Ruler-generated configurations:

```bash
# Preview what would be reverted
ruler revert --dry-run

# Revert all changes
ruler revert

# Revert specific assistants only
ruler revert --agents copilot,claude,gemini-cli
```

### Version Control

Ruler automatically manages `.gitignore` to exclude generated configuration files while preserving the source instructions in `.ruler/`. The centralized instructions are tracked in version control, but the generated assistant-specific files are not.

### Troubleshooting

**Configuration not applying:**
- Verify Ruler is installed: `ruler --version`
- Check configuration syntax: `ruler apply --verbose`
- Ensure agents are enabled in `.ruler/ruler.toml`

**Inconsistent AI behavior:**
- Run `ruler apply` to ensure all assistants have latest instructions
- Check that `.ruler/` files contain comprehensive guidelines
- Verify assistant-specific configuration files were generated

For more information about Ruler, visit the [official repository](https://github.com/intellectronica/ruler).
