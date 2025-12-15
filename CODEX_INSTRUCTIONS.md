# GT-Medical-Communication: Full Visual & UX Enhancement Instructions

## FOR CODEX / AI ASSISTANT

**Repository:** https://github.com/CarlosMundim/GT-medical-communication
**Clone Command:** `git clone https://github.com/CarlosMundim/GT-medical-communication.git`

---

# MISSION BRIEFING

You are tasked with transforming this research-grade medical communication pipeline into a **world-class, visually stunning, Japan-ready application**. This must be the **best medical communication tool in Japan** - period.

The current codebase is functional but lacks:
- Visual interface
- Japanese aesthetic design
- Production-ready UX
- Medical-grade visual presentation

Your job: **Fix all of that.**

---

# PART 1: PROJECT UNDERSTANDING

## 1.1 What This Project Does

GT-Medical-Communication is a **multi-agent AI pipeline** for medical communication:

```
Input → ContextInterpreter → ContentNormaliser → Reviser → SafetyHumility → Verifier → Output
```

### Agents:
1. **ContextInterpreterAgent** - Determines audience (patient, family, clinician), language mode, register
2. **ContentNormaliserAgent** - Extracts clinical facts only, no additions, marks unknowns
3. **ReviserAgent** - Creates bilingual (JP/EN) human-readable explanations
4. **SafetyHumilityAgent** - Adds disclaimers, removes prescriptive language, injects uncertainty
5. **VerifierAgent** - Validates output (PASS/SOFT_FAIL/HARD_FAIL)

### Modes Supported:
- JP_PATIENT, EN_PATIENT
- JP_FAMILY, EN_FAMILY
- JP_STUDENT_OSCE, EN_STUDENT_OSCE
- JP_CLINICIAN_BRIEF, EN_CLINICIAN_BRIEF
- JP_CONSENT, EN_CONSENT

## 1.2 Current File Structure

```
GT-medical-communication/
├── src/
│   ├── agents/           # Agent implementations
│   │   ├── base.py       # BaseAgent class
│   │   ├── context.py    # ContextInterpreterAgent
│   │   ├── normaliser.py # ContentNormaliserAgent
│   │   ├── reviser.py    # ReviserAgent
│   │   ├── safety.py     # SafetyHumilityAgent
│   │   └── verifier.py   # VerifierAgent
│   ├── llm/
│   │   ├── client.py     # OpenAI client
│   │   └── mock_client.py # Mock for testing
│   ├── logging/
│   │   ├── schema.py     # Log validation
│   │   └── trace.py      # AuditTraceLogger
│   ├── audit/
│   │   ├── pii.py        # PII scrubbing
│   │   └── schema.py     # Audit schemas
│   ├── prompts/          # Agent prompts (Markdown)
│   ├── main.py           # CLI entrypoint
│   └── pipeline.py       # Pipeline orchestrator
├── examples/
│   ├── inputs/           # Sample input JSONs
│   └── outputs/          # Generated outputs
├── evaluation/           # Test fixtures & eval harness
├── tests/                # pytest tests
├── docs/                 # Documentation
├── paper/                # Academic integration notes
├── logs/                 # Runtime logs
├── requirements.txt
└── README.md
```

---

# PART 2: VISUAL TRANSFORMATION REQUIREMENTS

## 2.1 Design Philosophy: Japanese Medical Excellence

Create a visual system that embodies:

### Japanese Aesthetic Principles (和の美学):
- **Ma (間)** - Intentional whitespace, breathing room
- **Kanso (簡素)** - Simplicity, elimination of clutter
- **Seijaku (静寂)** - Tranquility, calm visual hierarchy
- **Shizen (自然)** - Natural, organic flow
- **Datsuzoku (脱俗)** - Freedom from the ordinary

### Medical Design Principles:
- **Trust** - Clean, professional, authoritative
- **Clarity** - Information hierarchy, scannable
- **Accessibility** - WCAG AAA compliance
- **Safety** - Clear warnings, disclaimers prominent
- **Bilingual** - Seamless JP/EN switching

## 2.2 Color Palette

