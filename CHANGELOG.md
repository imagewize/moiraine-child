# Changelog

All notable changes to the Moiraine Child theme will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2025-10-08

### Changed
- **theme.json**: Synchronized color palette with parent theme v2.3.0
  - Updated `primary-accent` from `#DDDAFB` to `#e9e7ff`
  - Updated `primary-alt-accent` from `#575094` to `#3d386b`
  - Updated `secondary` (Base Accent) from `#5F5F82` to `#545473`

### Added
- **theme.json**: Added parent theme features for better compatibility
  - Added `appearanceTools: true` for enhanced editor tools
  - Added 5 duotone presets (Primary, Secondary, Accent, Neutral, High Contrast)
  - Added 6 gradient presets (Purple, Blue, Royal Blue, Pink, Black, Heat)
  - Added `link: true` for color link support
- **style.css**: Updated theme metadata
  - Added `Tested up to: 6.7.1`
  - Added `Requires PHP: 7.3`
- **composer.json**: Enhanced WPCS script exclusion patterns
  - Added exclusions for `*/node_modules/*`, `*/inc/blocks/*`, `*.js` to match parent theme
- **CHANGELOG.md**: Added comprehensive changelog tracking all version history
- **CLAUDE.md**: Added AI assistant documentation for future development work

## [1.0.1] - 2025-04-23

### Added
- **Composer Support**: Added composer.json for package management
  - PHP linting with `php-parallel-lint`
  - WordPress Coding Standards with `wpcs`
  - PHPCompatibility checks
  - Composer scripts: `lint`, `wpcs:scan`, `wpcs:fix`
- **Template Parts Structure**: Added `parts/` directory with `.gitkeep` for custom template part overrides
- **Documentation**: Added comprehensive README.md with customization guides
  - Pattern registration guide for parent theme categories
  - Style variations creation guide
  - Custom fonts integration guide
  - Template parts customization instructions

### Changed
- **License**: Migrated license to LICENSE.md format
- **style.css**: Updated metadata and theme header comments

## [1.0.0] - 2025-03-27

### Added
- Initial release of Moiraine Child theme
- **Custom Color Palette**: Brand-specific color overrides in theme.json
  - Brand colors: Primary (`#5344F4`), Primary Accent, Primary Alt, Primary Alt Accent
  - Contrast colors: Main (`#1E1E26`), Main Accent
  - Base colors: Base (`#fff`), Secondary, Tertiary
  - Border colors: Border Light, Border Dark
- **Theme Structure**: Essential child theme files
  - `theme.json` with custom color palette
  - `style.css` with theme headers
  - `functions.php` for parent stylesheet enqueuing
  - `screenshot.png` theme screenshot
  - Empty directories for future customization: `patterns/`, `styles/`
- **Asset Management**: Created `assets/` directory structure with subdirectories
  - `assets/fonts/` for custom font files
  - `assets/images/` for theme images
  - `assets/styles/` for additional stylesheets
- **WordPress Theme Standards**: Proper child theme implementation
  - Parent theme dependency (`Template: moiraine`)
  - GPL v2+ licensing
  - WordPress 6.0+ compatibility
  - PHP 7.4+ compatibility

### Technical Notes
- This is a minimal child theme that inherits all functionality from parent Moiraine theme
- Only overrides color palette in theme.json - all other settings inherited from parent
- Uses WordPress Block Theme (FSE) architecture
- Compatible with parent theme version 2.3.0
