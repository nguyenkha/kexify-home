# Kexify Homepage Design Spec

Design tokens and guidelines for the homepage (Jekyll + GitHub Pages) to match the kexify frontend UI/UX.

## Brand

- **Name**: kexify (lowercase)
- **Tagline**: keys simplified
- **Accent color**: Blue #3b82f6 (Tailwind blue-500)
- **Meta theme color**: #030712
- **Repo URL**: https://github.com/nguyenkha/kexify-web

## Logo

### Text Logo

Used in sidebar, login, freeze, and recovery pages:

```html
<h1 style="font-size: 30px; line-height: 36px; font-weight: 700; letter-spacing: -0.025em;">kexify</h1>
<p style="font-size: 11px; color: #4b5563;">keys simplified</p>
```

- Font: System sans-serif stack (no custom font)
- Size: `text-3xl` (30px), weight 700, `tracking-tight` (-0.025em)
- Tagline: 11px, `text-muted` (#4b5563 dark / #9ca3af light)
- Always lowercase "kexify"

### App Icon SVG (favicon, PWA)

"K" lettermark styled as a key — blue on dark background:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" fill="none">
  <!-- Background: rounded square -->
  <rect width="512" height="512" rx="96" fill="#030712"/>
  <!-- Vertical stroke (key shaft) -->
  <rect x="152" y="120" width="36" height="272" rx="18" fill="#3b82f6"/>
  <!-- Upper diagonal (key tooth) -->
  <path d="M188 256l120-120h48L212 280z" fill="#3b82f6"/>
  <!-- Lower diagonal -->
  <path d="M188 256l120 120h48L212 232z" fill="#3b82f6"/>
  <!-- Key bow (circle at top of shaft) -->
  <circle cx="170" cy="120" r="36" stroke="#3b82f6" stroke-width="20" fill="#030712"/>
</svg>
```

Available sizes: `icon.svg` (scalable), `icon-192.png`, `icon-512.png`

### Shield Icon SVG (security branding)

Shield with lock — used for security-related contexts:

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" fill="none">
  <rect width="512" height="512" rx="96" fill="#1a1a2e"/>
  <path d="M256 80c-60 0-112 40-128 96-4 14-6 28-6 44 0 80 56 160 134 192 78-32 134-112 134-192 0-16-2-30-6-44-16-56-68-96-128-96z" stroke="#3b82f6" stroke-width="24" fill="none" stroke-linejoin="round"/>
  <circle cx="256" cy="220" r="32" fill="#3b82f6"/>
  <rect x="248" y="252" width="16" height="56" rx="8" fill="#3b82f6"/>
</svg>
```

### Splash Screen (Loading State)

Used while JS bundle loads:

```html
<div style="text-align:center">
  <div style="font-size:30px;line-height:36px;font-weight:700;letter-spacing:-0.025em;color:#fff">kexify</div>
  <div style="font-size:11px;color:#4b5563;margin-top:2px">keys simplified</div>
  <div style="margin-top:32px">
    <!-- Blue spinner -->
    <svg width="24" height="24" viewBox="0 0 24 24" style="animation:spin 1s linear infinite;color:#3b82f6">
      <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2.5" fill="none" opacity="0.2"/>
      <path d="M12 2a10 10 0 019.95 9" stroke="currentColor" stroke-width="2.5" fill="none" stroke-linecap="round"/>
    </svg>
  </div>
</div>
```

Background: `#030712` (surface-primary dark)

## Color Tokens

### Light Theme (default)

```css
:root {
  --surface-primary: #ffffff;
  --surface-secondary: #f9fafb;
  --surface-tertiary: #f3f4f6;
  --border-primary: #e5e7eb;
  --border-secondary: #f3f4f6;
  --text-primary: #111827;
  --text-secondary: #374151;
  --text-tertiary: #6b7280;
  --text-muted: #9ca3af;
}
```

### Dark Theme (`data-theme="dark"` or `prefers-color-scheme: dark`)

```css
[data-theme="dark"] {
  --surface-primary: #030712;
  --surface-secondary: #111827;
  --surface-tertiary: #1f2937;
  --border-primary: #1f2937;
  --border-secondary: rgba(31, 41, 55, 0.5);
  --text-primary: #ffffff;
  --text-secondary: #d1d5db;
  --text-tertiary: #6b7280;
  --text-muted: #4b5563;
}
```

### Semantic Colors

| Purpose       | Light       | Dark        |
|---------------|-------------|-------------|
| Success/green | #4ade80     | #4ade80     |
| Error/red     | #f87171     | #f87171     |
| Warning/amber | #d97706     | #d97706     |
| Info/blue     | #3b82f6     | #3b82f6     |
| Purple accent | #c084fc     | #c084fc     |

## Typography

### Font Stack

```css
font-family: ui-sans-serif, system-ui, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji';
```

Monospace (for code, addresses, versions):
```css
font-family: ui-monospace, SFMono-Regular, 'SF Mono', Menlo, Consolas, monospace;
```

### Scale (Tailwind-based)

| Usage            | Size   | Weight | Color            |
|------------------|--------|--------|------------------|
| Page heading     | 18px   | 600    | text-primary     |
| Section heading  | 14px   | 500    | text-primary     |
| Body text        | 13px   | 400    | text-secondary   |
| Small / caption  | 12px   | 400    | text-secondary   |
| Micro / metadata | 10px   | 400    | text-muted       |
| Button text      | 12px   | 500    | white (on blue)  |

### Line Height

- Headings: 1.25 (tight)
- Body: 1.5 (relaxed)
- Micro text: 1.4

## Spacing

Based on 4px grid (Tailwind default):

| Token | Value |
|-------|-------|
| xs    | 4px   |
| sm    | 8px   |
| md    | 16px  |
| lg    | 24px  |
| xl    | 32px  |
| 2xl   | 48px  |

- Page padding: 16px mobile, 32px desktop
- Section gap: 20px (space-y-5)
- Card padding: 12-20px

## Components

### Cards

```css
.card {
  background: var(--surface-secondary);
  border: 1px solid var(--border-primary);
  border-radius: 8px;       /* rounded-lg */
  padding: 12px 16px;
  overflow: hidden;
}
```

Dividers inside cards: `border-color: var(--border-secondary)`

### Buttons

Primary:
```css
.btn-primary {
  background: #2563eb;      /* blue-600 */
  color: white;
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 12px;
  font-weight: 500;
  transition: background 150ms;
}
.btn-primary:hover { background: #1d4ed8; }  /* blue-700 */
```

Secondary:
```css
.btn-secondary {
  background: var(--surface-tertiary);
  color: var(--text-secondary);
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 12px;
  font-weight: 500;
  transition: background 150ms;
}
.btn-secondary:hover { background: var(--border-primary); }
```

### Status Badges

```css
.badge-success {
  background: rgba(74, 222, 128, 0.1);
  color: #4ade80;
  font-size: 10px;
  font-weight: 500;
  padding: 2px 6px;
  border-radius: 4px;
}
.badge-warning {
  background: rgba(234, 179, 8, 0.1);
  color: #eab308;
  /* same sizing as success */
}
```

### Icons

- Style: Heroicons outline (24x24 viewBox, stroke-based)
- Stroke width: 2 (default), 2.5 (emphasis)
- Sizes: 12px (micro), 16px (small), 20px (default)
- Color: inherits from text color

## Layout Patterns

### Sidebar (Desktop)

- Width: 256px (w-64)
- Background: `var(--surface-secondary)`
- Border-right: `var(--border-primary)`

### Header Bar

- Height: 56px (3.5rem)
- Border-bottom: `var(--border-primary)`
- Padding: 16px mobile, 32px desktop

### Content Area

- Max-width: none (fluid within sidebar layout)
- Padding: 16px mobile, 32px desktop
- Scrollable with overflow-auto

### Footer

- No border
- Padding: 6px horizontal
- Text: 10px, text-muted, tabular-nums

## Responsive Breakpoints

| Breakpoint | Width  | Behavior          |
|------------|--------|-------------------|
| Mobile     | <768px | Sidebar hidden, hamburger menu |
| Desktop    | ≥768px | Sidebar visible   |

## Animations

- Transitions: 150ms ease (colors, backgrounds)
- Flash green: `color: #4ade80 → inherit` over 1.2s ease-out
- Flash red: `color: #f87171 → inherit` over 1.2s ease-out
- Spinner: rotate 360° in 1s linear infinite
- Slide-up (toasts): `translateY(16px) → 0` + `opacity 0 → 1` in 0.2s

## Dark Mode Implementation

Use `data-theme="dark"` on `<html>` with JS toggle. For Jekyll homepage, can use:

```js
// Respect system preference, allow manual toggle
const theme = localStorage.getItem('theme') ||
  (matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
document.documentElement.setAttribute('data-theme', theme);
```

## Jekyll-Specific Notes

1. **Copy the CSS variables block** (light + dark) into your `_sass` or `<style>` block
2. **Use `var(--token)` references** in all styles — never hardcode colors
3. **Dark theme default** recommended for homepage (matches app dark feel)
4. **Minimal dependencies**: No Tailwind needed — raw CSS with these tokens is sufficient
5. **Font**: System font stack, no external font loading needed
6. **Copyright**: `© {year} Kha Do` — 10px, text-muted, right-aligned
