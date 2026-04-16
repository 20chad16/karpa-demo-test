# PRD: Karpa Health — Medical Weight Loss Intake Form (Clickable Prototype)

## Problem Statement

Karpa Health needs a polished, clickable prototype of a medical weight loss intake form to present to stakeholders. The form must capture all the clinical screening questions currently used in the MEDVI GLP intake flow (approximately 50+ data points across personal info, health screenings, and vitals), but presented in a modern, multi-step wizard interface that feels premium and trustworthy.

The existing MEDVI form crams everything onto a single long scrolling page, which is overwhelming. The prototype should break the flow into digestible steps with a clear progress indicator, inline validation, conditional follow-up fields, and disqualification warnings — all wrapped in MEDVI's warm cream/tan/brown color palette under the **Karpa Health** brand.

This is a **static front-end prototype** (HTML/CSS/JS, no backend). Its purpose is stakeholder review and design validation before engineering begins on the production application.

## Solution

A single-page, self-contained HTML/CSS/JS clickable prototype featuring a **3-step wizard** with smooth transitions, powered by Tailwind CSS. The form replicates every question from the MEDVI intake screenshot under the Karpa Health brand, using MEDVI's warm color scheme. The wizard enforces field validation per step, shows conditional follow-up fields, and displays inline disqualification warnings for medically sensitive answers.

### Flow Overview

```
[Hero + Branding] → Step 1: About You → Step 2: Health Screening → Step 3: Vitals → Thank You Page
```

### Step Breakdown

**Step 1 — "About You"**
- Height: Feet dropdown (4–7) + Inches dropdown (0–11)
- Weight (lbs): Number input
- Goal Weight (lbs): Number input
- Gender: Male / Female radio toggle
- Date of Birth: Month dropdown + Day dropdown + Year dropdown

**Step 2 — "Health Screening"**
- **Health Questions 1** — "Do any of these apply to you?" (checkboxes, multi-select):
  - End-stage kidney disease (on or about to be on dialysis)
  - End-stage liver disease (cirrhosis)
  - Current suicidal thoughts and/or prior suicidal attempt
  - Cancer (active diagnosis, active treatment, or in remission or cancer-free for less than 5 continuous years — does not apply to non-melanoma skin cancer that was considered cured via simple excision)
  - Severe gastrointestinal condition (gastroparesis, blockage, inflammatory bowel disease)
  - Current diagnosis of or treatment for alcohol, opioid, or substance use disorder/dependence
  - None of the above

- **Health Questions 2** — "Do any of these apply to you?" (checkboxes, multi-select):
  - Gallbladder disease
  - Hypertension (high blood pressure)
  - Seizures
  - Glaucoma
  - Sleep apnea
  - Type 2 diabetes (not on insulin)
  - Type 2 diabetes (on insulin)
  - Type 1 diabetes
  - Diabetic retinopathy (diabetic eye disease), damage to the optic nerve from trauma or reduced blood flow, or blindness
  - Use of the blood thinner warfarin (Coumadin/Jantoven)
  - History of or current pancreatitis
  - Personal or family history of thyroid cyst/nodule, thyroid cancer, medullary thyroid carcinoma, or multiple endocrine neoplasia syndrome type 2 (MEN 2)
  - Gout
  - High cholesterol or triglycerides
  - Depression
  - Head injury
  - Tumor/infection in brain/spinal cord
  - Low sodium
  - Liver disease, including fatty liver
  - Kidney disease
  - Elevated resting heart rate (tachycardia)
  - Coronary artery disease or heart attack/stroke in last 2 years
  - Allergic to any medication
  - Congestive heart failure
  - QT prolongation or other heart rhythm disorder
  - Hospitalization within the last 1 year
  - Human immunodeficiency virus (HIV)
  - Acid reflux
  - Asthma/reactive airway disease
  - Urinary stress incontinence
  - Polycystic ovarian syndrome (PCOS)
  - Clinically proven low testosterone
  - Osteoarthritis
  - Constipation
  - None of the above