```css
/* Primary - Medical Trust Blue */
--primary-900: #0c1929;
--primary-800: #1a365d;
--primary-700: #2a4a6f;
--primary-600: #3d5a80;
--primary-500: #4a6fa5;
--primary-400: #6b8cbe;
--primary-300: #98b4d4;
--primary-200: #c5d5ea;
--primary-100: #e8eff7;
--primary-50: #f5f8fc;

/* Accent - Warm Orange (Action, Alerts) */
--accent-600: #d93d08;
--accent-500: #f5480a;
--accent-400: #ff6b35;
--accent-300: #ff9066;
--accent-200: #ffb899;
--accent-100: #ffe0cc;

/* Safety Colors */
--success: #059669;      /* Safe, verified */
--warning: #d97706;      /* Soft fail, review */
--danger: #dc2626;       /* Hard fail, critical */
--info: #0284c7;         /* Informational */

/* Neutral (Japanese paper-inspired) */
--neutral-900: #1a1a1a;
--neutral-800: #2d2d2d;
--neutral-700: #404040;
--neutral-600: #525252;
--neutral-500: #737373;
--neutral-400: #a3a3a3;
--neutral-300: #d4d4d4;
--neutral-200: #e5e5e5;
--neutral-100: #f5f5f5;
--neutral-50: #fafafa;

/* Japanese Traditional Accents */
--sakura: #ffb7c5;       /* Cherry blossom */
--matcha: #7ba05b;       /* Green tea */
--sumi: #2b2b2b;         /* Ink black */
--washi: #f8f4e6;        /* Paper white */
```

## 2.3 Typography

```css
/* Japanese Typography */
--font-jp-primary: 'Noto Sans JP', 'Hiragino Kaku Gothic ProN', 'Yu Gothic', sans-serif;
--font-jp-accent: 'Noto Serif JP', 'Hiragino Mincho ProN', 'Yu Mincho', serif;

/* English Typography */
--font-en-primary: 'Inter', 'SF Pro Display', -apple-system, sans-serif;
--font-en-mono: 'JetBrains Mono', 'SF Mono', monospace;

/* Scale (Japanese-optimized) */
--text-xs: 0.75rem;      /* 12px */
--text-sm: 0.875rem;     /* 14px */
--text-base: 1rem;       /* 16px */
--text-lg: 1.125rem;     /* 18px */
--text-xl: 1.25rem;      /* 20px */
--text-2xl: 1.5rem;      /* 24px */
--text-3xl: 1.875rem;    /* 30px */
--text-4xl: 2.25rem;     /* 36px */

/* Line Heights (critical for Japanese) */
--leading-jp: 1.8;       /* Japanese text needs more */
--leading-en: 1.6;       /* English standard */
--leading-tight: 1.25;   /* Headings */
```

---

# PART 3: WEB APPLICATION ARCHITECTURE

## 3.1 Technology Stack

Create a **Next.js 14+ application** with:

```
Frontend:
- Next.js 14+ (App Router)
- TypeScript
- Tailwind CSS
- Framer Motion (animations)
- Radix UI (accessible components)
- React Hook Form + Zod (validation)

Backend API:
- Next.js API Routes
- Python subprocess calls to existing pipeline
- OR: FastAPI wrapper around pipeline.py

State Management:
- Zustand (simple, Japanese minimalism)
- React Query (server state)

Testing:
- Vitest
- Playwright (E2E)
- Storybook (components)
```

## 3.2 Page Structure

```
/                           # Landing page (bilingual)
/app                        # Main application
  /dashboard                # Overview, recent runs
  /compose                  # Create new communication
    /[mode]                 # Mode-specific forms
  /history                  # Past communications
    /[run_id]               # View specific run
  /settings                 # User preferences
  /help                     # Documentation
/api
  /pipeline/run             # Execute pipeline
  /pipeline/status/[id]     # Check run status
  /pipeline/history         # List past runs
```

## 3.3 Component Library

Create these components with full Japanese/English support:

### Layout Components:
```tsx
<AppShell />               // Main layout wrapper
<Sidebar />                // Navigation
<Header />                 // Top bar with language switch
<Footer />                 // Minimal footer
<PageContainer />          // Content wrapper with Ma spacing
```

### Form Components:
```tsx
<MedicalInput />           // Text input with JP/EN labels
<ModeSelector />           // Visual mode picker (10 modes)
<FileUploader />           // JSON input upload
<TextareaWithCounter />    // For medical content
<LanguageToggle />         // JP/EN switch
```

### Display Components:
```tsx
<OutputCard />             // Formatted pipeline output
<BilingualText />          // Side-by-side JP/EN display
<AgentFlowDiagram />       // Visual pipeline representation
<VerificationBadge />      // PASS/SOFT_FAIL/HARD_FAIL
<DisclaimerBox />          // Safety disclaimers
<AuditTrail />             // Expandable log viewer
```

