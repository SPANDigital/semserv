---
Source: .ruler/instructions.md
---
# Semantic Service Naming Documentation - AI Assistant Instructions

## Project Overview

This is a **Hugo static site** that documents the "Semantic Service Naming" (SemServ) specification - a standardized approach for creating meaningful service names that remain stable over time. The specification defines how to compose service names from three elements: [Namespace] - [Domain|Entity] - [Role].

**Key project details:**
- **Framework**: Hugo static site generator with Presidium theme
- **Purpose**: Technical documentation for service naming conventions
- **Audience**: Software engineers, DevOps teams, system architects
- **Languages**: English (primary) and Spanish
- **Versioning**: Multiple specification versions (1.0.0, 0.1.2, 0.1.1)

## Content Structure & Conventions

### Hugo Site Architecture
- **Base URL**: `/docs/sem-serv-docs`
- **Content organization**: Multilingual with version-specific pages
- **Layout system**: Custom Presidium-based theme
- **Configuration**: `config.yml` with multilingual and versioning support

### Content Directory Structure
```
content/
├── _index.md              # Root redirect page
├── en/                    # English content
│   ├── _index.md         # Language redirect
│   ├── 1.0.0.md          # Current specification version
│   ├── 0.1.2.md          # Previous version
│   └── 0.1.1.md          # Previous version
└── es/                    # Spanish content
    ├── _index.md         # Language redirect
    └── 0.1.2.md          # Translated version
```

### Version Management
- Versions follow semantic versioning (SemVer) principles
- Current stable version: **1.0.0**
- Version data managed in `data/versions.yaml`
- Each version has its own content file with full specification

## Writing Guidelines

### Content Style
- **Tone**: Professional, technical, authoritative
- **Voice**: Clear, direct, instructional
- **Audience**: Technical professionals familiar with service architecture
- **Format**: Technical specification with examples and explanations

### Documentation Patterns
1. **Specification sections** must include:
   - Summary with key formula
   - Detailed introduction explaining the problem
   - Numbered specification rules with RFC 2119 keywords
   - Real-world examples
   - FAQ addressing common concerns
   - Formal grammar (Backus-Naur Form)

2. **Examples format**:
   - Use realistic service names: `Payment-Processor`, `Hydra-Job-Scheduler`
   - Show both simple and namespaced examples
   - Include derived names (executables, deployments, instances)
   - Use consistent formatting with backticks for code

3. **Technical terminology**:
   - Use RFC 2119 keywords: MUST, SHOULD, MAY, etc.
   - Capitalize key concepts: Domain, Entity, Role, Namespace
   - Use consistent formatting for service name patterns

### Front Matter Requirements
All content files must include:
```yaml
---
title: "Semantic Service Naming [version]"
description: "Brief description of the specification"
keywords: "service naming, semantic service naming, semserv, semver"
author: "email@spandigital.com"
---
```

## Hugo-Specific Instructions

### Content Creation
- **File naming**: Use version numbers as filenames (e.g., `1.0.0.md`)
- **Hugo shortcodes**: Available for enhanced functionality
- **Markdown features**: Full Goldmark support with HTML allowed
- **Cross-references**: Use Hugo's built-in linking for internal references

### Multilingual Support
- **Primary language**: English (`en/`)
- **Secondary language**: Spanish (`es/`)
- **Translation approach**: Full content translation, not just UI
- **Language-specific URLs**: Each language has its own path structure

### Theme Integration
- **Presidium theme**: SPAN Digital's documentation theme
- **Layout types**: Uses custom layouts (`redirect`, `language-redirect`)
- **Styling**: Custom CSS through Presidium base modules
- **Features**: Built-in search, menu generation, version navigation

### Build and Deployment
- **Development**: Use `hugo serve` for local preview
- **Production**: Generate with `hugo` command
- **Output**: Static files in `public/` directory
- **Assets**: Images and static files in `static/` directory

## Content Maintenance

### Version Updates
1. Create new content file with version number
2. Update `data/versions.yaml` to include new version
3. Mark previous version as non-current if needed
4. Ensure all languages have consistent version availability

### Quality Standards
- **Accuracy**: Technical specifications must be precise and implementable
- **Consistency**: Use established terminology throughout
- **Completeness**: Each version should be self-contained
- **Examples**: Provide realistic, practical examples for all concepts

### Testing Guidelines
- **Preview locally**: Always test with `hugo serve` before committing
- **Cross-browser**: Verify rendering across different browsers
- **Mobile responsiveness**: Ensure content works on mobile devices
- **Link validation**: Check all internal and external links

## Development Workflow

### Making Changes
1. **Content updates**: Edit markdown files in `content/` directory
2. **Configuration**: Modify `config.yml` for site-wide changes
3. **Data updates**: Update `data/versions.yaml` for version management
4. **Preview**: Use `hugo serve` to review changes locally

### File Organization
- **Layouts**: Custom layouts in `layouts/` directory
- **Static assets**: Images, CSS, JS in `static/` directory
- **Data files**: Structured data in `data/` directory
- **Configuration**: Single `config.yml` file for all settings

### Git Workflow
- **Branch naming**: Use descriptive feature branch names
- **Commit messages**: Clear, descriptive commits
- **Testing**: Verify build with `hugo` before pushing
- **Documentation**: Update README.md when adding new features

## AI Assistant Specific Guidelines

### Code Assistance
- **Hugo syntax**: Understand Hugo templating and shortcodes
- **YAML structure**: Properly format configuration and data files
- **Markdown**: Use Hugo-flavored markdown with proper front matter
- **File paths**: Always use correct Hugo content organization

### Content Suggestions
- **Maintain consistency** with existing specification language
- **Preserve technical accuracy** of service naming rules
- **Follow established patterns** for examples and explanations
- **Respect multilingual** structure when suggesting changes

### Technical Context
- **Static site generation**: Understand Hugo's build process
- **Theme integration**: Work within Presidium theme constraints
- **Version management**: Respect the versioning system
- **SEO considerations**: Maintain proper meta tags and structure
