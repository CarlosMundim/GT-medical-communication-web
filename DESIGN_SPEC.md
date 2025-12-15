# GT-Medical-Communication: Design Specification

## Authors

- **Prof. Jeanette Dennisson** - Research Lead, Medical Communication Theory
- **Koda van Niekerk Mundim** - Technical Architecture, System Design

---

## Overview

This document specifies the visual and UX requirements for the GT-Medical-Communication web interface.

---

## Design Philosophy

### Japanese Aesthetic Principles (和の美学)

- **Ma (間)** - Intentional whitespace, breathing room
- **Kanso (簡素)** - Simplicity, elimination of clutter
- **Seijaku (静寂)** - Tranquility, calm visual hierarchy
- **Shizen (自然)** - Natural, organic flow
- **Datsuzoku (脱俗)** - Freedom from the ordinary

### Medical Design Principles

- **Trust** - Clean, professional, authoritative
- **Clarity** - Information hierarchy, scannable
- **Accessibility** - WCAG AAA compliance target
- **Safety** - Clear warnings, disclaimers prominent
- **Bilingual** - Seamless JP/EN switching

---

## Color Palette

### Primary Colors

```css
/* Trust Blue - Primary brand color */
--primary-900: #0B3A6A;
--primary-700: #1E5A94;
--primary-500: #2E7AB8;
--primary-300: #6BA3D4;
--primary-100: #E8F2FA;

/* Medical White - Clean backgrounds */
--white: #FFFFFF;
--off-white: #FAFBFC;
--warm-white: #F8F9FA;
```

### Secondary Colors

```css
/* Calm Green - Success, safety */
--green-700: #1B7D46;
--green-500: #28A05C;
--green-100: #E6F5ED;

/* Warm Orange - Attention, warnings */
--orange-700: #C75A00;
--orange-500: #E86F10;
--orange-100: #FFF3E8;

/* Soft Red - Errors, critical */
--red-700: #B91C1C;
--red-500: #DC2626;
--red-100: #FEE2E2;
```

### Neutral Colors

```css
--neutral-900: #1A1A1A;
--neutral-700: #404040;
--neutral-500: #737373;
--neutral-300: #D4D4D4;
--neutral-100: #F5F5F5;
```

---

## Typography

### Font Stack

```css
/* Japanese text */
font-family: "Noto Sans JP", "Hiragino Kaku Gothic ProN", "Yu Gothic", sans-serif;

/* English text */
font-family: "Inter", -apple-system, BlinkMacSystemFont, sans-serif;

/* Monospace (code, data) */
font-family: "JetBrains Mono", "Consolas", monospace;
```

### Type Scale

| Use | Size | Weight | Line Height |
|-----|------|--------|-------------|
| H1 (Hero) | 48px / 3rem | 700 | 1.2 |
| H2 (Section) | 32px / 2rem | 600 | 1.3 |
| H3 (Subsection) | 24px / 1.5rem | 600 | 1.4 |
| Body Large | 18px / 1.125rem | 400 | 1.8 |
| Body | 16px / 1rem | 400 | 1.8 |
| Caption | 14px / 0.875rem | 400 | 1.6 |
| Small | 12px / 0.75rem | 400 | 1.5 |

---

## Spacing System

Based on 4px grid:

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-6: 24px;
--space-8: 32px;
--space-12: 48px;
--space-16: 64px;
--space-24: 96px;
```

---

## Component Specifications

### Buttons

**Primary Button**
- Background: var(--primary-700)
- Text: white
- Padding: 12px 24px
- Border-radius: 8px
- Hover: var(--primary-900)

**Secondary Button**
- Background: transparent
- Border: 1px solid var(--primary-700)
- Text: var(--primary-700)
- Padding: 12px 24px
- Border-radius: 8px

### Cards

- Background: white
- Border: 1px solid var(--neutral-200)
- Border-radius: 12px
- Padding: 24px
- Shadow: 0 1px 3px rgba(0,0,0,0.1)

### Forms

- Input height: 48px
- Border: 1px solid var(--neutral-300)
- Border-radius: 8px
- Focus: 2px solid var(--primary-500)
- Error: border-color var(--red-500)

---

## Accessibility Requirements

- WCAG 2.1 AA minimum, AAA target
- Color contrast ratio: 4.5:1 minimum for text
- Focus indicators visible on all interactive elements
- Keyboard navigation support
- Screen reader compatibility
- Reduced motion support

---

## Bilingual Implementation

- Language toggle in header (JP/EN)
- URL structure: `/` for Japanese, `/en/` for English
- Content parity between languages
- Date formats: Japanese (YYYY年MM月DD日), English (Month DD, YYYY)

---

## Safety Indicators

All AI-generated content must include:
- Clear "AI-generated" badge
- Disclaimer text
- Verification status indicator
- Link to audit trail

---

*Prof. Jeanette Dennisson & Koda van Niekerk Mundim*
