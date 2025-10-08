# Moiraine Child Theme

A complete child theme template for the [Moiraine WordPress theme](https://github.com/imagewize/moiraine). This serves as a fully functional starting point for creating custom child themes with all parent theme features included.

## Description

Moiraine Child is a complete child theme template that includes the full parent Moiraine theme configuration. It comes with a complete design system (colors, typography, spacing, shadows, gradients, and duotone filters) ready to use out of the box. You can selectively modify any aspect to create your own branded child theme.

## How theme.json Works in This Child Theme

The child theme's `theme.json` includes a **complete copy** of the parent theme's configuration. This approach provides:

- **Standalone functionality**: Works immediately with full styling - no blank pages
- **Easy customization**: Modify any setting directly in the child theme.json
- **Clear starting point**: All design tokens visible and ready to customize
- **Version control**: Track exactly what settings your child theme uses

### Example: Adding Custom Colors

To override the parent's color palette, edit `theme.json`:

```json
{
  "$schema": "https://schemas.wp.org/trunk/theme.json",
  "version": 3,
  "settings": {
    "color": {
      "palette": [
        {
          "name": "Brand",
          "slug": "primary",
          "color": "#yourBrandColor"
        },
        {
          "name": "Brand Accent",
          "slug": "primary-accent",
          "color": "#yourAccentColor"
        }
        // Add more custom colors as needed
      ]
    }
  }
}
```

You can override any part of the parent's theme.json - colors, typography, spacing, or even add new settings. Anything not specified in the child will be inherited from the parent.

## Features

- Complete theme.json with full parent design system included
- Works standalone with proper styling from the start
- All 11 brand colors, typography settings, spacing system, shadows, gradients, and duotone presets
- Easy to customize - all settings visible in child theme
- Follows WordPress child theme best practices

## Requirements

- WordPress 6.0 or higher
- Moiraine parent theme must be installed
- PHP 7.4 or higher

## Installation

1. Download and install the [parent Moiraine theme](https://github.com/imagewize/moiraine)
2. Upload the Moiraine Child theme to your WordPress site
3. Activate the Moiraine Child theme from the WordPress admin panel

## Customization

This child theme template provides multiple ways to customize your site:

- **Modify colors** in the `theme.json` file (complete palette included)
- **Adjust typography** settings - fonts, sizes, weights already defined
- **Customize spacing** - responsive spacing system included
- **Add custom CSS** to the `style.css` file for additional styling
- **Create custom block patterns** in the `patterns/` directory
- **Add style variations** in the `styles/` directory
- **Include custom fonts** in the `assets/fonts/` directory
- **Override template parts** in the `parts/` directory (headers, footers, etc.)

The theme works immediately with full styling - customize as needed.

### Adding Custom Patterns to Parent Theme Categories

When creating custom block patterns, you can register them to appear within the parent Moiraine theme's existing pattern categories. This allows your custom patterns to be organized alongside the parent theme patterns for a unified editing experience.

To register your patterns with parent theme categories:

1. Create your pattern files in the `patterns` directory of your child theme
2. In your child theme's functions.php, hook into the pattern registration process
3. Use the same category slugs that the parent theme uses to add your patterns to those categories

Example code for functions.php:
```php
function moiraine_child_register_pattern_categories() {
    // Register existing parent theme categories again in the child theme
    // This ensures your patterns can be added to these categories
    register_block_pattern_category(
        'moiraine/features',
        array('label' => __('Features', 'moiraine-child'))
    );
    
    register_block_pattern_category(
        'moiraine/pages',
        array('label' => __('Pages', 'moiraine-child'))
    );
    
    // Add more parent categories as needed
}
add_action('init', 'moiraine_child_register_pattern_categories', 5);
```

By using the same category slugs as the parent theme, your custom patterns will appear in the same categories in the pattern inserter, creating a seamless experience for site editors.

### Adding Style Variations

To create custom style variations:

1. Navigate to the `styles` directory in your child theme
2. Create a new JSON file (e.g., `my-custom-style.json`)
3. Define your variation settings following the WordPress style variation format
4. Your new style variation will appear in the WordPress Site Editor under "Styles"

Example of a style variation file:
```json
{
  "$schema": "https://schemas.wp.org/trunk/theme.json",
  "version": 3,
  "title": "My Custom Style",
  "settings": {
    "color": {
      "palette": [
        {
          "slug": "primary",
          "color": "#yourCustomColor",
          "name": "Primary"
        }
        // Add more colors as needed
      ]
    }
  }
}
```

### Adding Custom Fonts

To add custom fonts to your theme:

1. Place your font files (woff, woff2, etc.) in the `assets/fonts` directory
2. Add the @font-face declarations to your `style.css` file
3. Update your `theme.json` to include the new font family

Example @font-face declaration for style.css:
```css
@font-face {
  font-family: 'Your Custom Font';
  src: url('./assets/fonts/your-custom-font.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}
```

### Customizing Template Parts

The theme includes a `parts` directory with a `.gitkeep` file, allowing you to customize theme parts such as headers, footers, and sidebars:

1. Create template part files in the `parts` directory (e.g., `parts/header.html`)
2. These files will override the corresponding template parts from the parent theme
3. Common parts to customize include:
   - `parts/header.html` - Override the site header
   - `parts/footer.html` - Customize the site footer 
   - `parts/sidebar.html` - Create a custom sidebar

This structure makes it easy to maintain a child theme with custom layouts while still benefiting from parent theme updates.

## Support

For support or more information, visit [Imagewize](https://imagewize.com).

## License

GNU General Public License v2 or later - http://www.gnu.org/licenses/gpl-2.0.html