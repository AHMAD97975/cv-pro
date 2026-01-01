# GitHub Copilot Instructions for CV-Pro

## Project Overview

This is a professional, bilingual CV website for Moein Najem, an organizational excellence and service improvement expert. The project showcases 12+ years of professional experience with leading government entities in the UAE and Saudi Arabia.

### Key Features
- **Bilingual Support**: Full Arabic (RTL) and English (LTR) support with language toggle
- **Responsive Design**: Mobile-first approach, works seamlessly across all devices
- **Professional CV/Resume**: Comprehensive sections including experience, education, certifications, skills, and awards
- **Print-Friendly**: Optimized for PDF generation and printing
- **Interactive UI**: Smooth animations, scroll effects, and interactive elements

## Technology Stack

- **HTML5**: Semantic markup, accessibility-focused structure
- **CSS3**: Modern styling with custom properties, flexbox, grid, and animations
- **Vanilla JavaScript**: No frameworks - pure JavaScript for all functionality
- **Font Awesome 6.5.1**: Icons throughout the interface
- **Google Fonts**: Tajawal font family for Arabic text

## File Structure

```
cv-pro/
├── index.html          # Main HTML file (933 lines)
├── styles.css          # All styles (1500+ lines)
├── script.js           # JavaScript functionality (930+ lines)
├── moein.jpg           # Profile image
└── README.md           # Project documentation
```

## Coding Standards

### General Principles

1. **Keep It Simple**: This is a static website - avoid adding unnecessary complexity
2. **Maintain Existing Structure**: Respect the current file organization (single HTML, CSS, JS files)
3. **Preserve Functionality**: Don't break existing features like language toggle, smooth scroll, animations
4. **Minimal Dependencies**: Keep the project framework-free and dependency-light

### HTML Guidelines

- Use semantic HTML5 elements (`<section>`, `<article>`, `<header>`, `<footer>`, etc.)
- Maintain proper heading hierarchy (h1 → h2 → h3)
- Include both `data-ar` and `data-en` attributes for all translatable text elements
- Use descriptive IDs for sections to support anchor navigation
- Ensure proper RTL support with `dir` attribute
- Keep HTML structure clean and well-indented (2 spaces)

### CSS Guidelines

- Use CSS custom properties (`:root` variables) for theming and colors
- Follow mobile-first responsive design approach
- Use meaningful class names that describe purpose (e.g., `.profile-card`, `.skill-category-card`)
- Group related styles together with clear comments
- Maintain consistent spacing and indentation (2 spaces)
- Use flexbox and grid for layouts
- Include print-specific styles in `@media print` queries
- Ensure smooth transitions and animations (use `ease` or `ease-in-out`)

**Color Scheme Variables:**
```css
:root {
    --primary-color: #1e3a8a;      /* Dark blue */
    --secondary-color: #3b82f6;    /* Light blue */
    --accent-color: #f59e0b;       /* Amber/gold */
}
```

### JavaScript Guidelines

- Use vanilla JavaScript - no jQuery or frameworks
- Implement event delegation for better performance
- Store language preference in `localStorage`
- Use `const` for constants, `let` for variables that change
- Add descriptive comments for complex functionality
- Maintain consistent naming conventions (camelCase for functions and variables)
- Handle edge cases and add proper error handling
- Use modern ES6+ features (arrow functions, destructuring, template literals)

**Key Functions:**
- `toggleLanguage()`: Switches between Arabic and English
- `downloadCV()`: Triggers print/PDF download
- `toggleMobileMenu()`: Controls mobile navigation
- `handleScroll()`: Manages navbar visibility on scroll

### Bilingual Support

#### Language Toggle Implementation
- All translatable content must have `data-ar` and `data-en` attributes
- Current language state stored in `currentLang` variable
- Language preference persisted in `localStorage`
- Direction (`dir`) and language (`lang`) attributes updated on `<html>` element

#### Translation Guidelines
- Keep translations concise and professional
- Maintain consistent terminology across all sections
- Ensure both languages fit within the same design space
- Test text overflow in both languages

#### RTL/LTR Considerations
- Use logical properties where possible (`margin-inline-start` vs `margin-left`)
- Icons and visual elements should adapt to reading direction
- Ensure proper text alignment in both directions

### Responsive Design

#### Breakpoints
```css
/* Mobile: Default (up to 768px) */
/* Tablet: 768px - 1024px */
/* Desktop: 1024px+ */
```

#### Guidelines
- Design mobile-first, enhance for larger screens
- Test all interactive elements on touch devices
- Ensure readable font sizes across devices (minimum 16px for body text)
- Maintain proper spacing and padding on small screens
- Hide/show elements appropriately (e.g., hamburger menu on mobile)

