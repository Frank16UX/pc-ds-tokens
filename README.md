# Design Tokens Repository

## Overview

This repository contains design tokens exported from Figma using the **Tokens Studio plugin**. These tokens are formatted in **W3C DTCG (Design Tokens Community Group) format** and serve as the single source of truth for design values across our design system.

## Repository Status

**Last Updated:** December 11, 2025 at 11:25:30 AM (CST)

## Content

The repository contains the following design token files in the `export-from-figma/` directory:

- `tokens-from-ts.json` - Main design tokens file
- `animation.json` - Animation-related tokens

## Important Notes

### Figma Integration

All values in this repository have been **imported from Figma using the Tokens Studio plugin**. This ensures consistency with our design system and enables seamless synchronization.

### Multiple JSONs per Collection

The `multiple-files/` directory contains design tokens organized into **multiple JSON files per collection**. This structure has been added to support the **development conversion to SCSS**, enabling more modular and maintainable token management. Each collection (e.g., Breakpoints, Elevation, Fonts, Primitives, etc.) is stored in its own JSON file, making it easier to:

- Convert tokens to SCSS variables and mixins
- Maintain and update specific token categories independently
- Improve build performance by loading only needed token sets
- Enable better version control and collaboration

### Manual Adjustments

Some values have been **manually added or modified** due to limitations in the Figma export process:

- **Typography Values** - Manually added as they are not fully supported by the Figma export
- **$radius-full** - Modified from `1000px` to `50%` for better scalability and maintainability
- **Modes Removed** - The "Modes" from the Figma import have been removed since we don't use separate modes or sets aside from the Responsive collection

These adjustments ensure the tokens are practical and usable in our development workflow while maintaining alignment with the design vision.

## File Structure

```
pc-design-tokens/
├── export-from-figma/
│   ├── tokens-from-ts.json
│   └── animation.json
├── multiple-files/
│   ├── $metadata.json
│   ├── $themes.json
│   ├── Breakpoints.json
│   ├── Elevation.json
│   ├── Fonts.json
│   ├── Numeric Tokens.json
│   ├── Primitives.json
│   ├── Ratios.json
│   ├── Responsive/
│   │   ├── Desktop.json
│   │   └── Mobile.json
│   └── Tokens.json
├── .gitignore
└── README.md
```

## Usage

These design tokens should be used across all projects to maintain visual consistency and enable efficient design-to-development workflows.

## Git Operations

This section covers the most common Git operations for working with this repository.

### Branch Strategy

This repository uses a two-branch workflow:

#### **main** (Production Branch)
- **Purpose**: Production-ready design tokens
- **Usage**: All finalized changes are merged here
- **Stability**: Should always contain stable, tested tokens
- **Workflow**: Merge changes from `w3c-dtcg-conversion` after review and validation

#### **w3c-dtcg-conversion** (Staging Branch)
- **Purpose**: Staging area for Tokens Studio updates
- **Usage**: Publish updates directly from Tokens Studio to this branch
- **Workflow**: 
  1. Export tokens from Figma using Tokens Studio
  2. Push updates to `w3c-dtcg-conversion`
  3. Review and test changes
  4. Merge to `main` when ready for production

#### Typical Workflow
```bash
# 1. Update staging branch with new tokens from Tokens Studio
git checkout w3c-dtcg-conversion
git add .
git commit -m "Update tokens from Tokens Studio"
git push origin w3c-dtcg-conversion

# 2. After review, merge to main
git checkout main
git merge w3c-dtcg-conversion
git push origin main
```

### Pulling Changes from Remote

#### Pull changes from the main branch
```bash
git pull origin main
```

#### Pull changes from a specific remote branch
```bash
git pull origin <branch-name>
```

#### Pull and rebase (instead of merge)
```bash
git pull --rebase origin main
```

### Pushing Changes to Remote

#### Push changes to remote main branch
```bash
# First, ensure you're on the main branch
git checkout main

# Stage your changes
git add .

# Commit your changes
git commit -m "Your commit message"

# Push to remote main
git push origin main
```

#### Push changes to an existing remote branch
```bash
# Switch to the branch
git checkout <branch-name>

# Stage and commit your changes
git add .
git commit -m "Your commit message"

# Push to the remote branch
git push origin <branch-name>
```

#### Push changes to a new remote branch
```bash
# Create and switch to a new branch
git checkout -b <new-branch-name>

# Stage and commit your changes
git add .
git commit -m "Your commit message"

# Push to remote and set upstream tracking
git push -u origin <new-branch-name>
```

### Branch Management

#### List all branches (local and remote)
```bash
# Local branches only
git branch

# Remote branches only
git branch -r

# All branches (local and remote)
git branch -a
```

#### Create a new branch
```bash
git checkout -b <new-branch-name>
```

#### Switch between branches
```bash
git checkout <branch-name>
```

#### Delete a local branch
```bash
git branch -d <branch-name>
```

#### Delete a remote branch
```bash
git push origin --delete <branch-name>
```

### Removing Files from Remote Repository

#### Remove a file from remote but keep it locally
```bash
# Remove from Git tracking
git rm --cached <file-path>

# Commit the removal
git commit -m "Remove <file-path> from repository"

# Push to remote
git push origin main
```

#### Remove a directory from remote but keep it locally
```bash
# Remove from Git tracking
git rm -r --cached <directory-path>

# Commit the removal
git commit -m "Remove <directory-path> from repository"

# Push to remote
git push origin main
```

#### Sync remote repository with current local file structure
This is useful when you've updated `.gitignore` and want to remove previously tracked files:

```bash
# Remove all files from Git's index
git rm -r --cached .

# Re-add all files (respecting .gitignore)
git add .

# Commit the changes
git commit -m "Sync repository with current file structure"

# Push to remote
git push origin main
```

### Checking Repository Status

#### View current status
```bash
git status
```

#### View commit history
```bash
# Basic log
git log

# Condensed log (one line per commit)
git log --oneline

# View last N commits
git log -n 5
```

#### View differences
```bash
# See unstaged changes
git diff

# See staged changes
git diff --staged

# Compare with remote
git diff origin/main
```

### Undoing Changes

#### Discard local changes (unstaged)
```bash
# Discard changes to a specific file
git checkout -- <file-path>

# Discard all local changes
git checkout -- .
```

#### Unstage files (keep changes)
```bash
# Unstage a specific file
git reset HEAD <file-path>

# Unstage all files
git reset HEAD
```

#### Undo last commit (keep changes)
```bash
git reset --soft HEAD~1
```

### Best Practices

1. **Always pull before pushing** to avoid conflicts:
   ```bash
   git pull origin main
   git push origin main
   ```

2. **Use descriptive commit messages** that explain what changed and why

3. **Create feature branches** for new work instead of committing directly to main:
   ```bash
   git checkout -b feature/token-updates
   ```

4. **Keep commits focused** - each commit should represent a single logical change

5. **Review changes before committing**:
   ```bash
   git status
   git diff
   ```

6. **Regularly sync with remote** to stay up-to-date with team changes