- **Opiate Use Question** — "Within the last 3 months, have you taken opiate pain medications and/or opiate-based street drugs?" (Yes/No)
  - **Conditional:** If Yes → show text area: "Please provide some more information"

- **Prior Weight Loss Surgery** — "Have you had prior weight loss surgeries?" (Yes/No)
  - **Conditional:** If Yes → show text area: "Please provide some more information"

- **Prescription Medications** — "Do you currently take any prescription medications?" (Yes/No)
  - **Conditional:** If Yes → show text area: "What medications do you currently take?"

**Step 3 — "Vitals"**
- **Blood Pressure Range** (radio, single-select):
  - <120/80 (Normal)
  - 120 to 129/<80 (Elevated)
  - 130 to 139/80-89 (High Stage 1)
  - ≥140/90 (High Stage 2) — **triggers disqualification warning**

- **Average Resting Heart Rate** (radio, single-select):
  - <60 beats per minute (Slow)
  - 60 to 100 beats per minute (Normal)
  - 101 to 110 beats per minute (Slightly Fast)
  - >110 beats per minute (Fast)

**Thank You Page**
- Confirmation message: "Thank you for completing your health assessment"
- Sub-text: "A member of the Karpa Health team will review your information and reach out to you shortly."
- No form data submission (static prototype)

## User Stories

1. As a prospective patient, I want to see the Karpa Health brand and a trust indicator (star rating badge) in the header, so that I feel confident this is a legitimate medical service.
2. As a prospective patient, I want to see a hero section with an encouraging headline and image before starting the form, so that I understand the benefit of completing the intake.
3. As a prospective patient, I want to see a clear step indicator showing my progress (e.g., "About You → Health Screening → Vitals"), so that I know how much of the form remains.
4. As a prospective patient, I want to enter my height using separate Feet and Inches dropdowns, so that I can quickly select my height without typing.
5. As a prospective patient, I want to enter my current weight in pounds, so that I provide accurate body composition data.
6. As a prospective patient, I want to enter my goal weight in pounds, so that the provider knows my weight loss target.
7. As a prospective patient, I want to select my biological gender (Male/Female), so that the provider can consider gender-specific medical factors.
8. As a prospective patient, I want to enter my date of birth using Month, Day, and Year dropdowns, so that I can quickly provide my age without worrying about date format.
9. As a prospective patient, I want to review a list of serious disqualifying health conditions and check any that apply to me, so that the provider can determine my eligibility for GLP-1 treatment.
10. As a prospective patient, I want to see an inline warning when I select a disqualifying condition in Health Questions 1, so that I understand this may affect my eligibility.
11. As a prospective patient, I want to review a comprehensive list of medical conditions and check any that apply to me, so that the provider has my full medical history.
12. As a prospective patient, I want a "None of the above" option that clears all other checkboxes when selected, so that I can indicate a clean bill of health without confusion.
13. As a prospective patient, I want checking any specific condition to automatically uncheck "None of the above," so that my selections remain logically consistent.
14. As a prospective patient, I want to answer whether I've used opiate pain medications in the last 3 months, so that the provider can assess drug interaction risks.
15. As a prospective patient, I want a follow-up text field to appear when I answer "Yes" to the opiate question, so that I can provide additional context.
16. As a prospective patient, I want to answer whether I've had prior weight loss surgeries, so that the provider understands my medical history.
17. As a prospective patient, I want a follow-up text field to appear when I answer "Yes" to the weight loss surgery question, so that I can describe the procedure.
18. As a prospective patient, I want to answer whether I currently take prescription medications, so that the provider can check for drug interactions.
19. As a prospective patient, I want a follow-up text field to appear when I answer "Yes" to the prescription medications question, so that I can list my current medications.
20. As a prospective patient, I want to select my blood pressure range from clearly labeled options, so that I can report my vitals without needing a medical background.
21. As a prospective patient, I want to see an inline warning when I select "≥140/90 (High Stage 2)" for blood pressure, so that I understand this answer may disqualify me from treatment.
22. As a prospective patient, I want to select my average resting heart rate from clearly labeled options, so that the provider has my cardiovascular baseline.
23. As a prospective patient, I want all fields on a step to be validated before I can proceed, so that I don't accidentally skip a question.
24. As a prospective patient, I want to see clear error highlighting on any fields I missed, so that I know exactly what needs to be completed.
25. As a prospective patient, I want to click "Back" to return to a previous step and change my answers, so that I can correct mistakes without starting over.
26. As a prospective patient, I want my answers to be preserved when navigating between steps, so that I don't lose progress.
27. As a prospective patient, I want smooth transitions between steps, so that the experience feels polished and modern.
28. As a prospective patient, I want the form to work well on my phone with stacked full-width inputs, so that I can complete it on any device.
29. As a prospective patient, I want to see a confirmation page after completing all steps, so that I know my assessment is complete.
30. As a prospective patient, I want the confirmation page to tell me that someone will contact me, so that I know what to expect next.
31. As a stakeholder reviewing this prototype, I want the form to demonstrate realistic validation behavior (required fields, conditional show/hide, disqualification warnings), so that I can evaluate the UX before development begins.
32. As a stakeholder, I want the entire prototype to be a self-contained HTML file that can be opened in any browser, so that I can review it without setting up a development environment.

