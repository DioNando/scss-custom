# SCSS Architecture - Modular & Maintainable Framework

Une structure SCSS complète, modulaire et hautement personnalisable construite selon les principes ITCSS (Inverted Triangle CSS). Ce framework offre un système de classes utilitaires de style Tailwind avec deux points de rupture responsifs simples.

## 🏗️ Architecture & Structure

```
scss/
├── abstracts/              # Configuration et outils
│   ├── _variables.scss     # Maps de couleurs, espacements, typographie
│   ├── _functions.scss     # Fonctions SCSS réutilisables
│   ├── _mixins.scss        # Mixins pour générer les classes utilitaires
│   ├── _placeholders.scss  # Placeholders (@extend)
│   └── _breakpoints.scss   # Points de rupture et media queries
├── base/                   # Styles de base
│   ├── _reset.scss         # Normalisation et reset CSS
│   ├── _base.scss          # Styles globaux et conteneurs
│   └── _typography.scss    # Typographie et styles de texte
├── utilities/              # Classes utilitaires
│   ├── _spacing.scss       # Marges et rembourrages (m, p, mx, py, etc.)
│   ├── _colors.scss        # Couleurs (text, bg, border)
│   ├── _display.scss       # Propriété display
│   ├── _flex.scss          # Utilitaires Flexbox
│   ├── _grid.scss          # Utilitaires CSS Grid
│   ├── _text.scss          # Typographie et alignement (text-size, font-weight, etc.)
│   ├── _position.scss      # Position et offsets (top, left, right, bottom)
│   ├── _border.scss        # Bordures et border-radius
│   ├── _sizing.scss        # Dimensions (width, height, max-width, min-height)
│   ├── _background.scss    # Propriétés background
│   ├── _zindex.scss        # Stacking context (z-index)
│   ├── _opacity.scss       # Opacité
│   ├── _overflow.scss      # Débordement (overflow, scroll)
│   ├── _cursor.scss        # Styles du curseur
│   └── _visibility.scss    # Visibilité et affichage
├── components/             # Composants stylisés
│   ├── _buttons.scss       # Styles pour boutons
│   ├── _cards.scss         # Styles pour cartes
│   └── _forms.scss         # Styles pour formulaires
└── main.scss               # Fichier d'entrée principal
```

## 📱 Points de Rupture Responsifs

### Deux Breakpoints Simples

```scss
$breakpoints: (
  mobile: 0,      // Petit écrans: max-width 1199px
  desktop: 1200px // Grands écrans: min-width 1200px
);
```

### Utilisation des Media Queries

```scss
@include respond(mobile) {
  // Styles pour mobiles (max-width: 1199px)
}

@include respond(desktop) {
  // Styles pour ordinateurs (min-width: 1200px)
}
```

## 🎯 Variantes Responsives des Utilitaires

Chaque classe utilitaire génère automatiquement des variantes responsives :

```html
<!-- Classe de base -->
<div class="m-4">Marge 1rem</div>

<!-- Variante mobile -->
<div class="mobile:m-2">Marge 0.5rem sur mobile</div>

<!-- Variante desktop -->
<div class="desktop:m-6">Marge 2rem sur desktop</div>

<!-- Exemple complet -->
<div class="p-4 mobile:p-2 desktop:p-8">
  Padding responsive
</div>
```

## 📦 Variables & Tokens

### Couleurs

```scss
$colors: (
  primary: #2563eb,
  secondary: #64748b,
  accent: #f59e0b,
  white: #ffffff,
  black: #000000,
  gray-50 à gray-900: // Échelle de gris
  success: #10b981,
  warning: #f59e0b,
  error: #ef4444,
  info: #06b6d4
);
```

### Espacements

```scss
$spacings: (
  0: 0,
  1: 0.25rem,  // 4px
  2: 0.5rem,   // 8px
  3: 0.75rem,  // 12px
  4: 1rem,     // 16px
  5: 1.5rem,   // 24px
  6: 2rem,     // 32px
  // ... jusqu'à 16: 5rem
);
```

