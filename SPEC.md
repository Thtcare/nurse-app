# Daily Fall-Risk Assessment App — SPEC

## Purpose

A simple phone app for ward nurses to record one patient’s daily fall-risk assessment at the bedside, plus a head-nurse screen showing today’s assessment status and risk levels.

Use made-up sample patients only in demos, screenshots, and development data. Do not use real patient details.

## Users

- **Ward nurse:** signs in, enters patient details, completes, reviews, and saves a daily assessment. Ward nurses do not get a saved-assessment correction control.
- **Head nurse:** signs in, reviews the ward’s assessment status for today, and can correct saved assessments.

## Visual direction

- Use **Concept 01 · Calm and structured** from `designs.html` as the selected visual direction for the assessment screen.
- Make the risk-factor descriptions and care-step labels larger than shown in the design preview, with clear, easy-to-read text for bedside phone use.

## Nurse workflow

1. Show a sign-in page on app launch. The user enters a name and chooses Ward nurse or Head nurse; the app uses that local profile for the current session and remembers it in this browser for the next sign-in.
2. Nurse enters ward, bed, date, patient name, and hospital number (HN) for the patient being assessed. The patient is entered each time; no patient roster was requested.
3. Nurse ticks all applicable risk factors.
4. App calculates and displays the risk level using the rules below.
5. Nurse ticks any care steps done: **Review medications**, **Check IV tubing**, **Monitor for changes**, and **Other** with a text field for a nurse-entered step.
6. Before saving, show a review screen with all entered answers and the calculated risk level; the nurse can go back and correct them.
7. On save, record the nurse’s name and automatically fill the assessment time with the current time.
8. For corrections, only the head nurse role can open a saved assessment. The correction review shows changed values in a distinct before/after color treatment before the head nurse confirms. Record the correcting head nurse’s name and reason.

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
- Care steps done: checkboxes for **Review medications**, **Check IV tubing**, and **Monitor for changes**, plus **Other** and a text field
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

1. How should the app know the full list of patients expected on the ward today so it can show who has not been assessed? The current choice to use assessment entries alone cannot identify patients with no entry.
2. Should date default to the phone’s current date, and can nurses record or amend an assessment for a different date?
3. What secure authentication and ward-access method should replace the local demo role selector before real patient data is used?

## Scope boundary

The plain HTML app is in `index.html`; it stores data in the current browser only. Its sign-in page selects a local name and role to control which correction controls are shown, but it is not secure authentication or access control. The requested care-step labels are **Review medications**, **Check IV tubing**, and **Monitor for changes**, plus **Other**. The roster workflow and remaining open items need ward confirmation.
