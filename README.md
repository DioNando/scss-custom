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
```

### Display

```html
<div class="block">Block</div>
<div class="inline">Inline</div>
<div class="flex">Flexbox</div>
<div class="grid">Grid</div>
<div class="hidden">Caché</div>
<div class="mobile:hidden desktop:block">Caché sur mobile</div>
```

### Flexbox

```html
<div class="flex flex-col gap-4">
  <div class="flex justify-center items-center">Centré</div>
  <div class="flex justify-between">Espacé</div>
  <div class="flex-1">Flex grow</div>
</div>
```

### Grid

```html
<div class="grid grid-cols-3 gap-4">
  <div>Col 1</div>
  <div class="col-span-2">Col 2-3</div>
</div>

<!-- Responsive -->
<div class="grid mobile:grid-cols-1 desktop:grid-cols-3 gap-4">
  Items
</div>
```

### Typographie

```html
<h1 class="text-5xl font-bold">Titre</h1>
<p class="text-lg text-gray-600">Paragraphe</p>
<span class="text-sm uppercase tracking-wide">Label</span>
<div class="truncate">Texte tronqué...</div>
```

### Couleurs

```html
<!-- Texte -->
<p class="text-primary">Texte primaire</p>
<p class="text-gray-600">Texte gris</p>

<!-- Fond -->
<div class="bg-primary text-white">Fond primaire</div>
<div class="bg-gray-100">Fond gris clair</div>

<!-- Bordures -->
<div class="border border-gray-300">Bordure</div>
<div class="border-t-2 border-primary">Bordure supérieure</div>
```

### Dimensionnement

```html
<div class="w-full">Pleine largeur</div>
<div class="max-w-6xl">Largeur maximale</div>
<div class="h-screen">Hauteur d'écran</div>
<div class="min-h-100">Hauteur minimale</div>
```

### Bordures & Radius

```html
<div class="border rounded">Bordure avec radius</div>
<div class="border-2 rounded-lg">Bordure épaisse</div>
<div class="border-none rounded-full">Bordure complète</div>
```

### Position

```html
<div class="relative">
  <div class="absolute top-0 right-0">Coin supérieur droit</div>
</div>
<div class="fixed bottom-0 left-0 z-modal">Modal fixe</div>
```

### Opacity

```html
<div class="opacity-50">50% transparent</div>
<div class="opacity-0">Invisible</div>
<div class="opacity-100">Opaque</div>
```

## 🧩 Composants

### Boutons

```html
<!-- Variants -->
<button class="btn btn-primary">Primaire</button>
<button class="btn btn-outline-primary">Outline</button>
<button class="btn btn-ghost">Ghost</button>

<!-- Tailles -->
<button class="btn btn-sm">Small</button>
<button class="btn btn-lg">Large</button>

<!-- États -->
<button class="btn btn-primary" disabled>Désactivé</button>
<button class="btn btn-loading">Chargement...</button>
```

### Cartes

```html
<div class="card">
  <div class="card-header">
    <h2 class="card-title">Titre</h2>
  </div>
  <div class="card-body">
    <p>Contenu</p>
  </div>
  <div class="card-footer">
    <button class="btn btn-primary">Action</button>
  </div>
</div>
```

### Formulaires

```html
<form class="form">
  <div class="form-group">
    <label class="form-label required">Nom</label>
    <input type="text" class="form-control" placeholder="Nom">
    <small class="form-text">Texte d'aide</small>
  </div>

  <div class="form-group">
    <label class="form-label">Message</label>
    <textarea class="form-control"></textarea>
  </div>

  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="agree">
    <label class="form-check-label" for="agree">J'accepte</label>
  </div>

  <button class="btn btn-primary btn-block">Envoyer</button>
</form>
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