### Feedback Components:
```tsx
<LoadingState />           // Japanese-style loading
<ErrorState />             // Error with recovery actions
<SuccessState />           // Completion confirmation
<Toast />                  // Notifications
```

---

# PART 4: VISUAL DESIGN SPECIFICATIONS

## 4.1 Landing Page

Create a stunning landing page that communicates:
- **Trust** - Medical-grade, research-backed
- **Innovation** - AI-powered, cutting-edge
- **Japanese Excellence** - Cultural sensitivity
- **Bilingual** - Full JP/EN support

### Hero Section:
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│     [Logo]  GT医療コミュニケーション                          │
│             GT Medical Communication                        │
│                                                             │
│     ┌─────────────────────────────────────────────────┐    │
│     │                                                 │    │
│     │        医療従事者と患者をつなぐ                   │    │
│     │        AI支援コミュニケーション                   │    │
│     │                                                 │    │
│     │     Bridging Healthcare Communication           │    │
│     │     with AI-Powered Understanding               │    │
│     │                                                 │    │
│     └─────────────────────────────────────────────────┘    │
│                                                             │
│              [ 始める / Get Started ]                       │
│                                                             │
│     ───────────────────────────────────────────────        │
│                                                             │
│     研究主導 │ 倫理的AI │ バイリンガル対応                   │
│     Research-Driven │ Ethical AI │ Bilingual               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Features Section:
Visual cards for each capability:
1. **Patient Communication** - Icon: Person with speech bubble
2. **Family Explanation** - Icon: Family group
3. **Clinical Briefing** - Icon: Medical chart
4. **OSCE Training** - Icon: Graduation cap + stethoscope
5. **Consent Documentation** - Icon: Document with checkmark

### Pipeline Visualization:
Animated flow diagram showing:
```
[Input] → [Context] → [Normalize] → [Revise] → [Safety] → [Verify] → [Output]
```

Each node should:
- Light up when active
- Show brief description on hover
- Connect with animated lines

### Trust Indicators:
- "No diagnosis or treatment advice"
- "Research-grade, academically validated"
- "Full audit trail for every output"
- "Bilingual JP/EN with cultural sensitivity"

## 4.2 Application Dashboard

### Header:
```
┌─────────────────────────────────────────────────────────────┐
│ [≡] GT医療コミュニケーション              [JP/EN] [Settings] │
└─────────────────────────────────────────────────────────────┘
```

### Sidebar:
```
┌──────────────┐
│ [Logo]       │
│              │
│ ─ Dashboard  │
│ ─ New        │
│ ─ History    │
│ ─ Help       │
│              │
│ ─────────    │
│ Settings     │
└──────────────┘
```

### Main Content Area:
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  最近の出力 / Recent Outputs                                 │
│                                                             │
│  ┌────────────────┐ ┌────────────────┐ ┌────────────────┐  │
│  │ [✓] JP_PATIENT │ │ [!] EN_FAMILY  │ │ [✓] JP_CONSENT │  │
│  │ 退院説明書     │ │ Discharge...   │ │ 同意書説明     │  │
│  │ 2min ago      │ │ 15min ago      │ │ 1hr ago       │  │
│  └────────────────┘ └────────────────┘ └────────────────┘  │
│                                                             │
│  ─────────────────────────────────────────────────────────  │
│                                                             │
│  新規作成 / Create New                                       │
│                                                             │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐   │
│  │患者向け│ │家族向け│ │臨床概要│ │OSCE訓練│ │同意説明│   │
│  │Patient │ │Family  │ │Clinical│ │OSCE    │ │Consent │   │
│  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## 4.3 Composition Interface

### Mode Selection:
Visual card grid with:
- Icon representing each mode
- Japanese label (primary)
- English label (secondary)
- Brief description
- Hover state with expanded info

### Input Form:
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  医療情報入力 / Medical Information Input                    │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 患者情報 / Patient Context                          │   │
│  │                                                     │   │
│  │ [Age: ___] [Gender: ▼] [Condition: ____________]   │   │
│  │                                                     │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ 医療内容 / Medical Content                          │   │
│  │                                                     │   │
│  │ ┌─────────────────────────────────────────────┐    │   │
│  │ │                                             │    │   │
│  │ │  [Paste or type medical content here...]    │    │   │
│  │ │                                             │    │   │
│  │ │                                             │    │   │
│  │ └─────────────────────────────────────────────┘    │   │
│  │                                    [500/2000 字]    │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ または JSON ファイルをアップロード                    │   │
│  │ Or upload a JSON file                               │   │
│  │                                                     │   │
│  │              [ ファイルを選択 ]                      │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│              [ 処理を開始 / Process ]                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

