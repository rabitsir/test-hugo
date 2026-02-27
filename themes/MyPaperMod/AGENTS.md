# Hugo PaperMod Theme

## Project Overview

Hugo PaperMod is a fast, clean, responsive Hugo theme designed for blogs. It is based on the original [hugo-paper](https://github.com/nanxiaobei/hugo-paper) theme with additional features and customization options.

- **Name**: PaperMod
- **License**: MIT
- **Author**: Aditya Telange
- **Homepage**: https://adityatelange.github.io/hugo-PaperMod/
- **Minimum Hugo Version**: 0.146.0
- **Repository**: https://github.com/adityatelange/hugo-PaperMod

## Technology Stack

- **Static Site Generator**: [Hugo](https://gohugo.io/) (Go-based)
- **Module System**: Go Modules (`go.mod`)
- **Styling**: Pure CSS (no CSS frameworks)
- **JavaScript**: Vanilla JavaScript (no external JS frameworks)
- **Search**: [Fuse.js](https://fusejs.io/) (lightweight fuzzy-search library)
- **Icons**: Inline SVG (Feather Icons, Simple Icons)
- **Syntax Highlighting**: Hugo's built-in Chroma highlighter

## Project Structure

```
.
├── assets/              # Static assets processed by Hugo's asset pipeline
│   ├── css/            # Stylesheets
│   │   ├── common/     # Common page components (header, footer, post styles)
│   │   ├── core/       # Core styles (reset, theme variables, media queries)
│   │   ├── extended/   # Extension point for custom CSS
│   │   └── includes/   # Additional features (chroma styles, scrollbar)
│   └── js/             # JavaScript files
│       ├── fastsearch.js      # Search functionality
│       └── fuse.basic.min.js  # Fuse.js library
├── i18n/               # Internationalization files (46 languages supported)
├── images/             # Theme screenshots for Hugo themes directory
├── layouts/            # Hugo HTML templates
│   ├── _default/       # Default page layouts
│   ├── _default/_markup/  # Render hooks
│   ├── partials/       # Reusable template components
│   │   └── templates/  # SEO templates (OpenGraph, Twitter Cards, Schema)
│   └── shortcodes/     # Custom Hugo shortcodes
├── .github/            # GitHub configuration
│   ├── workflows/      # GitHub Actions CI/CD
│   └── ISSUE_TEMPLATE/ # Issue templates
├── go.mod              # Go module definition
├── LICENSE             # MIT License
├── README.md           # User documentation
└── theme.toml          # Hugo theme metadata
```

## Key Layout Templates

| Template | Purpose |
|----------|---------|
| `_default/baseof.html` | Base layout for all pages |
| `_default/single.html` | Individual post/page layout |
| `_default/list.html` | List pages (home, sections, taxonomies) |
| `_default/search.html` | Search page layout |
| `_default/archives.html` | Archives page layout |
| `partials/head.html` | HTML head section with asset bundling |
| `partials/header.html` | Site header with navigation |
| `partials/footer.html` | Site footer |

## Asset Pipeline

The theme uses Hugo's built-in asset pipeline for CSS and JS processing:

### CSS Pipeline (in `partials/head.html`)
1. **Core CSS**: Theme variables → Reset → Common styles → Chroma syntax highlighting
2. **Extended CSS**: Custom styles from `assets/css/extended/`
3. **Processing**: Concatenation → Minification → Fingerprinting (optional)

### JavaScript
- **Search Page Only**: Fuse.js + fastsearch.js bundled together
- **Theme Toggle**: Inline JavaScript in footer
- **Code Copy**: Inline JavaScript for copy-to-clipboard functionality

## Configuration Parameters

The theme uses Hugo's site parameters (`site.Params`) for configuration:

### Key Parameter Groups
- `defaultTheme`: "light", "dark", or "auto"
- `disableThemeToggle`: Disable theme toggle button
- `profileMode`: Enable profile mode for homepage
- `homeInfoParams`: Show info block on homepage
- `ShowToc`: Show table of contents
- `ShowShareButtons`: Show social share buttons
- `ShowCodeCopyButtons`: Show copy button on code blocks
- `assets`: Favicon and asset configuration
- `fuseOpts`: Fuse.js search configuration

## Shortcodes

| Shortcode | Description |
|-----------|-------------|
| `collapse` | Collapsible content block |
| `figure` | Enhanced figure with lazy loading |
| `inTextImg` | Inline image shortcode |
| `ltr` / `rtl` | Text direction wrappers |
| `rawhtml` | Raw HTML injection |

## Development Conventions

### Code Style
- **HTML/Templates**: Use Hugo's Go template syntax with proper indentation
- **CSS**: Modular CSS files organized by component
- **JavaScript**: Vanilla JS, ES6+ features allowed
- **Naming**: kebab-case for CSS classes, camelCase for JavaScript

### Template Best Practices
- Use `partialCached` for reusable components when appropriate
- Check for parameter existence before use: `{{ if .Param "key" }}`
- Support multilingual: Use `i18n` function for user-facing strings
- Respect accessibility: Include ARIA labels and semantic HTML

### CSS Architecture
- **Core Variables**: Defined in `theme-vars.css` for theming
- **Responsive Design**: Mobile-first approach with breakpoints in `zmedia.css`
- **Dark Mode**: CSS custom properties switch based on `data-theme` attribute

## Internationalization (i18n)

- **46 Languages Supported**: Including English, Chinese, Japanese, Spanish, French, German, Arabic, and more
- **Translation Keys**: Defined in `i18n/*.yaml` files
- **Key IDs**: `prev_page`, `next_page`, `read_time`, `words`, `toc`, `translations`, `home`, `edit_post`, `code_copy`, `code_copied`

## Build and Deployment

### Local Development
```bash
# Install Hugo (v0.146.0 or later)
# Run Hugo server
hugo server -D
```

### GitHub Actions Workflow
- **File**: `.github/workflows/gh-pages.yml`
- **Triggers**: Push to `master` or `exampleSite` branches
- **Build Command**: `hugo --buildDrafts --gc --baseURL <url>`
- **Deployment**: GitHub Pages

### Demo Site
- The demo is built from the `exampleSite` branch
- Uses git submodules to include the theme

## Testing

This theme does not include automated unit tests. Testing is done through:

1. **Manual Testing**: Verify rendering across different Hugo versions
2. **Visual Testing**: Check responsive design on multiple devices
3. **Browser Testing**: Ensure compatibility with modern browsers
4. **Example Site**: Use the `exampleSite` branch for comprehensive testing

## Security Considerations

- **No External CDN Dependencies**: All assets are self-hosted
- **Subresource Integrity**: CSS/JS fingerprinting supported via `disableFingerprinting` parameter
- **Content Security Policy**: Compatible with strict CSP (no inline scripts required for core functionality)
- **SafeHTML**: Careful use of `safeHTML` and `markdownify` functions

## Contributing Guidelines

### Pull Request Checklist (from `.github/PULL_REQUEST_TEMPLATE.md`)
- [ ] Enable maintainer edits
- [ ] Verify code works as intended
- [ ] Does NOT include CDN resources/links
- [ ] Does NOT include unrelated scripts
- [ ] Social icons must have permissive licenses
- [ ] Translations use the provided template

### Issue Reporting
- Use GitHub Issues for bugs and feature requests
- Use GitHub Discussions for questions
- Join Discord community for real-time help
- Check Wiki and FAQs before reporting

## External Dependencies

### Bundled Libraries
- **Fuse.js** (`fuse.basic.min.js`): Client-side fuzzy search (MIT License)

### Third-Party Resources (Not Bundled)
- **Highlight.js**: Syntax highlighting (mentioned as inspiration)
- **Feather Icons**: Icon design inspiration
- **Simple Icons**: Social media icons

## SEO Features

- OpenGraph meta tags
- Twitter Cards support
- JSON-LD Schema.org structured data
- Canonical URLs
- RSS feed generation
- Multilingual hreflang tags
- Robots meta tag control

## License

MIT License - Copyright (c) 2020-2026 nanxiaobei and adityatelange