### Typographie

```scss
$font-sizes: (xs, sm, base, lg, xl, 2xl, 3xl, 4xl, 5xl);
$font-weights: (thin, extralight, light, normal, medium, semibold, bold, extrabold, black);
$line-heights: (none, tight, snug, normal, relaxed, loose);
```

### Bordures & Ombres

```scss
$border-radii: (none, xs, sm, base, md, lg, xl, 2xl, 3xl, full);
$shadows: (none, xs, sm, base, md, lg, xl);
$z-indexes: (hide, auto, base, dropdown, sticky, fixed, modal-backdrop, modal, popover, tooltip);
```

## 🔧 Mixins Principaux

### Mixin `responsive()`

Génère des classes utilitaires avec variantes responsives :

```scss
@include responsive('m', 'margin', $spacings);
// Génère: .m-1, .m-2, ..., .mobile:m-1, .mobile:m-2, .desktop:m-1, .desktop:m-2
```

### Utilisation dans les Utilities

```scss
// _spacing.scss
@use '../abstracts/mixins' as *;
@use '../abstracts/variables' as *;

@include responsive('m', 'margin', $spacings);
@include responsive('p', 'padding', $spacings);
```

## 🎨 Classes Utilitaires Disponibles

### Espacement (Margins & Padding)

```html
<!-- Marges -->
<div class="m-4">Marge 1rem</div>
<div class="mx-4">Marges horizontales 1rem</div>
<div class="my-4">Marges verticales 1rem</div>
<div class="mt-2 mr-4 mb-6 ml-8">Marges individuelles</div>

<!-- Rembourrages -->
<div class="p-4">Padding 1rem</div>
<div class="px-4 py-2">Padding horizontal & vertical</div>
<div class="py-6">Padding vertical 1.5rem</div>
<div class="p-8 mobile:p-4 desktop:p-8">Responsive padding</div>

<!-- Gap (Flexbox & Grid) -->
<div class="flex gap-4">Espacé de 1rem</div>
<div class="grid gap-6">Grille avec gap 2rem</div>
<div class="gap-x-4 gap-y-2">Gap horizontal & vertical</div>

<!-- Valeurs disponibles: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 16 -->
<!-- Équivalents: 0, 0.25rem, 0.5rem, 0.75rem, 1rem, 1.5rem, 2rem, 2.5rem, 3rem, 3.5rem, 4rem, 4.5rem, 5rem -->
```

### Display

```html
<div class="block">Block Display</div>
<div class="inline">Inline Display</div>
<div class="inline-block">Inline-Block</div>
<div class="flex">Flexbox Layout</div>
<div class="flex-row">Flexbox Row</div>
<div class="flex-col">Flexbox Column</div>
<div class="grid">Grid Layout</div>
<div class="hidden">Caché (display: none)</div>
<div class="mobile:hidden desktop:block">Caché sur mobile, visible desktop</div>
<div class="mobile:block desktop:hidden">Visible mobile, caché desktop</div>
```

### Flexbox

```html
<!-- Direction -->
<div class="flex flex-row">Flex row (défaut)</div>
<div class="flex flex-col">Flex colonne</div>

<!-- Justification (main axis) -->
<div class="flex justify-start">Aligned start</div>
<div class="flex justify-center">Centered</div>
<div class="flex justify-end">Aligned end</div>
<div class="flex justify-between">Space between</div>
<div class="flex justify-around">Space around</div>

<!-- Alignement (cross axis) -->
<div class="flex items-start">Items aligned start</div>
<div class="flex items-center">Items centered</div>
<div class="flex items-end">Items aligned end</div>
<div class="flex items-stretch">Items stretched</div>

<!-- Flex grow/shrink -->
<div class="flex gap-4">
  <div class="flex-1">Flex grow</div>
  <div class="flex-shrink-0">No shrink</div>
</div>

<!-- Wrap -->
<div class="flex flex-wrap gap-4">Items avec wrap</div>
<div class="flex flex-nowrap gap-4">Items sans wrap</div>
```

