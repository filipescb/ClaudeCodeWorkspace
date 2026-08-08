# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Add a brief description of what this project does and its main purpose here.

## Development Setup

Add project-specific setup instructions here (e.g., dependencies, environment variables, initial configuration).

## Common Commands

Document the commands typically used during development:

- **Build/Start:** `[add command]`
- **Tests:** `[add command]`
- **Lint/Format:** `[add command]`
- **Run single test:** `[add command]`

## Architecture

Add high-level architecture notes here once the project structure is established. Include:
- Key directories and their purposes
- How major components interact
- Any important design decisions or constraints

## Git Workflow

We use Git with GitHub for version control. **Commit and push regularly to `origin/master` to ensure we never lose work.**

### Commit Guidelines

- **Commit frequently:** Make commits after completing logical chunks of work, not just at the end of the day
- **Clear messages:** Write descriptive commit messages that explain the "why" and "what" of the change
  - Good: `Add user authentication flow for login page`
  - Poor: `fix stuff` or `updates`
- **Atomic commits:** Keep each commit focused on a single feature, fix, or refactor. Don't mix unrelated changes
- **Push regularly:** Push to GitHub after each commit or at least daily, so we have a complete backup and history

### Command Reference

```bash
# Check status
git status

# Stage files
git add <file>          # Add specific file
git add .               # Add all changes

# Commit
git commit -m "Description of changes"

# Push to GitHub
git push origin master

# View history
git log --oneline       # Concise commit history
git log -p              # Detailed commit history with diffs
```

### Important

Never let uncommitted work sit for long. If something breaks or needs reverting, having commits pushed to GitHub means we can always recover from any state.
