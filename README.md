# GT Medical Communication - Web Interface

## 医療コミュニケーションAI Webアプリケーション

A research-grade web application for the GT-Medical-Communication pipeline.

## Authors

- **Prof. Jeanette Dennisson** - Research Lead, Medical Communication Theory
- **Koda van Niekerk Mundim** - Technical Architecture, System Design

---

## Overview

This is the **visual frontend** for [GT-Medical-Communication](https://github.com/CarlosMundim/GT-medical-communication), a research-driven framework for human-centred medical communication AI.

### Core Pipeline (Backend)
Repository: https://github.com/CarlosMundim/GT-medical-communication

### Web Interface (This Repo)
A Next.js application providing:
- Beautiful Japanese aesthetic design
- Bilingual (JP/EN) interface
- Visual pipeline representation
- Accessible, medical-grade UX

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
- **Accessibility** - WCAG AAA compliance
- **Safety** - Clear warnings, disclaimers prominent
- **Bilingual** - Seamless JP/EN switching

---

## Technology Stack

```
Frontend:
├── Next.js 14+ (App Router)
├── TypeScript
├── Tailwind CSS
├── Framer Motion (animations)
├── Radix UI (accessible components)
└── React Hook Form + Zod (validation)

Backend Integration:
├── Next.js API Routes
└── Python subprocess / FastAPI wrapper

Testing:
├── Vitest
├── Playwright (E2E)
└── Storybook (components)
```

---

## Getting Started

### Prerequisites
- Node.js 18+
- pnpm (recommended) or npm
- Python 3.11+ (for backend pipeline)

### Installation

```bash
# Clone this repo
git clone https://github.com/CarlosMundim/GT-medical-communication-web.git
cd GT-medical-communication-web

# Install dependencies
pnpm install

# Run development server
pnpm dev

# Open http://localhost:3000
```

### Backend Setup

```bash
# Clone the pipeline repo
git clone https://github.com/CarlosMundim/GT-medical-communication.git
cd GT-medical-communication

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # or .venv\Scripts\Activate on Windows

# Install dependencies
pip install -r requirements.txt

# Test with mock mode
python -m src.main run --input examples/inputs/discharge_bilingual_example.json --mode JP_PATIENT --mock
```

---

## Project Structure

```
GT-medical-communication-web/
├── app/                    # Next.js App Router pages
│   ├── page.tsx           # Landing page
│   ├── dashboard/         # Main dashboard
│   ├── compose/           # Create new communication
│   ├── history/           # View past runs
│   └── api/               # API routes
├── components/
│   ├── ui/                # Base UI components
│   ├── forms/             # Form components
│   ├── display/           # Output display components
│   └── layout/            # Layout components
├── lib/
│   ├── api/               # API client
│   ├── i18n/              # Internationalization
│   └── utils/             # Utilities
├── styles/
│   └── globals.css        # Global styles + Tailwind
├── public/
│   ├── icons/             # Icon assets
│   ├── illustrations/     # Vector illustrations
│   └── locales/           # Translation files
└── DESIGN_SPEC.md         # Full design specification
```

---

## Features

### Modes Supported
| Mode | Japanese | English |
|------|----------|---------|
| Patient Communication | JP_PATIENT | EN_PATIENT |
| Family Explanation | JP_FAMILY | EN_FAMILY |
| Clinical Briefing | JP_CLINICIAN_BRIEF | EN_CLINICIAN_BRIEF |
| OSCE Training | JP_STUDENT_OSCE | EN_STUDENT_OSCE |
| Consent Documentation | JP_CONSENT | EN_CONSENT |

### Key Interfaces
1. **Landing Page** - Bilingual introduction with trust indicators
2. **Dashboard** - Recent outputs, quick actions
3. **Composition** - Mode selection, input forms
4. **Output Display** - Bilingual side-by-side, verification badges
5. **Audit Trail** - Full processing history

---

## Design Specifications

See [DESIGN_SPEC.md](./DESIGN_SPEC.md) for complete design specifications including:
- Color palette
- Typography system
- Component library
- Visual assets
- Animation specs
- Accessibility requirements

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## Related Repositories

- **Core Pipeline**: [GT-medical-communication](https://github.com/CarlosMundim/GT-medical-communication)
- **Web Interface**: This repository

---

## License

This project is for academic and research purposes.

---

## Acknowledgments

- Research collaboration with St. Marianna University
- Grounded Theory methodology for medical communication
- Japanese aesthetic design principles

---

*Prof. Jeanette Dennisson & Koda van Niekerk Mundim*