### Accessibility

- Include proper ARIA labels where needed
- Ensure sufficient color contrast (WCAG AA minimum)
- Make all interactive elements keyboard-accessible
- Provide alternative text for images
- Ensure focus states are visible
- Test with screen readers when adding new features

### Performance

- Minimize DOM manipulation
- Use CSS transforms for animations (better performance)
- Implement throttling/debouncing for scroll events
- Lazy load images if adding new ones
- Keep file sizes reasonable (no large libraries)

### Print Optimization

The CV is designed to be printed/saved as PDF:
- Hide navigation, buttons, and interactive elements in print view
- Ensure proper page breaks
- Use appropriate print-specific styles
- Maintain professional appearance in monochrome

## Development Workflow

### Making Changes

1. **Test in Both Languages**: Always verify changes work correctly in Arabic and English
2. **Test Responsive Behavior**: Check mobile, tablet, and desktop views
3. **Test Print View**: Ensure changes don't break PDF generation (Ctrl/Cmd + P)
4. **Verify Animations**: Check that transitions and animations remain smooth
5. **Check Console**: Ensure no JavaScript errors

### Adding New Content

When adding new sections or features:

1. Add HTML structure with proper semantic elements
2. Include `data-ar` and `data-en` attributes for all text
3. Add corresponding CSS with consistent class naming
4. Update JavaScript if interactivity is needed
5. Add to navigation menu if it's a major section
6. Test thoroughly in both languages
7. Ensure responsive behavior

### Modifying Existing Features

- Preserve backward compatibility
- Don't remove existing functionality without good reason
- Maintain consistent design patterns
- Update comments if logic changes
- Test edge cases

## Common Patterns

### Creating a Card Component

```html
<div class="card-name">
    <h3 data-ar="العنوان بالعربية" data-en="Title in English">العنوان بالعربية</h3>
    <p data-ar="النص بالعربية" data-en="Text in English">النص بالعربية</p>
</div>
```

```css
.card-name {
    background: white;
    border-radius: 12px;
    padding: 2rem;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
}

.card-name:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.15);
}
```

### Adding Scroll Animations

```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
        }
    });
}, { threshold: 0.1 });

document.querySelectorAll('.animate-element').forEach(el => {
    observer.observe(el);
});
```

## Testing Checklist

Before considering any change complete:

- [ ] Tested in both Arabic and English modes
- [ ] Verified on mobile (< 768px width)
- [ ] Verified on tablet (768px - 1024px width)  
- [ ] Verified on desktop (> 1024px width)
- [ ] Tested print preview (Ctrl/Cmd + P)
- [ ] Checked for console errors
- [ ] Verified smooth animations
- [ ] Tested all interactive elements (buttons, links, menu)
- [ ] Confirmed proper RTL/LTR behavior
- [ ] Validated HTML (if structural changes made)

## Security Considerations

- Don't include sensitive personal information in the code
- Sanitize any user input if forms are added
- Use HTTPS for external resources (CDN links)
- Avoid inline event handlers in HTML (use JavaScript event listeners)

## Browser Support

Target modern browsers:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Mobile)

## Common Issues and Solutions

### Language Toggle Not Working
- Check if `localStorage` is available
- Verify `data-ar` and `data-en` attributes are present
- Ensure `toggleLanguage()` function is properly defined

### Mobile Menu Not Closing
- Verify event listeners are attached
- Check if mobile menu backdrop is created
- Ensure proper class toggling logic

### Print Layout Issues
- Check `@media print` styles in CSS
- Verify elements marked with `@media print { display: none; }`
- Test with actual browser print dialog

### Scroll Animations Not Triggering
- Verify IntersectionObserver is supported
- Check threshold values
- Ensure elements have initial styles set

## Contact Information

For questions or issues related to this project:
- Repository: AHMAD97975/cv-pro
- Project Type: Professional CV/Resume Website
- Primary Language: Arabic with English translation

## Notes for AI Assistants

When helping with this project:

1. **Respect the Single-Page Architecture**: Don't suggest breaking into multiple files unnecessarily
2. **Maintain Bilingual Integrity**: Always update both Arabic and English versions
3. **Keep It Professional**: This is a professional CV - maintain formal tone and clean design
4. **Test Suggestions**: Always provide instructions for testing changes in both languages
5. **Preserve User Experience**: Don't break existing animations, transitions, or interactions
6. **Consider Print Output**: Changes should work well in both web and print formats
7. **Stay Framework-Free**: Don't suggest adding React, Vue, or other frameworks
8. **Mobile-First**: Prioritize mobile experience in suggestions

---

*Last Updated: 2025-01-01*
*Version: 1.0*