### Grid

```html
<!-- Template columns -->
<div class="grid grid-cols-1">Single column</div>
<div class="grid grid-cols-2">2 colonnes</div>
<div class="grid grid-cols-3">3 colonnes</div>
<div class="grid grid-cols-4">4 colonnes</div>

<!-- Template rows -->
<div class="grid grid-rows-2">2 rangées</div>
<div class="grid grid-rows-3">3 rangées</div>

<!-- Col span & Row span -->
<div class="grid grid-cols-3 gap-4">
  <div>Col 1</div>
  <div class="col-span-2">Span 2 colonnes</div>
  <div class="col-span-3">Span 3 colonnes (full width)</div>
</div>

<!-- Responsive -->
<div class="grid mobile:grid-cols-1 desktop:grid-cols-3 gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Auto fit -->
<div class="grid gap-4" style="grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))">
  Items avec auto-fit
</div>
```

### Typographie

```html
<!-- Font Size -->
<p class="text-xs">Extra small 0.75rem</p>
<p class="text-sm">Small 0.875rem</p>
<p class="text-base">Base 1rem</p>
<p class="text-lg">Large 1.125rem</p>
<p class="text-xl">Extra large 1.25rem</p>
<p class="text-2xl">2XL 1.5rem</p>
<p class="text-3xl">3XL 1.875rem</p>
<p class="text-4xl">4XL 2.25rem</p>
<p class="text-5xl">5XL 3rem</p>

<!-- Font Weight -->
<p class="font-thin">Thin 100</p>
<p class="font-light">Light 300</p>
<p class="font-normal">Normal 400</p>
<p class="font-semibold">Semibold 600</p>
<p class="font-bold">Bold 700</p>
<p class="font-black">Black 900</p>

<!-- Line Height -->
<p class="leading-none">None 1</p>
<p class="leading-tight">Tight 1.25</p>
<p class="leading-normal">Normal 1.5</p>
<p class="leading-loose">Loose 2</p>

<!-- Text Transform -->
<span class="uppercase">uppercase text</span>
<span class="lowercase">LOWERCASE TEXT</span>
<span class="capitalize">capitalize text</span>

<!-- Text Alignment -->
<p class="text-left">Aligned left</p>
<p class="text-center">Centered</p>
<p class="text-right">Aligned right</p>
<p class="text-justify">Justified text</p>

<!-- Text Decoration -->
<p class="underline">Underlined text</p>
<p class="line-through">Strikethrough text</p>
<p class="italic">Italic text</p>

<!-- Text Overflow -->
<div class="truncate">Texte tronqué...</div>
<div class="line-clamp-2">Limité à 2 lignes</div>
<div class="line-clamp-3">Limité à 3 lignes</div>

<!-- Letter Spacing -->
<p class="tracking-tight">Tight letter spacing</p>
<p class="tracking-normal">Normal letter spacing</p>
<p class="tracking-wide">Wide letter spacing</p>
```

### Couleurs

```html
<!-- Texte -->
<p class="text-primary">Texte primaire</p>
<p class="text-secondary">Texte secondaire</p>
<p class="text-success">Texte success</p>
<p class="text-warning">Texte warning</p>
<p class="text-danger">Texte danger</p>
<p class="text-info">Texte info</p>
<p class="text-gray-600">Texte gris 600</p>
<p class="text-gray-900">Texte gris 900</p>

<!-- Fond -->
<div class="bg-primary text-white">Fond primaire</div>
<div class="bg-secondary text-white">Fond secondaire</div>
<div class="bg-success text-white">Fond success</div>
<div class="bg-warning text-white">Fond warning</div>
<div class="bg-danger text-white">Fond danger</div>
<div class="bg-info text-white">Fond info</div>
<div class="bg-gray-100">Fond gris clair</div>
<div class="bg-white">Fond blanc</div>

<!-- Bordures -->
<div class="border border-primary">Bordure primaire</div>
<div class="border border-gray-300">Bordure grise</div>
<div class="border-t-2 border-primary">Bordure supérieure</div>
<div class="border-l-4 border-primary">Bordure gauche</div>
<div class="border-solid">Border solid</div>
<div class="border-dashed">Border dashed</div>
<div class="border-dotted">Border dotted</div>
```

