# Design System Reference

<!-- This is a TEMPLATE. Fill in each section with your project's actual values. -->

## Color Palette

<!-- Define your brand and semantic colors. Example: -->
<!-- Primary: #3B82F6 (blue-500) — used for CTAs, links, active states -->
<!-- Secondary: #6366F1 (indigo-500) — used for accents, secondary actions -->
<!-- Accent: #F59E0B (amber-500) — used for highlights, badges -->
<!-- Semantic: success=#22C55E, warning=#EAB308, error=#EF4444, info=#3B82F6 -->
<!-- Neutrals: gray-50 through gray-900 for text, borders, backgrounds -->

## Typography Scale

<!-- Define font families, sizes, and weights. Example: -->
<!-- Font family: Inter (sans), JetBrains Mono (mono) -->
<!-- Sizes: xs=12px, sm=14px, base=16px, lg=18px, xl=20px, 2xl=24px, 3xl=30px, 4xl=36px -->
<!-- Weights: normal=400, medium=500, semibold=600, bold=700 -->
<!-- Line heights: tight=1.25, normal=1.5, relaxed=1.75 -->

## Spacing System

<!-- Define your spacing scale. Example: -->
<!-- Base unit: 4px (0.25rem) -->
<!-- Scale: 1=4px, 2=8px, 3=12px, 4=16px, 5=20px, 6=24px, 8=32px, 10=40px, 12=48px, 16=64px -->

## Breakpoints

<!-- Define responsive breakpoints. Example: -->
<!-- sm: 640px — mobile landscape -->
<!-- md: 768px — tablet -->
<!-- lg: 1024px — desktop -->
<!-- xl: 1280px — wide desktop -->
<!-- 2xl: 1536px — ultra-wide -->

## Component Patterns

<!-- Document recurring component patterns. Example: -->

### Buttons
<!-- Variants: primary, secondary, ghost, danger -->
<!-- Sizes: sm (h-8), md (h-10), lg (h-12) -->
<!-- States: default, hover, active, disabled, loading -->

### Inputs
<!-- Variants: text, select, textarea, checkbox, radio -->
<!-- States: default, focus, error, disabled -->
<!-- Always include a visible label; use aria-describedby for help text -->

### Cards
<!-- Structure: header (optional), body, footer (optional) -->
<!-- Border radius, shadow, padding conventions -->

### Modals / Dialogs
<!-- Overlay color, max-width, padding, close behavior -->
<!-- Focus trap and Escape key to dismiss -->

## Animation & Transitions

<!-- Define motion standards. Example: -->
<!-- Duration: fast=150ms, normal=200ms, slow=300ms -->
<!-- Easing: ease-out for entrances, ease-in for exits, ease-in-out for state changes -->
<!-- Prefer transform/opacity for performance; avoid animating layout properties -->

## Dark Mode

<!-- Document dark mode strategy. Example: -->
<!-- Approach: CSS custom properties toggled via class="dark" on <html> -->
<!-- Background: gray-900, surface: gray-800, text: gray-100 -->
<!-- Ensure contrast ratio >= 4.5:1 for all text -->

## Anti-Patterns

<!-- List things to avoid. Example: -->
<!-- Do NOT use inline styles for colors — always reference design tokens -->
<!-- Do NOT hardcode pixel values — use the spacing scale -->
<!-- Do NOT create one-off colors — extend the palette if needed -->
<!-- Do NOT skip focus indicators — every interactive element needs a visible focus ring -->
