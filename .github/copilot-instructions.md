# Copilot Instructions for css-riso

## Project Overview

This repository demonstrates CSS risograph-style print effects using SVG filters. The project showcases how to create authentic printing imperfections like misregistration, color bleeding, and paper texture using web technologies.

**Live demo:** https://jonmccon.github.io/css-riso/

## Project Structure

```
css-riso/
├── index.html           # Main demo page with SVG filter implementation
├── img/                 # Image assets
├── .github/
│   └── Workflows/       # GitHub Actions workflows
│       ├── static.yml   # Deploys main branch to GitHub Pages
│       └── preview-deploy.yml  # Deploys copilot branches as previews
└── README.md           # Project documentation
```

## Technology Stack

- **HTML5**: Semantic markup for demo content
- **CSS3**: Styling and layout, including advanced filters
- **SVG Filters**: Core technology for creating risograph effects
  - `feColorMatrix`: Channel separation
  - `feOffset`: Misregistration
  - `feTurbulence`: Noise generation
  - `feDisplacementMap`: Ink diffusion
  - `feGaussianBlur`: Soft bleeding
  - `feBlend`: Channel recombination

## Code Style Guidelines

### HTML
- Use semantic HTML5 elements
- Include descriptive comments for major sections
- Keep inline styles minimal; prefer CSS classes
- Use BEM-like naming for utility classes (e.g., `ink-print--jitter`)

### CSS
- Follow the existing structure: base styles, utilities, demo styles
- Use custom properties for reusable values where appropriate
- Prefer `clamp()` for responsive typography
- Comment complex filter chains and SVG manipulations
- Maintain readability with clear section separators

### SVG Filters
- Always include `color-interpolation-filters="sRGB"` for consistent color
- Extend filter region with `x="-20%" y="-20%" width="140%" height="140%"` to prevent clipping
- Name filter results descriptively (e.g., `rOff`, `gSoft`, `final`)
- Document the purpose of each filter primitive in comments
- Keep filters modular for easy experimentation

## Development Workflow

### Making Changes
1. Create branches following the `copilot/*` or `copilot-*` pattern for automatic preview deployment
2. Edit `index.html` for both markup and styling changes
3. Test locally by opening `index.html` in a browser
4. Push changes to trigger preview deployment

### Preview Deployments
- Copilot branches automatically deploy to: `https://jonmccon.github.io/css-riso/{branch-name}/`
- Preview builds include a yellow banner indicating branch and commit
- Main site remains at root URL

### Production Deployments
- Only changes to `main` branch are deployed to production
- Deployment is automatic via GitHub Actions

## Testing Guidelines

### Manual Testing
- Open `index.html` in multiple browsers (Chrome, Firefox, Safari)
- Verify SVG filters render correctly across browsers
- Check responsive behavior at different viewport sizes
- Confirm text remains readable despite filter effects
- Validate accessibility (color contrast, semantic markup)

### Visual Testing
- Compare filter effects against reference examples
- Ensure misregistration appears subtle and authentic
- Verify paper grain overlay is visible but not overwhelming
- Check that text jitter is micro-scale (sub-pixel)

## Best Practices

### SVG Filter Performance
- Keep filter chains as simple as possible
- Minimize the number of blur operations
- Use appropriate `baseFrequency` values for turbulence (higher = more detail = slower)
- Test performance on lower-end devices

### Accessibility
- Ensure filtered text maintains sufficient contrast
- Don't rely solely on color to convey information
- Provide alternative text for decorative elements
- Test with screen readers when adding new content

### Maintenance
- Document any new filter parameters with comments
- Keep the README updated with new features or techniques
- Reference useful tools (like fecolormatrix.com) in comments or docs
- Maintain backward compatibility when modifying existing filters

## Useful Resources

- [feColorMatrix tool](https://fecolormatrix.com/) - Visual tool for creating color matrices
- [Texture example](https://codepen.io/chriskirknielsen/pen/rNmgXyV) - Additional texture techniques

## Common Tasks

### Adding a New Filter Variant
1. Copy the existing `#ink-print` filter in the SVG `<defs>`
2. Give it a unique ID (e.g., `#ink-print-variant`)
3. Adjust parameters (offset values, blur amounts, turbulence settings)
4. Create a new CSS class that references it: `filter: url(#ink-print-variant);`
5. Add a demo section showcasing the new variant

### Adjusting Color Separation
- Modify the `feColorMatrix` values for each channel (r, g, b)
- Higher values intensify that channel (max 1.0)
- Lower values reduce intensity (min 0.0)
- Keep alpha channel around 0.8 for subtle transparency

### Tuning Misregistration
- Adjust `feOffset` `dx` and `dy` values
- Smaller values (< 2px) = subtle, authentic effect
- Larger values = more dramatic, artistic effect
- Mix positive and negative offsets for multi-directional shift

## Notes

- This is a static HTML project with no build process
- No dependencies or package managers required
- Changes are immediately visible by refreshing the browser
- The project emphasizes visual effects over functionality
