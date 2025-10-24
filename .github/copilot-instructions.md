# GitHub Copilot Custom Instructions - Dive Into Unicorn Magic ✨🦄

## Project Overview
This is a whimsical, unicorn-themed educational website reimagining Mark Pilgrim's "Dive Into HTML5". The project transforms technical HTML5 documentation into an enchanting learning experience using creative storytelling, magical themes, and beautiful visual design.

## Code Style & Standards

### HTML
- Use semantic HTML5 elements throughout
- Maintain accessibility with proper ARIA attributes where needed
- Keep markup clean and well-structured
- Include whimsical comments that fit the unicorn theme
- Use meaningful class names that reference the magical theme when appropriate

### CSS
- Use the established CSS custom properties defined in `unicorn-style.css`:
  - `--unicorn-purple: #9b59b6`
  - `--unicorn-pink: #ff69b4`
  - `--unicorn-blue: #87ceeb`
  - `--unicorn-gold: #ffd700`
  - `--magic-gradient`, `--sparkle-gradient`, etc.
- Prefer modern CSS (flexbox, grid, animations, gradients, transforms)
- Use `font-family: 'Cinzel'` for headings and `'Crimson Text'` for body text
- Include magical animations and transitions where appropriate
- Follow mobile-first responsive design principles
- Maintain consistent spacing and visual hierarchy

### JavaScript
- Use jQuery for DOM manipulation (already included via `j/jquery.js`)
- Keep JavaScript unobtrusive and enhancement-focused
- Add magical effects (sparkles, animations, rainbows) where they enhance UX
- Ensure all interactive features are accessible
- Use ES5 syntax for broader compatibility

## Content & Tone

### Writing Style
- **Whimsical and engaging**: Use unicorn metaphors and magical storytelling
- **Educational**: Preserve accurate technical information about HTML5
- **Memorable**: Make concepts stick through creative narratives
- **Accessible**: Explain complex topics in friendly, approachable language
- **Emoji usage**: Sprinkle unicorns 🦄, sparkles ✨, rainbows 🌈, and stars 🌟 throughout

### Content Guidelines
- Frame HTML5 features as "magical spells" or "unicorn powers"
- Use fairy tale or fantasy narrative structures when introducing topics
- Include practical, working code examples
- Maintain attribution to original "Dive Into HTML5" by Mark Pilgrim
- Balance whimsy with technical accuracy

## Visual Design Principles

### Color Palette
- Purple (#9b59b6) - primary unicorn color
- Pink (#ff69b4) - magic and sparkles
- Blue (#87ceeb) - sky and dreams  
- Gold (#ffd700) - highlights and treasure
- Lavender (#e6e6fa) - soft backgrounds
- Use gradients liberally for magical effects

### Interactive Elements
- Add hover effects with rainbow colors or scale transforms
- Include floating unicorn animations
- Create sparkle effects for emphasis
- Use gradient backgrounds on buttons and important elements
- Ensure animations respect `prefers-reduced-motion`

## File Organization
- Main content pages: `*.html` in root directory
- Stylesheets: `unicorn-style.css` (main), `screen.css` (supplementary)
- JavaScript: `j/` directory
- Images: `i/` directory
- Each page should be self-contained but link appropriately to others

## Technical Constraints
- No build process - pure HTML/CSS/JS
- No modern frameworks - vanilla JavaScript with jQuery
- Support modern browsers (Chrome, Firefox, Safari, Edge)
- Responsive design for mobile and desktop
- No external dependencies beyond Google Fonts and jQuery

## Best Practices
- Keep pages lightweight and fast-loading
- Validate HTML5 semantics
- Ensure accessibility (keyboard navigation, screen readers)
- Test on multiple devices and browsers
- Maintain consistent magical theme across all pages
- Include appropriate meta tags for viewport and character encoding

## Attribution & Licensing
- Always credit Mark Pilgrim as the original author
- Reference "Dive Into HTML5" (https://diveintohtml5.info)
- Note Creative Commons Attribution 3.0 license
- Clearly identify unicorn theme as transformative addition

## When Suggesting Code
- Provide complete, working examples
- Include both HTML structure and CSS styling when relevant
- Add inline comments explaining magical concepts
- Show mobile-responsive patterns
- Demonstrate accessibility features
- Include unicorn-themed variable names and comments where fun but not confusing

## Special Considerations
- This is an educational resource - accuracy is paramount
- Whimsy should enhance, not obscure, learning
- Code examples should be copy-paste ready
- Animations should be tasteful and not distracting
- Maintain the delicate balance between fun and functional
