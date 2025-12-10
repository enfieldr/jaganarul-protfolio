# AI Copilot Instructions for Jaganarul Portfolio

## Project Overview
This is a **personal portfolio website** for Jaganarul, a Java Developer specializing in AI integration and core banking systems. The site showcases projects, skills, and experience with a modern dark-mode aesthetic supporting light mode.

### Key Technologies
- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Design System**: CSS variables, Glassmorphism, Gradient animations
- **Theming**: Dark mode (default) + Light mode toggle with localStorage persistence
- **Icons**: Font Awesome 6.5.2
- **Fonts**: Google Inter (variable font)
- **JavaScript Libraries**: GSAP (scroll animations referenced but not fully used)

---

## Architecture & Structure

### Core Layout Pattern
```
index.html
├── Professional Header (sticky, responsive nav)
├── Main Content (sections)
│   ├── #about (name, stats, bio)
│   ├── #skills (tech tags)
│   ├── #projects (cards with images, links)
│   ├── #experience (timeline items)
│   ├── #resume (download link)
│   ├── #contact (form/email)
│   └── #chatbot (floating assistant)
└── Professional Footer (multi-column, social links)
```

### Design System (CSS Variables in `:root`)
**Dark Mode (default)**:
- `--primary-color`: #adf0d4 (mint green, main text)
- `--accent-color`: #13b88a (teal, borders)
- `--accent4`: #d2d81d (yellow, highlights/CTAs)
- `--bg-color`: #080707 (near black)
- `--glass-bg`: rgba(31,216,164,0.12) (glassmorphism overlay)
- `--card-bg`: rgba(24,24,24,0.85) (semi-transparent dark)

**Light Mode** (activated by `.light-mode` class on `<html>`):
- `--primary-color`: #1a1a1a (dark text)
- `--bg-color`: #ffffff
- Inverted accent colors for readability

### Transition & Animation Rules
- **Smooth transitions**: All UI elements use `var(--transition)` = 0.25s cubic-bezier(.4,0,.2,1)
- **Hover effects**: Scale/translateY with shadow changes
- **Animations**: Pulse keyframe on icons, heartbeat on footer heart, gradient shift on body

---

## Development Patterns

### Component-Based CSS Classes
1. **`.professional-header`**: Sticky top nav with brand logo, navigation links, social icons
2. **`.professional-footer`**: Multi-column grid footer with quick links and social media
3. **`.stats-container`**, **`.skills-list`**, **`.projectItem`**: Content section patterns
4. **`.linkItem`**, **`.nav-link`**: Interactive links with underline-on-hover effect

### Interactive Elements
- **Navigation links**: Smooth scroll to anchor IDs (handled in `script.js`)
- **Theme toggle**: Checkbox input saves preference to localStorage
- **Chatbot**: Floating widget with typing effects and suggestion buttons
- **Project images**: Scale + rotate on hover

### Accessibility Considerations
- ARIA labels on icon-only buttons (`aria-label="GitHub"`)
- Color contrast maintained in both dark/light modes
- Semantic HTML (header, footer, main, nav, section tags)
- Focus states on form inputs and buttons

---

## Critical Developer Workflows

### Theme Implementation
1. Light mode activates when `.light-mode` class is added to `<html>` element
2. CSS variables automatically adjust via light-mode selectors
3. User preference persists in `localStorage['theme']`
4. Toggle happens via checkbox in theme-switch component

**Example**:
```javascript
html.classList.toggle('light-mode', isLightMode);
localStorage.setItem('theme', isLightMode ? 'light' : 'dark');
```

### Adding New Project/Experience Cards
1. Follow existing `.projectItem` or `.experience-item` HTML structure
2. Ensure images are placed in root directory (no subdirectories)
3. Update both content AND alt text for images
4. Use `.linkItem` class for GitHub/documentation links
5. Add date in consistent format (e.g., "Jan 24, 2024")

### CSS Updates
- **Never hardcode colors**: Always use CSS variables
- **Animations**: Update `@keyframes` sections, not individual element transitions
- **Responsive breakpoints**: Use existing media queries (768px, 480px)
- **Shadows & borders**: Maintain consistency with `var(--shadow)` and `var(--radius)`

---

## Important Files & Their Roles

| File | Purpose |
|------|---------|
| `index.html` | Full HTML structure with embedded styles for theme toggle |
| `styles.css` | All styling, animations, responsiveness, theming |
| `script.js` | Smooth scroll nav, chatbot logic, GSAP animations (partial) |
| `jaganprofile.png` | Profile photo in about section |
| `Background.jpg` | Hero background image (overlay gradient) |
| Project images | Each project has a .png screenshot |

---

## Common Customization Tasks

### Change Color Scheme
Edit `:root` CSS variables in `styles.css`. Dark mode colors are primary; update light-mode selectors in `.light-mode` block.

### Update Contact Information
- Email button: Update `href="mailto:jaganarul179@gmail.com"`
- Social links: Find and replace URLs in header/footer
- GitHub/LinkedIn: Appears in multiple places (header, footer, contact section)

### Add New Section
1. Create `<section id="new-section">` in HTML after closing `</main>`
2. Add nav link: `<a href="#new-section">Label</a>` in `.professional-nav`
3. Add footer quick link if relevant
4. Apply consistent styling (use section styles from existing sections)

### Update Resume Link
Search for `#resume` section and update the `.linkItem` href to new resume file.

---

## Performance & Best Practices

### Image Optimization
- Project screenshots should be optimized (aim for <200KB each)
- Profile image: Use circular crop (handled by `.imgContainer`)
- Background image: Keep under 500KB for fast loading

### JavaScript Efficiency
- Event listeners use `.forEach()` for nav links (efficient batch attach)
- Chatbot uses simple string matching, not regex (performance optimal for 5-10 responses)
- Smooth scroll fallback to browser's native scroll behavior if JS fails

### Responsive Design
- **Header/Footer**: Full-width containers with centered inner max-width (1200px)
- **Stack on mobile**: Flex columns, grid single-column layouts below 768px
- **Font sizes**: Use relative units (em), not px (e.g., 0.95em for smaller text)

---

## Troubleshooting Guide

| Issue | Solution |
|-------|----------|
| Theme not persisting | Check `localStorage` in DevTools; verify checkbox saves value |
| Images not loading | Ensure filename matches case-sensitively; verify relative paths |
| Layout broken on mobile | Check `@media (max-width: 768px)` breakpoint CSS |
| Colors look wrong in light mode | Update light-mode selectors in CSS; test contrast ratios |
| Animations stuttering | Reduce simultaneous animations; check GPU acceleration |

---

## Git Commit Patterns
- Feature additions: "feat: add [component] section"
- Bug fixes: "fix: correct [issue] in [file]"
- Styling: "style: update [color/spacing/animation]"
- Documentation: "docs: update copilot-instructions"

---

## Next Steps for Enhancement
- [ ] Implement form submission for contact section (currently email-only)
- [ ] Add filtering to projects by technology stack
- [ ] Optimize GSAP scroll animations (partially referenced)
- [ ] Add dark/light mode toggle to header (currently theme switch only)
- [ ] Implement project search/filter functionality
