# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **WordPress child theme** for the Moiraine parent theme. It extends the parent theme with custom colors and styles while maintaining all parent functionality. The child theme follows WordPress block theme standards (theme.json, FSE).

**Parent Theme Location**: `~/code/moiraine` (local development setup)

## Key Architecture

### Child Theme Pattern
- The child theme **inherits** all functionality from the parent Moiraine theme
- `functions.php` only enqueues the child theme stylesheet - it does NOT replicate parent functionality
- Parent theme dependency is declared in `composer.json` as `"imagewize/moiraine": "*"`
- Template override: `style.css` header declares `Template: moiraine`

### theme.json Strategy
The child theme's `theme.json` is **minimal** - it only includes color palette overrides. It does NOT duplicate the parent theme's complete configuration (typography, spacing, shadows, etc.). WordPress automatically merges child theme.json with parent theme.json.

**Current child theme.json includes**:
- Version 3 schema
- Custom color palette (11 colors with specific brand colors)

**Parent theme.json includes** (NOT duplicated in child):
- Typography settings (font families, font sizes, fluid typography)
- Spacing system (7 responsive spacing sizes)
- Shadow presets (8 shadow variations)
- Layout settings (contentSize, wideSize)
- Custom properties (fontWeight, lineHeight)
- Block styles and element styles
- Duotone and gradient presets

### File Structure
```
moiraine-child/
├── theme.json           # Minimal - only color overrides
├── style.css            # Child theme header + any custom CSS
├── functions.php        # Only stylesheet enqueuing
├── patterns/            # Custom block patterns (empty, ready for use)
├── styles/              # Style variations (empty, ready for use)
├── parts/               # Template part overrides (empty, ready for use)
└── assets/fonts/        # Custom fonts (if needed)
```

## Development Commands

### Install Dependencies
```bash
composer install
```

### Code Quality
```bash
# PHP syntax check
composer lint

# WordPress Coding Standards scan
composer wpcs:scan

# Auto-fix WPCS issues
composer wpcs:fix
```

## Customization Workflows

### Updating Colors
When parent theme colors change, update child `theme.json`:
1. Check parent theme's color palette in `~/code/moiraine/theme.json`
2. Update only the colors you want to override in child `theme.json`
3. Keep the same color slugs for consistency (e.g., "primary", "main", "base")

### Adding Custom Patterns
1. Create pattern files in `patterns/` directory
2. To add to parent theme categories, register the parent categories in `functions.php`:
```php
register_block_pattern_category('moiraine/features', array('label' => __('Features', 'moiraine-child')));
```

### Adding Style Variations
1. Create JSON files in `styles/` directory following theme.json schema
2. Define custom color palettes or typography settings
3. WordPress automatically detects and lists them in Site Editor

### Overriding Template Parts
Place HTML files in `parts/` to override parent:
- `parts/header.html` - Custom header
- `parts/footer.html` - Custom footer
- `parts/sidebar.html` - Custom sidebar

## WordPress Context

### Requirements
- WordPress 6.0+
- PHP 7.3+
- Parent Moiraine theme must be installed and available

### Theme Activation
The child theme depends on the parent theme. WordPress will warn if parent is not available.

## Comparing with Parent Theme

When syncing updates from parent theme:
1. Parent location: `~/code/moiraine/`
2. Compare `theme.json` files - only merge new color definitions or features you want
3. DO NOT copy parent's entire theme.json - keep child minimal
4. Check parent `functions.php` for new features, but don't duplicate in child
5. Parent has extensive `inc/` directory with block extensions - child doesn't need this