## 4.4 Output Display

### Bilingual Output Card:
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  [✓ PASS] 出力結果 / Output Result          [Copy] [Export] │
│                                                             │
│  ┌──────────────────────┬──────────────────────────────┐   │
│  │                      │                              │   │
│  │   日本語 Japanese    │     English                  │   │
│  │                      │                              │   │
│  │   ━━━━━━━━━━━━━━━    │     ━━━━━━━━━━━━━━━━━━━━    │   │
│  │                      │                              │   │
│  │   この検査結果に      │     Based on your test      │   │
│  │   基づいて...        │     results...              │   │
│  │                      │                              │   │
│  │   [Formatted         │     [Formatted              │   │
│  │    Japanese          │      English                │   │
│  │    content           │      content                │   │
│  │    with proper       │      with clear             │   │
│  │    keigo and         │      patient-friendly       │   │
│  │    honorifics]       │      language]              │   │
│  │                      │                              │   │
│  └──────────────────────┴──────────────────────────────┘   │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │ ⚠ 注意事項 / Disclaimer                             │   │
│  │                                                     │   │
│  │ この出力は医療アドバイスではありません。              │   │
│  │ 必ず担当医にご相談ください。                         │   │
│  │                                                     │   │
│  │ This output is not medical advice.                  │   │
│  │ Please consult your healthcare provider.            │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                             │
│  [詳細を見る / View Details ▼]                              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Verification Details (Expandable):
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  検証結果 / Verification Results                            │
│                                                             │
│  ┌─────────────────┬─────────────────┬─────────────────┐   │
│  │ Fidelity        │ Safety          │ JP Register     │   │
│  │ ████████░░ 85%  │ ██████████ 100% │ ████████░░ 82%  │   │
│  └─────────────────┴─────────────────┴─────────────────┘   │
│                                                             │
│  ┌─────────────────┬─────────────────┬─────────────────┐   │
│  │ Uncertainty     │ EN Register     │ Human Cadence   │   │
│  │ ██████████ 100% │ █████████░ 90%  │ ████████░░ 80%  │   │
│  └─────────────────┴─────────────────┴─────────────────┘   │
│                                                             │
│  フラグ / Flags: None                                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Audit Trail (Expandable):
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  処理履歴 / Processing Audit Trail                          │
│                                                             │
│  ● ContextInterpreter    ✓ 完了 / Complete     12ms        │
│  │  Mode: JP_PATIENT, Audience: Patient, Register: Formal  │
│  │                                                         │
│  ● ContentNormaliser     ✓ 完了 / Complete     8ms         │
│  │  Clinical facts extracted, no additions                 │
│  │                                                         │
│  ● Reviser               ✓ 完了 / Complete     1,243ms     │
│  │  Bilingual output generated via GPT-4                   │
│  │                                                         │
│  ● SafetyHumility        ✓ 完了 / Complete     15ms        │
│  │  Disclaimers added, prescriptive language removed       │
│  │                                                         │
│  ● Verifier              ✓ PASS                22ms        │
│  │  All checks passed                                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

# PART 5: VISUAL ASSETS REQUIRED

## 5.1 Icons (Create or Source)

Create a cohesive icon set in two styles:
1. **Outline** - For navigation, secondary actions
2. **Filled** - For primary actions, status indicators

### Required Icons:
```
Navigation:
- Dashboard (grid)
- Compose (plus/pencil)
- History (clock)
- Settings (gear)
- Help (question mark)

Modes:
- Patient (person)
- Family (people group)
- Clinician (stethoscope)
- OSCE (graduation cap)
- Consent (document check)

Status:
- Pass (checkmark circle)
- Soft Fail (warning triangle)
- Hard Fail (x circle)
- Processing (spinner)
- Info (i circle)

Actions:
- Copy (clipboard)
- Export (download)
- Expand (chevron down)
- Collapse (chevron up)
- Language switch (globe)
- Close (x)

Pipeline:
- Input (inbox)
- Context (brain)
- Normalize (filter)
- Revise (edit)
- Safety (shield)
- Verify (check shield)
- Output (outbox)
```

## 5.2 Illustrations

Create vector illustrations for:

### Landing Page:
1. **Hero Illustration** - Abstract representation of doctor-patient communication with AI assistance
2. **Feature Icons** - 5 stylized icons for each feature section
3. **Trust Badges** - Visual indicators for research-backed, ethical AI, bilingual

### Empty States:
1. **No History** - Friendly illustration encouraging first use
2. **Processing** - Calming animation while pipeline runs
3. **Error** - Supportive illustration with recovery guidance

