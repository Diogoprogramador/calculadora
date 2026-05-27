---
name: testing-calculadora
description: Test the Calculadora em Libras web app end-to-end. Use when verifying layout, functionality, or accessibility changes.
---

# Testing the Calculadora em Libras

## Local Setup

The app is a single static `index.html` file with inline CSS and JS — no build step or dependencies.

```bash
cd /home/ubuntu/repos/calculadora
python3 -m http.server 8081 &
# Open http://localhost:8081/index.html in browser
```

## Key Testing Areas

### Layout / Viewport Fit
- The calculator should fit entirely within the browser viewport without scrolling
- Verify via JS console: `document.documentElement.scrollHeight <= window.innerHeight` should return `true`
- All 20 buttons (CE, C, %, ÷, 7-9, ×, 4-6, −, 1-3, +, ±, 0, comma, =) must be visible
- Footer text "Calculadora acessível em Libras — por Diogo" must be visible at the bottom

### Calculator Functionality
- Test basic arithmetic: click number buttons, operator, number, equals
- Verify the result display shows the correct number
- Verify the expression display shows the full operation (e.g., "5 + 3 =")
- Verify the Libras display updates with the correct hand emoji and number name in Portuguese

### Libras Display
- Each digit 0-9 maps to a hand emoji and Portuguese name (Zero/Um/Dois/Três/Quatro/Cinco/Seis/Sete/Oito/Nove)
- The Libras section shows both the emoji and the name

### Clear Button
- C button should reset display to 0, clear expression, and show "Zero" in Libras
- CE button should clear current entry only

### Responsive Design
- Test at different viewport sizes using DevTools device emulation
- Key breakpoints: 360px (small mobile), 480-768px (tablet), 769px+ (desktop)
- Landscape mode: `max-height: 500px` media query hides hand emojis on buttons

## Branches
- `main` — original Python tkinter calculator
- Feature branches may contain the web version (`index.html`)

## Devin Secrets Needed
None — the app is fully static with no authentication or API calls.
