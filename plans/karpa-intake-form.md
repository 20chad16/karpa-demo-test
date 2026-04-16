# Plan: Karpa Health Intake Form — Clickable Prototype

> Source PRD: [Issue #1](https://github.com/20chad16/karpa-demo-test/issues/1) / `PRD.md`

## Architectural decisions

Durable decisions that apply across all phases:

- **Delivery format**: Single self-contained HTML file, openable via `file://` with no build tools or server
- **Styling**: Tailwind CSS via CDN (`cdn.tailwindcss.com`), extended with custom theme config inline
- **Typography**: Manrope (headlines) + Inter (body/labels) via Google Fonts
- **Icons**: Material Symbols Outlined via Google Fonts
- **Color palette**: MEDVI warm scheme — cream background (~#FBF5EB), brown/tan accents (~#B08D57), dark brown text; replaces the teal palette from `form.html`
- **JavaScript**: Vanilla JS, no framework. Wizard state held in a plain JS object in memory (no localStorage, no backend)
- **Wizard structure**: 3 labeled steps ("About You" → "Health Screening" → "Vitals") + a Thank You confirmation view, all rendered as `<section>` elements toggled via CSS class. One step visible at a time.
- **Stepper UI**: Horizontal dot stepper in the header with step labels. Active step highlighted with accent color, completed steps show a filled dot or checkmark.
- **Units**: Imperial — height in feet/inches, weight in lbs
- **Component patterns**: Reuse `form.html` patterns — rounded cards for inputs, card-style radio toggles for gender/Yes-No, checkbox grid for Health Q2, vertical checkbox list for Health Q1
- **Responsive breakpoint**: Tailwind `md:` (768px). Mobile = stacked single-column. Desktop = max-width ~768px centered container.

---

## Phase 1: Wizard Shell + Step 1 (About You)

**User stories**: 1, 2, 3, 4, 5, 6, 7, 8, 23, 24, 27, 28, 32

### What to build

Build the entire page from scratch as a single HTML file. The page includes:

**Header & Branding** — Karpa Health logo/wordmark, a star-rating trust badge, and the 3-step labeled stepper ("About You" → "Health Screening" → "Vitals"). The stepper reflects the current active step.

**Hero Section** — An encouraging headline ("Reach your goal weight fast / without restrictive diets and exercise"), a supporting sub-headline, and a placeholder hero image in a rounded container. Matches the visual weight of the MEDVI screenshot and `form.html` hero.

**Step 1 Form: "About You"** — Five input groups:
1. **Height**: Two side-by-side dropdowns — Feet (4, 5, 6, 7) and Inches (0–11)
2. **Weight (lbs)**: Number input
3. **Goal Weight (lbs)**: Number input
4. **Gender**: Male / Female card-style radio toggle
5. **Date of Birth**: Three dropdowns — Month (January–December), Day (1–31), Year (generated range, e.g. 1930–2008)

**Validation** — All five fields required. Clicking "Next" with missing fields shows red error borders and a brief message. "Next" is blocked until all fields are completed.

**Navigation** — "Next" button advances to Step 2 (placeholder content for now). Stepper updates to show Step 1 as completed. Smooth fade/slide CSS transition between steps.

**Responsive** — Full-width stacked layout on mobile. Centered max-width container on desktop. Touch-friendly tap targets (min 44px).

**Color & Styling** — MEDVI warm cream/tan/brown palette applied via Tailwind config. Typography, spacing, border radius, and shadow patterns adapted from `form.html`.

### Acceptance criteria

- [ ] Opening the HTML file in a browser shows the Karpa Health branded header with trust badge and 3-step stepper
- [ ] Hero section displays with headline, sub-text, and placeholder image
- [ ] Step 1 shows all 5 input groups (Height ft/in, Weight, Goal Weight, Gender, DOB)
- [ ] Attempting to click "Next" with empty fields shows error highlighting on missing fields
- [ ] Completing all fields and clicking "Next" transitions to a Step 2 placeholder with a smooth animation
- [ ] Stepper updates to show Step 1 completed and Step 2 active
- [ ] Page is responsive: stacked layout at mobile widths, centered container on desktop
- [ ] File opens correctly via `file://` protocol with no console errors

---

## Phase 2: Step 2 (Health Screening with Full Interactivity)

**User stories**: 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 25, 26, 31

### What to build

Replace the Step 2 placeholder with the complete Health Screening step containing five question groups and all interactive behaviors.

**Health Questions 1 — Disqualifying Conditions** — Vertical checkbox list with card-style rows (matching `form.html` Health Assessment pattern). Seven conditions with bold labels and descriptive sub-text:
- End-stage kidney disease (on or about to be on dialysis)
- End-stage liver disease (cirrhosis)
- Current suicidal thoughts and/or prior suicidal attempt
- Cancer (active diagnosis, active treatment, or in remission or cancer-free for less than 5 continuous years — does not apply to non-melanoma skin cancer that was considered cured via simple excision)
- Severe gastrointestinal condition (gastroparesis, blockage, inflammatory bowel disease)
- Current diagnosis of or treatment for alcohol, opioid, or substance use disorder/dependence
- None of the above

**Disqualification warning**: When any condition (other than "None") is checked, an inline amber/orange warning banner appears below the section.

**Health Questions 2 — Detailed Medical History** — Dense multi-column checkbox grid (2–3 cols desktop, 1 col mobile). All 34 conditions:
Gallbladder disease, Hypertension, Seizures, Glaucoma, Sleep apnea, Type 2 diabetes (not on insulin), Type 2 diabetes (on insulin), Type 1 diabetes, Diabetic retinopathy / optic nerve damage / blindness, Use of warfarin, History of or current pancreatitis, Thyroid history (MTC/MEN 2), Gout, High cholesterol or triglycerides, Depression, Head injury, Tumor/infection in brain/spinal cord, Low sodium, Liver disease including fatty liver, Kidney disease, Elevated resting heart rate (tachycardia), Coronary artery disease / heart attack / stroke in last 2 years, Allergic to any medication, Congestive heart failure, QT prolongation / heart rhythm disorder, Hospitalization within last year, HIV, Acid reflux, Asthma/reactive airway disease, Urinary stress incontinence, PCOS, Clinically proven low testosterone, Osteoarthritis, Constipation, None of the above.

**"None of the above" mutual exclusion** — For both Health Q1 and Q2: selecting "None" clears all other checkboxes; selecting any condition clears "None."

**Three Yes/No Questions** — Card-style button toggles:
1. "Within the last 3 months, have you taken opiate pain medications and/or opiate-based street drugs?"
2. "Have you had prior weight loss surgeries?"
3. "Do you currently take any prescription medications?"

**Conditional follow-up fields** — When "Yes" is selected for any of the three questions, a text area slides open below asking for more details. Selecting "No" hides it.

**Validation** — At least one checkbox selected in each health question group (including "None"). All three Yes/No questions must be answered. Conditional text fields required when visible.

**Back navigation** — "Back" button returns to Step 1 with all previously entered data preserved.

### Acceptance criteria

- [ ] Health Questions 1 displays all 7 conditions with descriptive sub-text plus "None of the above"
- [ ] Checking any Health Q1 condition shows an inline disqualification warning banner
- [ ] Health Questions 2 displays all 34 conditions in a multi-column grid plus "None of the above"
- [ ] "None of the above" in both groups is mutually exclusive with all other options
- [ ] All three Yes/No questions render as card-style toggles
- [ ] Selecting "Yes" on any Yes/No question reveals a follow-up text area with slide animation
- [ ] Selecting "No" hides the follow-up text area if previously shown
- [ ] Validation prevents advancing without completing all question groups (including conditional fields)
- [ ] "Back" button returns to Step 1 with all data intact
- [ ] Layout is responsive (checkbox grid collapses to single column on mobile)

---

## Phase 3: Step 3 (Vitals) + Thank You + Final Polish

**User stories**: 20, 21, 22, 29, 30

### What to build

**Step 3 Form: "Vitals"** — Two radio-button question groups styled as selectable card rows:

1. **Blood Pressure Range** (single-select):
   - <120/80 (Normal)
   - 120 to 129/<80 (Elevated)
   - 130 to 139/80-89 (High Stage 1)
   - ≥140/90 (High Stage 2) — selecting this shows a red inline warning: "For your safety, this answer may disqualify you from a prescription."

2. **Average Resting Heart Rate** (single-select):
   - <60 beats per minute (Slow)
   - 60 to 100 beats per minute (Normal)
   - 101 to 110 beats per minute (Slightly Fast)
   - >110 beats per minute (Fast)

**Validation** — Both questions required before "Submit" is enabled.

**Thank You Page** — After submitting Step 3, display a confirmation view (replacing the form):
- Headline: "Thank you for completing your health assessment"
- Sub-text: "A member of the Karpa Health team will review your information and reach out to you shortly."
- Stepper shows all 3 steps completed.

**Final Polish (all steps)** — Smooth slide/fade CSS transitions between every step. Consistent animation timing. Review all steps for visual consistency, spacing, and color alignment with MEDVI palette. Ensure mobile layout is polished across all steps. Verify the complete end-to-end flow works flawlessly.

### Acceptance criteria

- [ ] Step 3 shows both vitals questions as selectable card-style radio rows
- [ ] Selecting "≥140/90 (High Stage 2)" shows a red disqualification warning inline
- [ ] Both questions must be answered before "Submit" is enabled
- [ ] Clicking "Submit" transitions to the Thank You confirmation page
- [ ] Thank You page shows completion message and "we'll contact you" text
- [ ] Stepper shows all 3 steps completed on the Thank You page
- [ ] "Back" from Step 3 returns to Step 2 with all data preserved
- [ ] Smooth slide/fade transitions work between all steps (1→2, 2→3, 3→Thank You, and back)
- [ ] Complete end-to-end flow works: Hero → Step 1 → Step 2 → Step 3 → Thank You
- [ ] Mobile responsive across all steps at 375px viewport width