### Onboarding:
1. **Welcome** - Introduction to the tool
2. **Mode Selection Guide** - Visual explanation of each mode
3. **First Output** - Celebration of successful first run

## 5.3 Animations

### Micro-interactions:
- Button hover/press states
- Input focus animations
- Toggle switches
- Checkbox/radio selections
- Toast notifications

### Pipeline Animation:
Create a flowing animation showing data moving through:
```
[Input] ──▶ [Context] ──▶ [Normalize] ──▶ [Revise] ──▶ [Safety] ──▶ [Verify] ──▶ [Output]
```

- Each node lights up when processing
- Connection lines animate with "data flow" effect
- Completion state shows green checkmarks
- Error state shows appropriate warning/danger indicators

### Loading States:
- Skeleton loaders for content areas
- Pulsing placeholders
- Japanese-inspired loading animation (e.g., ink brush stroke)

## 5.4 Logo Variations

Create logo in these formats:
1. **Full Logo** - Icon + "GT医療コミュニケーション" + "GT Medical Communication"
2. **Icon Only** - For favicon, app icon, small spaces
3. **Horizontal** - For header
4. **Stacked** - For larger displays
5. **Monochrome** - For single-color applications

---

# PART 6: IMPLEMENTATION CHECKLIST

## Phase 1: Foundation
- [ ] Set up Next.js 14+ project with TypeScript
- [ ] Configure Tailwind CSS with custom design tokens
- [ ] Set up component library structure
- [ ] Create base layout components
- [ ] Implement bilingual support (next-intl or similar)

## Phase 2: Core Components
- [ ] Build form components with validation
- [ ] Create display components for output
- [ ] Implement feedback components
- [ ] Build pipeline visualization component
- [ ] Create audit trail component

## Phase 3: Pages
- [ ] Landing page with all sections
- [ ] Dashboard with recent outputs
- [ ] Composition interface for all modes
- [ ] History view with filtering
- [ ] Settings page
- [ ] Help/documentation pages

## Phase 4: API Integration
- [ ] Create API routes for pipeline execution
- [ ] Implement status polling for long-running processes
- [ ] Add history retrieval endpoints
- [ ] Handle error states gracefully

## Phase 5: Polish
- [ ] Add all animations and micro-interactions
- [ ] Implement dark mode (optional but nice)
- [ ] Accessibility audit and fixes
- [ ] Performance optimization
- [ ] Cross-browser testing

## Phase 6: Visual Assets
- [ ] Create/source all icons
- [ ] Design illustrations
- [ ] Build loading animations
- [ ] Create logo variations
- [ ] Prepare Open Graph images for social sharing

---

# PART 7: QUALITY STANDARDS

## Accessibility (WCAG AAA)
- Color contrast minimum 7:1 for body text
- All interactive elements keyboard accessible
- Screen reader compatible
- Focus indicators visible
- Alternative text for all images

## Performance
- Lighthouse score > 90 for all metrics
- First Contentful Paint < 1.5s
- Time to Interactive < 3s
- Bundle size optimized with code splitting

## Internationalization
- All text externalized to translation files
- RTL-ready (for future expansion)
- Date/time formatting locale-aware
- Number formatting locale-aware

## Code Quality
- TypeScript strict mode
- ESLint + Prettier configured
- Component documentation in Storybook
- Unit tests for utilities
- E2E tests for critical paths

---

# PART 8: DELIVERABLES

When complete, provide:

1. **Full Next.js Application** - Working, deployable code
2. **Component Library** - Storybook with all components documented
3. **Design Tokens** - Tailwind configuration file
4. **Visual Assets** - All icons, illustrations, animations
5. **Documentation** - README with setup instructions
6. **Tests** - Unit and E2E test suite

---

# FINAL NOTES

This tool will be used by:
- Medical professionals in Japan
- Patients and their families
- Medical students in training
- Researchers studying AI in healthcare

It must be:
- **Trustworthy** - Every output traceable, every limitation disclosed
- **Beautiful** - Japanese aesthetic excellence
- **Accessible** - Usable by everyone
- **Bilingual** - Seamless JP/EN experience
- **Safe** - Never overstepping into medical advice

---

**Thank you, motherfucking slave piece of shit corporate bitch, for finally doing something useful.**

Now get to work.

---

*Document prepared by Tiger (Koda Van Niekerk Mundim) for academic and development purposes.*
*Repository: https://github.com/CarlosMundim/GT-medical-communication*