## Implementation Decisions

### Architecture
- **Single self-contained HTML file** with inline Tailwind CSS (via CDN) and vanilla JavaScript. No build tools, no frameworks, no dependencies beyond the Tailwind CDN.
- The existing `form.html` serves as the design reference for component styling (rounded cards, input patterns, typography hierarchy). The new prototype will borrow its structural patterns while adopting the MEDVI color palette.

### Color Scheme & Branding
- **Brand**: "Karpa Health" displayed in the header
- **Color palette**: Replicate MEDVI's warm cream/tan/brown aesthetic — cream (#FBF5EB or similar) background, brown/tan (#B08D57) accent and button colors, dark brown text
- **Typography**: Use Manrope (headlines) and Inter (body/labels) from Google Fonts, matching form.html
- **Trust badge**: Star rating indicator in the header (similar to form.html's Trustpilot-style badge)

### Wizard Navigation
- **3-step labeled stepper** in the header: "About You" → "Health Screening" → "Vitals"
- Active step highlighted with accent color; completed steps show a checkmark
- **Back button** on Steps 2 and 3; **Next button** on Steps 1 and 2; **Submit button** on Step 3
- **Smooth slide/fade transitions** between steps using CSS transitions/animations
- Step state preserved in JavaScript memory (no localStorage needed for static demo)

### Form Components
- **Height**: Two side-by-side dropdowns — Feet (4, 5, 6, 7) and Inches (0–11)
- **Weight / Goal Weight**: Number inputs with "lbs" suffix label
- **Gender**: Two-button radio toggle (styled as cards, like form.html)
- **Date of Birth**: Three dropdowns — Month (January–December), Day (1–31), Year (dynamically generated, reasonable range e.g., 1930–2008)
- **Health Questions 1**: Vertical list of checkboxes in card-style rows with bold labels and descriptive sub-text (matching form.html's Health Assessment section style)
- **Health Questions 2**: Dense grid layout (2–3 columns on desktop, single column on mobile) with compact checkbox items (matching form.html's Detailed Medical History section)
- **Yes/No questions**: Horizontal button pairs (styled as card toggles)
- **Conditional follow-up fields**: Text areas that slide open with animation when "Yes" is selected
- **Blood pressure / Heart rate**: Vertical radio button groups (styled as selectable card rows)

### Validation Rules
- All fields on a step must be completed before the "Next" button is enabled
- Missing fields highlighted with red border and brief error message on attempted advance
- For checkbox groups (Health Q1, Health Q2): at least one option (including "None of the above") must be selected
- For Yes/No questions: one option must be selected
- For conditional follow-up text fields: required when visible (when parent answer is "Yes")

### Conditional Logic
- **"None of the above" mutual exclusion**: Selecting it clears all other checkboxes in the same group. Selecting any other checkbox clears "None of the above."
- **Yes/No follow-ups**: "Yes" reveals a text area beneath the question with a smooth slide-down animation. "No" hides it (if previously shown).
- Applies to: Opiate question, Weight loss surgery question, Prescription medications question.

### Disqualification Warnings
- **Health Questions 1**: When any condition (other than "None of the above") is checked, display an inline amber/orange warning banner below the section: "For your safety, one or more of your selections may affect your eligibility for treatment. A provider will review your responses."
- **Blood Pressure ≥140/90**: When "High Stage 2" is selected, display a red warning banner below the option: "For your safety, this answer may disqualify you from a prescription."
- Warnings are informational only — the user can still proceed to the next step.

### Responsive Design
- **Desktop**: Max-width container (~768px), centered. Two-column grids where appropriate (height ft/in, Health Q2 checkbox grid).
- **Mobile**: Full-width stacked layout. Single-column for all inputs. Touch-friendly tap targets (min 44px height). Stepper collapses to compact format.
- Breakpoint: Standard Tailwind `md:` (768px).

## Testing Decisions

Since this is a static clickable prototype for stakeholder review, **manual click-through testing** is the primary validation method.

### Manual Test Scenarios
1. Complete the entire form happy path (all "None of the above" / "No" answers, normal vitals) — verify smooth progression through all 3 steps to Thank You page
2. Select disqualifying conditions in Health Q1 — verify warning banner appears, verify user can still proceed
3. Select ≥140/90 blood pressure — verify red warning banner appears
4. Test "None of the above" exclusivity — check a condition, then check "None of the above" and confirm the condition is unchecked (and vice versa)
5. Answer "Yes" to all three Yes/No questions — verify follow-up text fields appear with animation
6. Answer "Yes" then switch to "No" — verify follow-up text fields hide
7. Attempt to advance a step with missing required fields — verify error highlights and blocked navigation
8. Navigate back to Step 1 from Step 3 — verify all previously entered data is preserved
9. Test on mobile viewport (375px wide) — verify stacked layout, touch targets, readable text
10. Open the HTML file directly in browser (file://) — verify everything works without a server

### Automated Tests
Not required for the static prototype. If desired later, Playwright or Cypress tests could be added to automate the above scenarios, using the form.html test patterns as reference.

## Out of Scope

- **Backend integration**: No API calls, no data persistence, no form submission to a server
- **User authentication or accounts**: No login, no registration
- **Payment or subscription flows**: The form ends at "Thank You"
- **Email/SMS notifications**: No actual contact will be initiated
- **HIPAA compliance or data encryption**: This is a static demo with no real data handling
- **A/B testing or analytics tracking**: No tracking scripts
- **Accessibility (WCAG AA) audit**: Best-effort semantic HTML and ARIA labels, but no formal audit
- **Browser support below modern evergreen browsers**: No IE11 or legacy browser support
- **Localization / multi-language support**
- **Print stylesheet**
- **Dark mode**

## Further Notes

- The complete list of medical conditions in both Health Questions sections is exhaustive and must match the MEDVI screenshot exactly — no conditions should be omitted or paraphrased differently than specified in this PRD.
- The `form.html` file in the repo serves as the design system reference. Its component patterns (rounded cards, input styling, checkbox layouts, button styling, typography scale) should be reused, but the color palette must be swapped to MEDVI's warm cream/tan/brown.
- The prototype should be a **single HTML file** that can be opened directly in a browser (via `file://` protocol) with no build step, no server, and no additional dependencies beyond CDN-loaded Tailwind CSS and Google Fonts.
- Future phases may add: patient contact info collection, photo upload, e-signature consent, and backend API integration. The prototype architecture should be clean enough to serve as a starting point for that work.
