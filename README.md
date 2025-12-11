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
├── .gitignore
└── README.md
```

## Usage

These design tokens should be used across all projects to maintain visual consistency and enable efficient design-to-development workflows.
