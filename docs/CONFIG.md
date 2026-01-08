# Configuration & Customization Guide

## 🎯 Quick Start

### 1. Installation
```bash
# Clone or download the project
cd your-project/scss

# Install Sass compiler (if not already installed)
npm install -g sass
# or
npm install --save-dev sass
```

### 2. Compile SCSS
```bash
# One-time compilation
sass scss/main.scss css/main.css

# Watch mode (auto-recompile on changes)
sass --watch scss:css

# Production (minified)
sass --style=compressed scss/main.scss css/main.min.css
```

### 3. Include in HTML
```html
<link rel="stylesheet" href="css/main.css">
```

---

## 🎨 Customization Guide

### Modifying Colors

Edit `scss/abstracts/_variables.scss`:

```scss
$colors: (
  primary: #your-color,      // Change primary color
  secondary: #your-color,    // Change secondary color
  accent: #your-color,       // Change accent color
  // ... modify other colors
);
```

**Generated Classes:**
- `.text-{color-name}`
- `.bg-{color-name}`
- `.border-{color-name}`

### Modifying Spacing Scale

Edit `scss/abstracts/_variables.scss`:

```scss
$spacings: (
  0: 0,
  1: 0.25rem,  // 4px - Modify the value
  2: 0.5rem,   // 8px
  3: 0.75rem,  // 12px
  4: 1rem,     // 16px - Base unit
  // Add custom spacings
  18: 4.5rem,
  20: 5rem,
  22: 5.5rem,
);
```

**Affects:** `.m-*`, `.p-*`, `.gap-*`, `.mx-*`, `.py-*`, etc.

### Modifying Font Sizes

Edit `scss/abstracts/_variables.scss`:

```scss
$font-sizes: (
  xs: 0.75rem,   // Modify values
  sm: 0.875rem,
  base: 1rem,    // Base size = 16px
  lg: 1.125rem,
  xl: 1.25rem,
  2xl: 1.5rem,
  3xl: 1.875rem,
  4xl: 2.25rem,
  5xl: 3rem,
  // Add custom sizes
  6xl: 3.75rem,
);
```

### Modifying Breakpoints

Edit `scss/abstracts/_breakpoints.scss`:

```scss
$breakpoints: (
  mobile: 0,        // Min width for mobile
  desktop: 1200px,  // Min width for desktop
);

@mixin respond($target) {
  @if $target == mobile {
    @media (max-width: 1199px) { @content; }
  } @else if $target == desktop {
    @media (min-width: 1200px) { @content; }
  }
}
```

**Note:** To add more breakpoints, add them to the map and create corresponding `@else if` conditions.

### Modifying Border Radius

Edit `scss/abstracts/_variables.scss`:

```scss
$border-radii: (
  none: 0,
  xs: 0.125rem,
  sm: 0.25rem,
  base: 0.375rem,  // Default
  md: 0.5rem,
  lg: 0.75rem,
  xl: 1rem,
  2xl: 1.5rem,
  3xl: 2rem,
  full: 9999px,    // Circle/pill shape
);
```

### Modifying Font Weights

Edit `scss/abstracts/_variables.scss`:

```scss
$font-weights: (
  thin: 100,
  extralight: 200,
  light: 300,
  normal: 400,      // Default
  medium: 500,
  semibold: 600,
  bold: 700,
  extrabold: 800,
  black: 900,
);
```

### Modifying Shadows

Edit `scss/abstracts/_variables.scss`:

```scss
$shadows: (
  none: none,
  xs: 0 1px 2px 0 rgba(0, 0, 0, 0.05),
  sm: 0 1px 3px 0 rgba(0, 0, 0, 0.1),
  base: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
  md: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
  lg: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
  xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25),
);
```

---

## 🔧 Advanced Customization

### Creating New Utility Classes

1. Create a new file in `scss/utilities/`:

```scss
// scss/utilities/_opacity.scss
@use '../abstracts/mixins' as *;
@use '../abstracts/variables' as *;

// Generate opacity utilities
@include responsive('opacity', 'opacity', $opacities);
```

2. Import in `main.scss`:

```scss
@use 'utilities/opacity';
```

### Creating Custom Components

1. Create a new file in `scss/components/`:

```scss
// scss/components/_modal.scss
@use '../abstracts/variables' as *;

.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: map-get($z-indexes, modal);
}

.modal-content {
  background-color: map-get($colors, white);
  border-radius: map-get($border-radii, lg);
  padding: map-get($spacings, 6);
  box-shadow: map-get($shadows, lg);
}
```

2. Import in `main.scss`:

```scss
@use 'components/modal';
```

### Extending Components

Use SCSS `@extend` with placeholders:

```scss
.btn-custom {
  @extend %smooth-transition;
  @extend %focus-ring;
  // Add custom styles
}
```

### Creating Custom Functions

Add to `scss/abstracts/_functions.scss`:

```scss
@function spacing($size) {
  @return map-get($spacings, $size);
}

@function color($name) {
  @return map-get($colors, $name);
}

// Usage:
.element {
  margin: spacing(4);
  color: color(primary);
}
```