### Dimensionnement

```html
<!-- Width -->
<div class="w-full">Width 100%</div>
<div class="w-3/4">Width 75%</div>
<div class="w-1/2">Width 50%</div>
<div class="w-1/4">Width 25%</div>
<div class="max-w-4xl">Max width 1024px</div>
<div class="max-w-6xl">Max width 1280px</div>
<div class="min-w-100">Min width 100px</div>

<!-- Height -->
<div class="h-full">Height 100%</div>
<div class="h-screen">Height viewport</div>
<div class="h-96">Height 384px</div>
<div class="h-64">Height 256px</div>
<div class="max-h-96">Max height 384px</div>
<div class="min-h-screen">Min height viewport</div>

<!-- Aspect Ratio (via CSS) -->
<div style="aspect-ratio: 16/9">Video aspect ratio</div>
```

### Bordures & Radius

```html
<!-- Border Width -->
<div class="border">Border 1px</div>
<div class="border-2">Border 2px</div>
<div class="border-4">Border 4px</div>
<div class="border-0">No border</div>

<!-- Border Sides -->
<div class="border-t">Border top only</div>
<div class="border-r">Border right only</div>
<div class="border-b">Border bottom only</div>
<div class="border-l">Border left only</div>

<!-- Border Radius -->
<div class="rounded-none">No radius</div>
<div class="rounded-sm">Small radius 0.25rem</div>
<div class="rounded">Base radius 0.375rem</div>
<div class="rounded-md">Medium radius 0.5rem</div>
<div class="rounded-lg">Large radius 0.75rem</div>
<div class="rounded-xl">XL radius 1rem</div>
<div class="rounded-full">Full radius (50%)</div>

<!-- Border Color -->
<div class="border border-primary">Primary border</div>
<div class="border border-gray-300">Gray border</div>
<div class="border border-success">Success border</div>
```

### Position

```html
<!-- Position Type -->
<div class="static">Static positioning</div>
<div class="relative">Relative positioning</div>
<div class="absolute">Absolute positioning</div>
<div class="fixed">Fixed positioning</div>
<div class="sticky">Sticky positioning</div>

<!-- Position Values -->
<div class="absolute top-0">Top 0</div>
<div class="absolute right-0">Right 0</div>
<div class="absolute bottom-0">Bottom 0</div>
<div class="absolute left-0">Left 0</div>

<!-- Combined -->
<div class="relative">
  <div class="absolute top-0 right-0">Top right corner</div>
  <div class="absolute top-0 left-0">Top left corner</div>
  <div class="absolute bottom-0 right-0">Bottom right corner</div>
</div>

<!-- Z-Index -->
<div class="z-10">Z-index 10</div>
<div class="z-20">Z-index 20</div>
<div class="z-modal">Z-index modal</div>
<div class="z-tooltip">Z-index tooltip</div>
```

### Opacity

```html
<div class="opacity-0">Opacity 0% (invisible)</div>
<div class="opacity-25">Opacity 25%</div>
<div class="opacity-50">Opacity 50%</div>
<div class="opacity-75">Opacity 75%</div>
<div class="opacity-100">Opacity 100% (opaque)</div>
```

## 🧩 Composants
### Overflow

