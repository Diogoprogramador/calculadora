---
name: testing-calculadora-libras
description: Test the Calculadora em Libras web app end-to-end. Use when verifying calculator UI, math operations, Libras display, or responsive layout changes.
---

# Testing Calculadora em Libras

## Overview
This is a single-file HTML calculator (`index.html`) with no backend or dependencies. It features Libras (Brazilian Sign Language) emoji display and responsive CSS for PC/mobile.

## How to Test Locally
1. Open `file:///path/to/repo/index.html` in Chrome
2. No server needed — it's a standalone HTML file

## Key Test Areas

### Math Operations
- Basic: +, -, ×, ÷
- Edge cases: division by zero (should show "Erro"), percentage (%)
- Verify results display correctly with pt-BR formatting (comma decimal, dot thousands)

### Libras Display
- Each digit should show a hand emoji and its Portuguese name (e.g., "Um", "Dois")
- The Libras section sits between the result display and buttons
- On error ("Erro"), the Libras section should show the default label with no hand emojis

### Responsive Layout
- Use Puppeteer/CDP to resize viewport for mobile testing (375x667 for iPhone SE)
- Verify all 4 button columns are visible with no horizontal scrolling
- The page has media queries for: <=360px, 480-768px, >=769px, and landscape orientation
- Dark mode support via `prefers-color-scheme`

### Keyboard Input (PC)
- The page intercepts keydown with `e.preventDefault()`, so DevTools shortcuts (F12, Ctrl+Shift+I) may not work when the page has focus
- Supported keys: 0-9, +, - (minus), * (shift+8), / (slash), % (shift+5), Enter/=, Escape, Backspace
- To use `*` via xdotool/computer tool, send `shift+8` not `asterisk`

## Tips
- The page's keydown handler calls `e.preventDefault()` which blocks browser shortcuts. Click outside the page content area or use CDP/Playwright if you need DevTools.
- For mobile viewport testing, use Puppeteer via CDP at `http://localhost:29229` to set viewport dimensions rather than trying to open DevTools device toolbar.
- The calculator state resets cleanly with the Escape key or C button.

## No Secrets Needed
This is a standalone HTML file with no API calls or authentication.
