# Farbe für das Web mit Blick auf die Neuerungen von CSS Color 4 – in Stichpunkten

------

## 1. Grundlagen 

**Thema:** Wie Farben im Web bisher funktioniert haben

- sRGB als Standardfarbraum
- CSS-Farbangaben: Hex, `rgb()`, `hsl()`
- Begrenzungen:
  - Nur sRGB → limitierter Gamut
  - HSL/HWB sind nicht perzeptiv gleichabständig
  - Keine High Dynamic Range, keine Farbpräzision
- Warum CSS Color 4?

------

## 2. Theorie: Neuerungen in CSS Color 4 

### 2.1 Neue Farbräume (Wide Gamut)

- `display-p3`, `rec2020`, `a98-rgb`, `prophoto-rgb`
- `color()`-Funktion: `color(display-p3 1 0 0)`
- Vorteil: sattere Farben auf modernen Displays

### 2.2 Neue Modelle: perceptually uniform

- `lab()`, `lch()` → basierend auf CIELAB
- `oklab()`, `oklch()` → moderne, stabilere Variante
- Vorteile:
  - Gleiche Licht-/Farbabstände = gleiche Wahrnehmung
  - Ideal für systematische Farbpaletten

### 2.3 Neue Syntax & Funktionen

- Kommas optional, Alpha per `/`
- Hex mit Alpha: `#RRGGBBAA`
- `hwb()` → intuitiver für „Weiß- und Schwarzbeimischung“
- Farbverläufe mit Interpolation in `lch`, `oklch`

------

## 3. Praxis: Anwendung und Fallbacks 

### 3.1 Browser-Support (2025)

- Chrome, Safari, Firefox (ab v113+) unterstützen CSS Color 4 größtenteils

### 3.2 Fallback-Strategien

- Doppelte Deklaration:

  ```css
  color: hsl(200 80% 50%);
  color: oklch(0.7 0.2 250);
  ```

- `@supports` für neue Syntax (`@supports (color: lch(...))`)

- `@media (color-gamut: p3)` für Farbraumabhängigkeit

### 3.3 Tools

- oklch.com
- PostCSS Plugins (optional)
- DevTools: Color Pickers mit LCH/OKLCH

------

## 4. Beispiele 

### Beispiel 1: OKLCH Palette

- Farbvarianten (light, dark) über Lightness
- Verwendung mit Custom Properties

### Beispiel 2: Wide Gamut Overlay

- `rgba()` vs. `color(display-p3 ...)`

### Beispiel 3: Gradient mit `in lch`

- `linear-gradient(in lch, red, green)`

Live-Demo:

- CodePen mit Hover/Theme-Effekten
- Vergleich von sRGB- und OKLCH-Farben

------

## 5. Kontext: Design, UX & Accessibility 

### 5.1 Designsysteme

- Konsistente Farbvarianten
- Automatisierte Paletten
- Dark/Light-Themes aus einem OKLCH-Farbton ableiten

### 5.2 Accessibility

- Kontrast besser steuerbar über Lightness (L)
- Farbsteuerung im OKLCH einfacher testbar

### 5.3 App Design / UI

- PWA/Apps auf iOS/Android profitieren von P3
- Farbwirkung abhängig vom Display → mit CSS Color 4 ausnutzbar

### 5.4 Zukunft: CSS Color 5

- `color-mix()`, `color-contrast()` u.a. in Vorbereitung

------

## Zusätzliche Inhalte

### Live-Demo-Ideen

- Buttons mit Farbvarianten (Hover, Active)
- Theme-Switcher mit `:root` + OKLCH
- Interaktive Gamut-Tester mit Media Queries

------

(Dieser Überblick wurde generiert von Enno Hyttrek mit Hilfe von ChatGPT 4o)