```html
<!-- Overflow behavior -->
<div class="overflow-visible">Content peut déborder</div>
<div class="overflow-hidden">Content est clippé</div>
<div class="overflow-auto">Scrollbar si nécessaire</div>
<div class="overflow-scroll">Scrollbar toujours visible</div>

<!-- Overflow directions -->
<div class="overflow-x-auto">Scroll horizontal only</div>
<div class="overflow-y-auto">Scroll vertical only</div>
```

### Background

```html
<!-- Background attachment -->
<div class="bg-fixed">Fixed background</div>
<div class="bg-scroll">Scrolling background</div>
<div class="bg-local">Local background</div>

<!-- Background position -->
<div class="bg-center">Center position</div>
<div class="bg-top">Top position</div>
<div class="bg-bottom">Bottom position</div>
<div class="bg-left">Left position</div>
<div class="bg-right">Right position</div>

<!-- Background repeat -->
<div class="bg-repeat">Repeat pattern</div>
<div class="bg-no-repeat">No repeat</div>
<div class="bg-repeat-x">Repeat X only</div>
<div class="bg-repeat-y">Repeat Y only</div>

<!-- Background clip -->
<div class="bg-clip-border">Clip to border</div>
<div class="bg-clip-padding">Clip to padding</div>
<div class="bg-clip-content">Clip to content</div>
```

```html
<!-- Card variants -->
<div class="card">
  <div class="card-header">
    <h2 class="card-title">Basic Card</h2>
  </div>
  <div class="card-body">
    <p>Contenu standard</p>
  </div>
  <div class="card-footer">
    <button class="btn btn-primary btn-sm">Action</button>
  </div>
</div>

<div class="card card-elevated">
  <div class="card-body">
    <p>Carte élevée avec ombre</p>
  </div>
</div>

<div class="card card-flat">
  <div class="card-body">
    <p>Carte plate sans ombre</p>
  </div>
</div>
```

### Boutons

```html
<!-- Variantes principales -->
<button class="btn btn-primary">Primary Button</button>
<button class="btn btn-secondary">Secondary Button</button>
<button class="btn btn-success">Success Button</button>
<button class="btn btn-warning">Warning Button</button>
<button class="btn btn-info">Info Button</button>

<!-- Variantes outline -->
<button class="btn btn-outline-primary">Outline Primary</button>
<button class="btn btn-outline-secondary">Outline Secondary</button>

<!-- Variantes ghost & link -->
<button class="btn btn-ghost">Ghost Button</button>
<button class="btn btn-link">Link Button</button>

<!-- Tailles -->
<button class="btn btn-xs btn-primary">Extra Small</button>
<button class="btn btn-sm btn-primary">Small</button>
<button class="btn btn-md btn-primary">Medium (default)</button>
<button class="btn btn-lg btn-primary">Large</button>
<button class="btn btn-xl btn-primary">Extra Large</button>

<!-- Largeur complète -->
<button class="btn btn-primary" style="width: 100%">Full Width Button</button>

<!-- États -->
<button class="btn btn-primary" disabled>Disabled Button</button>
<button class="btn btn-primary" style="opacity: 0.8">Loading State</button>

<!-- Border radius variants -->
<button class="btn btn-primary btn-rounded-none">No Radius</button>
<button class="btn btn-primary btn-rounded-sm">Small Radius</button>
<button class="btn btn-primary btn-rounded">Base Radius</button>
<button class="btn btn-primary btn-rounded-lg">Large Radius</button>
<button class="btn btn-primary btn-rounded-full">Full Radius</button>

<!-- Button groups -->
<div style="display: flex; gap: 0.5rem">
  <button class="btn btn-primary">Save</button>
  <button class="btn btn-secondary">Cancel</button>
  <button class="btn btn-ghost">Delete</button>
</div>
```

### Cartes

