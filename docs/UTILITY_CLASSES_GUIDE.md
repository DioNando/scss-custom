# Complete Utility Classes Reference Guide

A comprehensive guide to all available utility classes in the SCSS Framework with real-world examples and use cases.

## Table of Contents

1. [Spacing](#spacing)
2. [Display & Layout](#display--layout)
3. [Flexbox](#flexbox)
4. [Grid](#grid)
5. [Typography](#typography)
6. [Colors](#colors)
7. [Borders](#borders)
8. [Sizing](#sizing)
9. [Position](#position)
10. [Opacity](#opacity)
11. [Overflow](#overflow)
12. [Background](#background)
13. [Cursor](#cursor)
14. [Z-Index](#z-index)
15. [Common Patterns](#common-patterns)

---

## Spacing

### Margin Classes

Margin utilities apply spacing outside elements.

**Syntax**: `.m{direction}-{value}`

- `.m-{0-16}` - All sides margin
- `.mx-{0-16}` - Horizontal margin (left & right)
- `.my-{0-16}` - Vertical margin (top & bottom)
- `.mt-{0-16}` - Margin top
- `.mr-{0-16}` - Margin right
- `.mb-{0-16}` - Margin bottom
- `.ml-{0-16}` - Margin left

**Values**: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 16
**Equivalents**: 0, 0.25rem, 0.5rem, 0.75rem, 1rem, 1.5rem, 2rem, 2.5rem, 3rem, 3.5rem, 4rem, 4.5rem, 5rem

```html
<!-- Basic margin -->
<div class="m-4">Margin 1rem on all sides</div>

<!-- Directional margins -->
<div class="mt-2 mr-4 mb-6 ml-8">Different margins per side</div>

<!-- Horizontal/Vertical shortcuts -->
<div class="mx-auto">Center horizontally</div>
<div class="my-4">Margin top & bottom 1rem</div>

<!-- Responsive margins -->
<div class="m-2 mobile:m-4 desktop:m-6">
  Different margin on different breakpoints
</div>
```

### Padding Classes

Padding utilities apply spacing inside elements.

**Syntax**: `.p{direction}-{value}`

- `.p-{0-16}` - All sides padding
- `.px-{0-16}` - Horizontal padding (left & right)
- `.py-{0-16}` - Vertical padding (top & bottom)
- `.pt-{0-16}` - Padding top
- `.pr-{0-16}` - Padding right
- `.pb-{0-16}` - Padding bottom
- `.pl-{0-16}` - Padding left

```html
<!-- Basic padding -->
<div class="p-4">Padding 1rem on all sides</div>

<!-- Directional padding -->
<div class="pt-2 pr-4 pb-6 pl-8">Different padding per side</div>

<!-- Padding shortcuts -->
<div class="px-4">Horizontal padding 1rem</div>
<div class="py-2">Vertical padding 0.5rem</div>

<!-- Responsive padding -->
<button class="p-2 mobile:p-3 desktop:p-4">Responsive Padding</button>
```

### Gap Classes

Gap utilities control spacing between flex and grid items.

**Syntax**: `.gap{direction}-{value}`

- `.gap-{0-16}` - Gap between all items
- `.gap-x-{0-16}` - Horizontal gap (columns)
- `.gap-y-{0-16}` - Vertical gap (rows)

```html
<!-- Flex with gap -->
<div class="flex gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Grid with gap -->
<div class="grid grid-cols-3 gap-6">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Directional gap -->
<div class="grid grid-cols-2 gap-x-4 gap-y-2">
  <div>Horizontal gap 1rem, vertical 0.5rem</div>
</div>
```

---

## Display & Layout

### Display Property

Controls how elements are rendered.

**Available Classes**:
- `.block` - Block display (full width)
- `.inline` - Inline display (width based on content)
- `.inline-block` - Inline-block display
- `.flex` - Flexbox layout
- `.grid` - CSS Grid layout
- `.hidden` - Hidden (display: none)

```html
<!-- Block elements -->
<div class="block">Takes full width</div>

<!-- Inline elements -->
<span class="inline">Width based on content</span>

<!-- Inline-block -->
<span class="inline-block">Block behavior, inline flow</span>

<!-- Responsive display -->
<nav class="hidden mobile:hidden desktop:block">
  Desktop only navigation
</nav>

<button class="mobile:block desktop:hidden">
  Mobile only button
</button>
```

### Flex Direction

Controls the direction of flex items.

**Available Classes**:
- `.flex-row` - Row direction (default, left to right)
- `.flex-col` - Column direction (top to bottom)
- `.flex-row-reverse` - Row reverse direction
- `.flex-col-reverse` - Column reverse direction

```html
<!-- Row layout (default) -->
<div class="flex flex-row gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

<!-- Column layout -->
<div class="flex flex-col gap-4">
  <div>Header</div>
  <div>Content</div>
  <div>Footer</div>
</div>
```

---

## Flexbox

### Justify Content

Aligns items along the main axis.

**Available Classes**:
- `.justify-start` - Align to start
- `.justify-center` - Center items
- `.justify-end` - Align to end
- `.justify-between` - Space between items
- `.justify-around` - Space around items
- `.justify-evenly` - Equal space between items

```html
<!-- Center content -->
<div class="flex justify-center">
  <button>Centered Button</button>
</div>

<!-- Space between -->
<nav class="flex justify-between">
  <div>Logo</div>
  <div>Links</div>
</nav>

<!-- Align to end -->
<div class="flex justify-end gap-2">
  <button>Cancel</button>
  <button>Save</button>
</div>
```

### Align Items

Aligns items along the cross axis.

**Available Classes**:
- `.items-start` - Align to start
- `.items-center` - Center items
- `.items-end` - Align to end
- `.items-stretch` - Stretch items
- `.items-baseline` - Align to baseline

```html
<!-- Center vertically and horizontally -->
<div class="flex justify-center items-center h-64">
  <div>Perfectly Centered</div>
</div>

<!-- Align items to top -->
<div class="flex items-start gap-4">
  <img src="avatar.jpg" alt="User">
  <div>User info</div>
</div>

<!-- Stretch items -->
<div class="flex items-stretch h-48">
  <div class="flex-1">Full Height</div>
  <div class="flex-1">Full Height</div>
</div>
```

### Flex Grow & Shrink

Controls how flex items grow and shrink.

**Available Classes**:
- `.flex-1` - Grow to fill available space (flex: 1)
- `.flex-shrink-0` - Don't shrink below content size
- `.flex-grow-0` - Don't grow
- `.flex-nowrap` - Don't wrap items
- `.flex-wrap` - Wrap items to next line

```html
<!-- Equal width columns -->
<div class="flex gap-4">
  <div class="flex-1">Col 1</div>
  <div class="flex-1">Col 2</div>
  <div class="flex-1">Col 3</div>
</div>

<!-- Flexible sidebar layout -->
<div class="flex gap-4">
  <aside class="w-64 flex-shrink-0">Sidebar</aside>
  <main class="flex-1">Main content</main>
</div>

<!-- Wrapping items -->
<div class="flex flex-wrap gap-4">
  <div class="w-48">Item</div>
  <div class="w-48">Item</div>
  <div class="w-48">Item</div>
</div>
```

---

## Grid

### Grid Columns

Defines the number of columns in a grid.

**Available Classes**:
- `.grid-cols-1` - 1 column
- `.grid-cols-2` - 2 columns
- `.grid-cols-3` - 3 columns
- `.grid-cols-4` - 4 columns
- `.grid-cols-6` - 6 columns
- `.grid-cols-12` - 12 columns

```html
<!-- 3 column grid -->
<div class="grid grid-cols-3 gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Responsive grid -->
<div class="grid mobile:grid-cols-1 desktop:grid-cols-3 gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Auto-fit grid -->
<div class="grid gap-4" style="grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))">
  <div>Auto-fitting items</div>
  <div>Auto-fitting items</div>
  <div>Auto-fitting items</div>
</div>
```

### Column Span

Makes an item span multiple columns.

**Available Classes**:
- `.col-span-{1-12}` - Span across N columns
- `.row-span-{1-6}` - Span across N rows

```html
<!-- Item spanning 2 columns -->
<div class="grid grid-cols-3 gap-4">
  <div>Item 1</div>
  <div class="col-span-2">Spans 2 columns</div>
  <div class="col-span-3">Full width (3 cols)</div>
</div>
```

---

## Typography

### Font Size

Controls text size.

**Available Classes**: `.text-xs`, `.text-sm`, `.text-base`, `.text-lg`, `.text-xl`, `.text-2xl`, `.text-3xl`, `.text-4xl`, `.text-5xl`

**Values**: 0.75rem, 0.875rem, 1rem, 1.125rem, 1.25rem, 1.5rem, 1.875rem, 2.25rem, 3rem

```html
<!-- Font sizes -->
<p class="text-xs">Extra Small (12px)</p>
<p class="text-sm">Small (14px)</p>
<p class="text-base">Base (16px)</p>
<p class="text-lg">Large (18px)</p>
<p class="text-2xl">2XL (24px)</p>
<p class="text-5xl">5XL (48px)</p>

<!-- Responsive sizes -->
<h1 class="text-2xl mobile:text-3xl desktop:text-5xl">
  Responsive Heading
</h1>
```

### Font Weight

Controls text thickness.

**Available Classes**: 
- `.font-thin` - 100
- `.font-light` - 300
- `.font-normal` - 400
- `.font-semibold` - 600
- `.font-bold` - 700
- `.font-extrabold` - 800
- `.font-black` - 900

```html
<!-- Font weights -->
<p class="font-thin">Thin text</p>
<p class="font-normal">Normal text</p>
<p class="font-bold">Bold text</p>
<p class="font-black">Black text</p>

<!-- Combined with size -->
<h1 class="text-4xl font-bold">Bold Heading</h1>
```

### Line Height

Controls vertical spacing between lines.

**Available Classes**: `.leading-none`, `.leading-tight`, `.leading-snug`, `.leading-normal`, `.leading-relaxed`, `.leading-loose`

```html
<!-- Tight leading for headlines -->
<h2 class="leading-tight">
  Multiple line heading with tight spacing
</h2>

<!-- Relaxed leading for paragraphs -->
<p class="leading-relaxed">
  Long paragraph with more comfortable reading
  experience through increased line height
</p>
```

### Text Transform

Changes text appearance.

**Available Classes**:
- `.uppercase` - UPPERCASE
- `.lowercase` - lowercase
- `.capitalize` - Capitalize Each Word

```html
<span class="uppercase">small caps</span>
<span class="lowercase">LOWERCASE THIS</span>
<span class="capitalize">capitalize this</span>
```

### Text Alignment

Aligns text content.

**Available Classes**: `.text-left`, `.text-center`, `.text-right`, `.text-justify`

```html
<p class="text-left">Left aligned</p>
<p class="text-center">Centered</p>
<p class="text-right">Right aligned</p>
<p class="text-justify">Justified text spreads evenly</p>
```

### Text Overflow

Handles text that's too long for its container.

**Available Classes**:
- `.truncate` - Single line truncate with ellipsis
- `.line-clamp-2` - Truncate to 2 lines
- `.line-clamp-3` - Truncate to 3 lines

```html
<!-- Single line truncate -->
<p class="truncate">This very long text will be cut off with ellipsis...</p>

<!-- Multi-line clamp -->
<p class="line-clamp-3">
  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
  Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
  Ut enim ad minim veniam, quis nostrud exercitation ullamco.
</p>
```

---

## Colors

### Text Color

Changes text color.

**Available Classes**:
- `.text-primary` - Primary blue
- `.text-secondary` - Secondary gray
- `.text-success` - Success green
- `.text-warning` - Warning amber
- `.text-danger` - Danger red
- `.text-info` - Info cyan
- `.text-gray-{50-900}` - Gray scale

```html
<!-- Semantic colors -->
<p class="text-primary">Primary text</p>
<p class="text-success">Success message</p>
<p class="text-danger">Error message</p>

<!-- Gray scale -->
<p class="text-gray-500">Medium gray</p>
<p class="text-gray-900">Dark gray (almost black)</p>
```

### Background Color

Changes background color.

**Available Classes**:
- `.bg-primary` - Primary background
- `.bg-secondary` - Secondary background
- `.bg-success` - Success background
- `.bg-warning` - Warning background
- `.bg-danger` - Danger background
- `.bg-info` - Info background
- `.bg-gray-{50-900}` - Gray scale
- `.bg-white` - White background
- `.bg-black` - Black background

```html
<!-- Semantic backgrounds -->
<div class="bg-primary text-white p-4">Primary background</div>
<div class="bg-success text-white p-4">Success background</div>
<div class="bg-warning text-white p-4">Warning background</div>

<!-- Gray scale -->
<div class="bg-gray-100 p-4">Light gray background</div>
<div class="bg-gray-900 text-white p-4">Dark background</div>
```

---

## Borders

### Border Width

Controls border thickness.

**Available Classes**:
- `.border` - 1px border
- `.border-2` - 2px border
- `.border-4` - 4px border
- `.border-8` - 8px border
- `.border-0` - No border
- `.border-t`, `.border-r`, `.border-b`, `.border-l` - Sides
- `.border-t-2`, `.border-r-2`, etc. - Side width

```html
<!-- Full borders -->
<div class="border">1px border</div>
<div class="border-2">2px border</div>

<!-- Single side -->
<div class="border-b border-b-2">Bottom border only</div>
<div class="border-l-4">Left border 4px</div>

<!-- No border -->
<div class="border-0">No border</div>
```

### Border Style

Controls how borders are drawn.

**Available Classes**: `.border-solid`, `.border-dashed`, `.border-dotted`, `.border-double`, `.border-none`

```html
<div class="border border-solid">Solid border</div>
<div class="border border-dashed">Dashed border</div>
<div class="border border-dotted">Dotted border</div>
<div class="border border-double">Double border</div>
```

### Border Color

Changes border color.

**Available Classes**:
- `.border-primary` - Primary border
- `.border-success` - Success border
- `.border-gray-300` - Gray border
- etc. (all color variations)

```html
<div class="border-2 border-primary">Primary border</div>
<div class="border-2 border-success">Success border</div>
<div class="border-2 border-gray-300">Gray border</div>
```

### Border Radius

Rounds corners.

**Available Classes**: `.rounded-none`, `.rounded-sm`, `.rounded`, `.rounded-md`, `.rounded-lg`, `.rounded-xl`, `.rounded-2xl`, `.rounded-3xl`, `.rounded-full`

**Values**: 0, 0.125rem, 0.25rem, 0.375rem, 0.5rem, 0.75rem, 1rem, 1.5rem, 2rem, 50%

```html
<!-- Corner radius -->
<div class="rounded-none">No radius</div>
<div class="rounded-md">Medium radius</div>
<div class="rounded-full">Pill shape (circle)</div>

<!-- Per corner -->
<div class="rounded-t-lg">Top corners only</div>
<div class="rounded-br-lg">Bottom right only</div>
```

---

## Sizing

### Width

Controls element width.

**Available Classes**:
- `.w-full` - 100% width
- `.w-1/2` - 50% width
- `.w-1/3` - 33% width
- `.w-1/4` - 25% width
- `.w-3/4` - 75% width
- `.max-w-{value}` - Maximum width
- `.min-w-{value}` - Minimum width

```html
<!-- Full width -->
<div class="w-full">100% width</div>

<!-- Fractional width -->
<div class="flex gap-4">
  <div class="w-1/4">25%</div>
  <div class="w-1/4">25%</div>
  <div class="w-1/2">50%</div>
</div>

<!-- Max width container -->
<div class="max-w-6xl mx-auto">
  Container with max 1280px width, centered
</div>
```

### Height

Controls element height.

**Available Classes**:
- `.h-full` - 100% height
- `.h-screen` - Viewport height
- `.h-auto` - Auto height
- `.max-h-{value}` - Maximum height
- `.min-h-{value}` - Minimum height

```html
<!-- Full height -->
<div class="h-full">100% height</div>

<!-- Screen height -->
<div class="h-screen">Full viewport height</div>

<!-- Min height fullscreen -->
<main class="min-h-screen">
  At least viewport height
</main>
```

---

## Position

### Position Type

Controls how elements are positioned.

**Available Classes**:
- `.static` - Static positioning (default)
- `.relative` - Relative positioning
- `.absolute` - Absolute positioning
- `.fixed` - Fixed positioning
- `.sticky` - Sticky positioning

```html
<!-- Relative positioning container -->
<div class="relative">
  <div class="absolute top-0 right-0">Top right</div>
  <div class="absolute bottom-0 left-0">Bottom left</div>
</div>

<!-- Fixed navbar -->
<nav class="fixed top-0 left-0 right-0">
  Navigation stays at top
</nav>

<!-- Sticky header -->
<div class="sticky top-0">
  Sticks to top while scrolling
</div>
```

### Position Offsets

Controls position values.

**Available Classes**: `.top-{value}`, `.right-{value}`, `.bottom-{value}`, `.left-{value}`

```html
<div class="absolute top-4 right-4">
  Top right offset
</div>

<div class="absolute bottom-0 left-0 right-0">
  Full width at bottom
</div>
```

---

## Opacity

Controls element transparency.

**Available Classes**: `.opacity-0`, `.opacity-25`, `.opacity-50`, `.opacity-75`, `.opacity-100`

```html
<!-- Semi-transparent -->
<div class="opacity-50 bg-primary">
  50% transparent
</div>

<!-- Invisible but takes space -->
<div class="opacity-0">
  Invisible element
</div>

<!-- Fully opaque -->
<div class="opacity-100">
  Fully visible
</div>

<!-- Hover effect -->
<button class="opacity-100 hover:opacity-75">
  Fades on hover
</button>
```

---

## Overflow

Controls content overflow behavior.

**Available Classes**:
- `.overflow-visible` - Content overflows (default)
- `.overflow-hidden` - Content is clipped
- `.overflow-auto` - Scrollbar if needed
- `.overflow-scroll` - Always show scrollbar
- `.overflow-x-auto` - Horizontal scroll only
- `.overflow-y-auto` - Vertical scroll only

```html
<!-- Hidden overflow -->
<div class="overflow-hidden">
  Content that exceeds will be hidden
</div>

<!-- Auto scrolling -->
<div class="overflow-auto h-64">
  Long content gets scrollbar
</div>

<!-- Horizontal scroll -->
<div class="overflow-x-auto">
  <table style="min-width: 800px">
    Wide table scrolls horizontally
  </table>
</div>
```

---

## Background

### Background Attachment

Controls how background images scroll.

**Available Classes**:
- `.bg-scroll` - Background scrolls with content
- `.bg-fixed` - Background fixed while scrolling
- `.bg-local` - Background scrolls with element

```html
<div class="bg-fixed" style="background-image: url(...)">
  Background stays fixed while scrolling
</div>
```

### Background Position

Controls where background image is positioned.

**Available Classes**: `.bg-top`, `.bg-center`, `.bg-bottom`, `.bg-left`, `.bg-right`, `.bg-left-top`, `.bg-right-bottom`, etc.

### Background Repeat

Controls background image repetition.

**Available Classes**: `.bg-repeat`, `.bg-no-repeat`, `.bg-repeat-x`, `.bg-repeat-y`

### Background Clip

Controls background clipping.

**Available Classes**: `.bg-clip-border`, `.bg-clip-padding`, `.bg-clip-content`, `.bg-clip-text`

```html
<!-- Text gradient effect -->
<h1 class="bg-clip-text" style="background: linear-gradient(45deg, blue, purple); -webkit-text-fill-color: transparent;">
  Gradient Text
</h1>
```

---

## Cursor

Controls cursor appearance on hover.

**Available Classes**:
- `.cursor-auto` - Automatic cursor
- `.cursor-default` - Default arrow
- `.cursor-pointer` - Pointer hand
- `.cursor-wait` - Wait spinner
- `.cursor-text` - Text selection cursor
- `.cursor-move` - Move cursor
- `.cursor-not-allowed` - Disabled cursor
- `.cursor-help` - Help cursor
- `.cursor-progress` - Progress cursor

```html
<!-- Interactive elements -->
<button class="cursor-pointer">Click me</button>

<!-- Disabled elements -->
<button class="cursor-not-allowed" disabled>Disabled</button>

<!-- Draggable elements -->
<div class="cursor-move" draggable="true">Drag me</div>
```

---

## Z-Index

Controls element stacking order.

**Available Classes**: `.z-0`, `.z-10`, `.z-20`, `.z-30`, `.z-40`, `.z-50`, `.z-auto`

```html
<!-- Modal backdrop -->
<div class="fixed inset-0 bg-black z-40"></div>

<!-- Modal -->
<div class="fixed inset-0 z-50 flex items-center justify-center">
  Modal content
</div>

<!-- Dropdown menu -->
<div class="relative">
  <button>Menu</button>
  <div class="absolute bg-white z-10">
    <a href="#">Item 1</a>
    <a href="#">Item 2</a>
  </div>
</div>
```

---

## Common Patterns

### Centered Container

```html
<div class="max-w-6xl mx-auto p-4">
  Centered content with max width and padding
</div>
```

### Card Component

```html
<div class="bg-white border rounded-lg shadow-md p-6">
  <h2 class="text-xl font-bold mb-2">Card Title</h2>
  <p class="text-gray-600">Card content</p>
  <button class="btn btn-primary mt-4">Action</button>
</div>
```

### Button Group

```html
<div class="flex gap-2">
  <button class="btn btn-primary flex-1">Save</button>
  <button class="btn btn-secondary flex-1">Cancel</button>
  <button class="btn btn-ghost flex-1">Delete</button>
</div>
```

### Responsive Grid

```html
<div class="grid mobile:grid-cols-1 desktop:grid-cols-3 gap-4">
  <div class="card">Item 1</div>
  <div class="card">Item 2</div>
  <div class="card">Item 3</div>
</div>
```

### Navbar

```html
<nav class="bg-primary text-white p-4 sticky top-0 z-40">
  <div class="flex justify-between items-center max-w-6xl mx-auto">
    <div class="font-bold text-lg">Logo</div>
    <div class="flex gap-4">
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </div>
  </div>
</nav>
```

### Hero Banner

```html
<div class="bg-primary text-white py-16 text-center">
  <div class="max-w-4xl mx-auto px-4">
    <h1 class="text-5xl font-bold mb-4">Welcome</h1>
    <p class="text-xl mb-6">Build beautiful websites</p>
    <button class="btn btn-primary">Get Started</button>
  </div>
</div>
```

### Form Layout

```html
<form class="max-w-md">
  <div class="mb-4">
    <label class="block font-bold mb-2">Email</label>
    <input type="email" class="w-full px-3 py-2 border rounded">
  </div>
  <div class="mb-4">
    <label class="block font-bold mb-2">Message</label>
    <textarea class="w-full px-3 py-2 border rounded"></textarea>
  </div>
  <button class="btn btn-primary w-full">Send</button>
</form>
```

---

## Responsive Design Tips

### Mobile-First Approach

```html
<!-- Start with mobile styles, override on desktop -->
<div class="text-sm mobile:p-2 desktop:p-4 mobile:grid-cols-1 desktop:grid-cols-3">
  Content
</div>
```

### Common Breakpoints

- **Mobile**: max-width 1199px (default)
- **Desktop**: min-width 1200px

### Responsive Text

```html
<!-- Smaller on mobile, larger on desktop -->
<h1 class="text-2xl mobile:text-3xl desktop:text-5xl font-bold">
  Responsive Heading
</h1>
```

### Responsive Layout

```html
<!-- Single column on mobile, multiple columns on desktop -->
<div class="grid mobile:grid-cols-1 desktop:grid-cols-2 gap-4">
  <div class="card">Left</div>
  <div class="card">Right</div>
</div>
```

---

## Performance Tips

1. **Use utility classes directly** - No need for custom CSS
2. **Combine utilities** - Stack multiple classes for complex styles
3. **Keep specificity low** - Utilities maintain low specificity for easy overrides
4. **Responsive by default** - Add breakpoint prefixes as needed
5. **Semantic HTML** - Use proper HTML elements with utility classes

---

## Customization

All spacing, color, and sizing values can be customized in `_variables.scss`.

### Adding New Colors

```scss
$colors: (
  // ... existing colors
  custom: #your-color,
);
```

### Adding New Spacing Values

```scss
$spacings: (
  // ... existing values
  18: 4.5rem,
  20: 5rem,
);
```

### Creating New Utilities

```scss
@include responsive('custom', 'custom-property', $your-values);
```

---

**Happy styling! For more examples, check the example.html file.**