### Creating Custom Mixins

Add to `scss/abstracts/_mixins.scss`:

```scss
@mixin hover-lift {
  transition: all 0.3s ease;
  
  &:hover {
    transform: translateY(-4px);
    box-shadow: map-get($shadows, lg);
  }
}

// Usage:
.card {
  @include hover-lift;
}
```

---

## 📋 File Organization Best Practices

### When to Create New Files

✅ **Create new utility file if:**
- It handles multiple related properties
- It generates 5+ classes
- Example: `_flex.scss` for all flexbox utilities

✅ **Create new component file if:**
- It's a styled component (button, card, form, etc.)
- It has multiple variants or modifiers
- Example: `_buttons.scss` for button variations

❌ **Don't create new file if:**
- It's just 1-2 classes
- It's a one-off style
- Add to existing relevant file instead

---

## 🚀 Performance Optimization

### Production Build

```bash
# Minified output
sass --style=compressed scss/main.scss css/main.min.css

# Source map (for debugging)
sass --source-map scss/main.scss css/main.css
```

### File Size Tips

1. **Remove unused utilities** - Delete unused files from `utilities/`
2. **Limit color palette** - Fewer colors = smaller CSS
3. **Use gzip compression** - Server-side compression
4. **Lazy load CSS** - Load non-critical styles later

### Typical File Sizes

- **Uncompressed:** ~150-200 KB
- **Compressed (gzip):** ~15-25 KB
- **With purging unused:** ~30-50 KB

---

## 🔍 Debugging Tips

### Enable Source Maps

```bash
sass --source-map scss/main.scss css/main.css
```

Then in DevTools, you'll see the original SCSS file names and line numbers.

### Check Compiled CSS

View `css/main.css` to see generated classes:

```bash
# View first 100 lines
head -100 css/main.css

# Search for specific class
grep "\.mobile" css/main.css
```

### Common Issues

**Issue:** Classes not generating
- **Solution:** Check `main.scss` imports order
- **Check:** Verify file exists and syntax is correct

**Issue:** Responsive variants not working
- **Solution:** Check breakpoint values in `_breakpoints.scss`
- **Check:** Media query syntax is correct

**Issue:** Colors not applying
- **Solution:** Check color names match in `_variables.scss`
- **Check:** No typos in color map keys

---

## 📚 Variable Reference

### Available Maps

| Variable | Keys | Usage |
|----------|------|-------|
| `$colors` | color names | Colors throughout CSS |
| `$spacings` | 0-32 | Margins, padding, gaps |
| `$font-sizes` | xs-5xl | Text sizing |
| `$font-weights` | thin-black | Font weight |
| `$border-radii` | none-full | Border radius |
| `$shadows` | none-xl | Box shadows |
| `$z-indexes` | 0-1070 | Z-index values |
| `$line-heights` | none-loose | Line height |

### Accessing Variables

```scss
// In your SCSS files
color: map-get($colors, primary);
padding: map-get($spacings, 4);
font-size: map-get($font-sizes, lg);
```

---

## 🎯 Project Structure Template

For a complete project setup:

```
project/
├── scss/
│   ├── abstracts/
│   ├── base/
│   ├── utilities/
│   ├── components/
│   ├── main.scss
│   └── README.md
├── css/
│   ├── main.css          # Compiled output
│   └── main.min.css      # Minified output
├── js/
│   └── app.js
├── index.html
└── package.json
```

---

## 📦 NPM Scripts (Optional)

Add to `package.json`:

```json
{
  "scripts": {
    "sass": "sass scss/main.scss css/main.css",
    "sass:watch": "sass --watch scss:css",
    "sass:prod": "sass --style=compressed scss/main.scss css/main.min.css",
    "build": "npm run sass:prod",
    "dev": "npm run sass:watch"
  },
  "devDependencies": {
    "sass": "^1.69.0"
  }
}
```

Then run:
```bash
npm run dev      # Watch mode
npm run build    # Production build
```

---

## ✅ Checklist Before Deploying

- [ ] Compiled SCSS to CSS
- [ ] Minified CSS for production
- [ ] Added CSS link to HTML
- [ ] Tested in all target browsers
- [ ] Checked responsive breakpoints
- [ ] Verified all colors load correctly
- [ ] Tested form interactions
- [ ] Tested button states
- [ ] Performance checked (file size)
- [ ] Accessibility verified

---

## 🆘 Support & Resources

### Common Patterns

**Centered flex container:**
```html
<div class="flex justify-center items-center h-screen">
  Content
</div>
```

**Responsive grid:**
```html
<div class="grid mobile:grid-cols-1 desktop:grid-cols-3 gap-4">
  Items
</div>
```

**Card with image:**
```html
<div class="card">
  <img src="image.jpg" class="card-image-top">
  <div class="card-body">Content</div>
</div>
```

**Responsive text:**
```html
<h1 class="text-2xl mobile:text-lg desktop:text-4xl">
  Heading
</h1>
```

---

Last Updated: 2024