```html
<!-- Variantes de cartes -->
<div class="card">
  <div class="card-header">
    <h2 class="card-title">Basic Card</h2>
    <p class="card-subtitle">With subtitle</p>
  </div>
  <div class="card-body">
    <p class="card-text">Contenu standard de la carte</p>
  </div>
  <div class="card-footer">
    <button class="btn btn-primary btn-sm">Action</button>
  </div>
</div>

<!-- Carte élevée -->
<div class="card card-elevated">
  <div class="card-header">
    <h2 class="card-title">Elevated Card</h2>
  </div>
  <div class="card-body">
    <p class="card-text">Avec ombre élevée pour plus de profondeur</p>
  </div>
</div>

<!-- Carte plate -->
<div class="card card-flat">
  <div class="card-header">
    <h2 class="card-title">Flat Card</h2>
  </div>
  <div class="card-body">
    <p class="card-text">Sans ombre, design minimaliste</p>
  </div>
</div>

<!-- Carte avec image -->
<div class="card">
  <div style="width: 100%; height: 200px; background: linear-gradient(135deg, #2563eb, #1e40af); border-radius: 0.75rem 0.75rem 0 0;"></div>
  <div class="card-header">
    <h2 class="card-title">Card with Image</h2>
  </div>
  <div class="card-body">
    <p class="card-text">Contenu avec image en haut</p>
  </div>
</div>
```

### Formulaires

```html
<!-- Groupe de formulaire basique -->
<form>
  <div class="form-group">
    <label for="name">Full Name</label>
    <input type="text" id="name" placeholder="Enter your name" style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem;">
  </div>

  <div class="form-group">
    <label for="email">Email Address</label>
    <input type="email" id="email" placeholder="your@email.com" style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem;">
    <small style="display: block; margin-top: 0.25rem; color: #6b7280;">We'll never share your email</small>
  </div>

  <div class="form-group">
    <label for="message">Message</label>
    <textarea id="message" rows="4" placeholder="Enter your message..." style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem; font-family: inherit;"></textarea>
  </div>

  <!-- Checkbox -->
  <div class="form-group" style="display: flex; align-items: center; margin-bottom: 1rem;">
    <input type="checkbox" id="agree" style="margin-right: 0.5rem;">
    <label for="agree" style="margin: 0;">I agree to the terms and conditions</label>
  </div>

  <!-- Radio buttons -->
  <div class="form-group">
    <p style="margin-bottom: 0.5rem; font-weight: 500;">Select an option:</p>
    <div style="display: flex; flex-direction: column; gap: 0.5rem;">
      <label style="display: flex; align-items: center;">
        <input type="radio" name="option" style="margin-right: 0.5rem;">
        Option 1
      </label>
      <label style="display: flex; align-items: center;">
        <input type="radio" name="option" style="margin-right: 0.5rem;">
        Option 2
      </label>
      <label style="display: flex; align-items: center;">
        <input type="radio" name="option" style="margin-right: 0.5rem;">
        Option 3
      </label>
    </div>
  </div>

  <!-- Select -->
  <div class="form-group">
    <label for="country">Country</label>
    <select id="country" style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem;">
      <option>Select a country</option>
      <option>United States</option>
      <option>Canada</option>
      <option>France</option>
    </select>
  </div>

  <!-- Boutons -->
  <div style="display: flex; gap: 1rem;">
    <button class="btn btn-primary" style="flex: 1;">Submit Form</button>
    <button class="btn btn-secondary" style="flex: 1;">Reset</button>
  </div>
</form>

<!-- Formulaire inline -->
<form style="display: flex; gap: 1rem; align-items: flex-end;">
  <div style="flex: 1;">
    <label for="search">Search</label>
    <input type="text" id="search" placeholder="Search..." style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem;">
  </div>
  <button class="btn btn-primary">Search</button>
</form>

<!-- États des inputs -->
<div class="form-group">
  <label>Success State</label>
  <input type="text" value="Valid input" style="width: 100%; padding: 0.5rem; border: 2px solid #10b981; border-radius: 0.375rem;">
</div>

<div class="form-group">
  <label>Error State</label>
  <input type="text" placeholder="Invalid input" style="width: 100%; padding: 0.5rem; border: 2px solid #ef4444; border-radius: 0.375rem;">
  <small style="display: block; margin-top: 0.25rem; color: #ef4444;">This field is required</small>
</div>

<div class="form-group">
  <label>Disabled State</label>
  <input type="text" placeholder="Disabled" disabled style="width: 100%; padding: 0.5rem; border: 1px solid #d1d5db; border-radius: 0.375rem; background: #f9fafb; opacity: 0.6;">
</div>
```

