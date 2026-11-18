# Daily Fall-Risk Assessment App — SPEC

## Purpose

A simple phone app for ward nurses to record one patient’s daily fall-risk assessment at the bedside, plus a head-nurse screen showing today’s assessment status and risk levels.

Use made-up sample patients only in demos, screenshots, and development data. Do not use real patient details.

## Users

- **Ward nurse:** signs in, enters patient details, completes and saves a daily assessment.
- **Head nurse:** reviews the ward’s assessment status for today.

## Visual direction

- Use **Concept 01 · Calm and structured** from `designs.html` as the selected visual direction for the assessment screen.
- Make the risk-factor descriptions and care-step labels larger than shown in the design preview, with clear, easy-to-read text for bedside phone use.

## Nurse workflow

1. Nurse signs in; the app uses the signed-in nurse’s name on the assessment.
2. Nurse enters ward, bed, date, patient name, and hospital number (HN) for the patient being assessed. The patient is entered each time; no patient roster was requested.
3. Nurse ticks all applicable risk factors.
4. App calculates and displays the risk level using the rules below.
5. Nurse ticks any care steps done. Show 2–3 common care-step checkboxes once approved by ward nurses, plus **Other** with a text field for a nurse-entered step.
6. Before saving, show a review screen with all entered answers and the calculated risk level; the nurse can go back and correct them.
7. On save, record the nurse’s name and automatically fill the assessment time with the current time. For a correction after saving, the nurse asks the head nurse to correct it.

## Assessment fields

- Ward
- Bed
- Date (defaults to today; confirm date handling with nurses)
- Patient name
- Hospital number (HN)
- Risk factors (select all that apply):
  - **R1:** Over 65 and has fallen before
  - **R2:** Confused, or awareness has changed
  - **R3:** Problem with balance or walking
  - **R4:** Poor eyesight
  - **R5:** Medicines that raise fall risk
  - **R6:** Urgent or frequent toilet needs
  - **R7:** Lines or devices attached
- Risk level (calculated by the app; not manually selected)
- Care steps done: 2–3 ward-approved checkbox items, plus **Other** and a text field
- Nurse name (from sign-in)
- Assessment time (automatically filled with the current time on save)

## Risk-level rules

Apply the highest applicable category:

| Selected factors | Risk level |
|---|---|
| Any of R1, R2, or R3 | High |
| Otherwise, any of R4, R5, or R6 | Moderate |
| Otherwise, R7 only | Low |
| No factors selected | None |

## Head-nurse view

- One screen for the ward, for today.
- Show each patient’s name and bed, today’s risk level, and whether an assessment has been recorded.
- Make risk level and not-yet-assessed status easy to scan.
- The user chose to use assessment entries only, rather than enter a separate daily ward list. With entries alone, the app can list assessed patients but cannot know which other patients are on the ward or who has not been assessed. The intended “who has not been assessed yet” view therefore needs a nurse-approved roster source or another workflow decision (see Questions for the nurses).

## Sample data for demos only

These are invented examples and must never be replaced with real patient data in demo material:

| Ward | Bed | Patient | HN | Factors | Calculated risk |
|---|---|---|---|---|---|
| Cedar | 01 | Mina Example | DEMO-001 | R1, R4 | High |
| Cedar | 02 | Arun Sample | DEMO-002 | R5 | Moderate |
| Cedar | 03 | Dara Fiction | DEMO-003 | R7 | Low |

## Questions for the nurses

1. What are the 2–3 common care steps that should appear as checkboxes? The ward requested common steps plus an **Other** free-text option, but the actual steps were not provided.
2. How should the app know the full list of patients expected on the ward today so it can show who has not been assessed? The current choice to use assessment entries alone cannot identify patients with no entry.
3. Should date default to the phone’s current date, and can nurses record or amend an assessment for a different date?
4. Which user roles need sign-in, and how is the head nurse’s ward view limited to the correct ward?

## Scope boundary

This document describes the requested app and open questions only. No app has been built. Clinical content, including the care-step labels and roster workflow, needs ward confirmation before implementation.