## 🚀 Utilisation

### 1. Compiler le SCSS

```bash
# Avec Dart Sass
sass scss/main.scss css/main.css

# Avec node-sass
node-sass scss/main.scss css/main.css

# Avec watch mode
sass --watch scss:css
```

### 2. Importer dans HTML

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="css/main.css">
</head>
<body>
  <!-- Votre contenu -->
</body>
</html>
```

### 3. Utiliser les classes

```html
<div class="flex flex-col gap-4 p-6">
  <h1 class="text-3xl font-bold text-primary">Bonjour!</h1>
  <p class="text-gray-600">Ceci est un paragraphe</p>
  <button class="btn btn-primary">Cliquez-moi</button>
</div>
```

## 🎓 Philosophie ITCSS

Cette architecture suit la méthodologie ITCSS (Inverted Triangle CSS) :

1. **ABSTRACTS** (Spécificité minimale)
   - Variables et configuration
   - Fonctions utilitaires
   - Mixins réutilisables

2. **BASE**
   - Reset/Normalize
   - Styles par défaut
   - Typographie globale

3. **UTILITIES**
   - Classes single-purpose
   - Très réutilisables
   - Spécificité faible à moyenne

4. **COMPONENTS** (Spécificité maximale)
   - Composants stylisés
   - Styles complexes
   - Réutilisables mais spécifiques

## 🔄 Système Responsif

### Mobile-First Approach

```html
<!-- Par défaut: mobile -->
<div class="m-2 text-sm">

<!-- Override sur desktop -->
<div class="m-2 desktop:m-4 text-sm desktop:text-base">
```

### Media Queries

```scss
// Génère: @media (max-width: 1199px)
@include respond(mobile) {
  // Styles mobiles
}

// Génère: @media (min-width: 1200px)
@include respond(desktop) {
  // Styles desktop
}
```

## 💡 Personnalisation

### Ajouter une couleur

```scss
// Dans abstracts/_variables.scss
$colors: (
  // ... couleurs existantes
  custom: #your-color,
);
```

### Ajouter un espacement

```scss
// Dans abstracts/_variables.scss
$spacings: (
  // ... espacements existants
  18: 4.5rem,
);
```

### Créer un composant personnalisé

```scss
// Dans components/_custom.scss
@use '../abstracts/variables' as *;

.my-component {
  padding: map-get($spacings, 4);
  background-color: map-get($colors, primary);
  border-radius: map-get($border-radii, md);
}
```

Puis l'importer dans `main.scss` :

```scss
@use 'components/custom';
```

## 📊 Avantages de cette Architecture

✅ **Modulaire** - Facile à maintenir et à étendre
✅ **Réutilisable** - Composants et utilitaires réutilisables
✅ **Évolutif** - Grandir sans complexité
✅ **Performant** - Pas de redondance CSS
✅ **Responsif** - Breakpoints simples et flexibles
✅ **Maintenable** - Structure claire et organisée
✅ **Customisable** - Tout peut être modifié
✅ **Documenté** - Code bien commenté

## 📝 Licence

Ce framework SCSS est libre d'utilisation et de modification selon vos besoins.

---

**Créé avec ❤️ pour les projets SCSS modernes et maintenables**