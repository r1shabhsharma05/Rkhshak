# Screen Templates — unslop rules per screen

Shapes and themes set the system. These templates set the rules for the screens every product has. Apply the template's rules on top of the 9 passes — they are the screen-specific tells.

## Login / Signup
- One primary action, one secondary (e.g. "Continue with Google"). Never a wall of social buttons.
- The form sits IN the material, not beside a picture panel. No picture panel beside a form column.
- Password field shows its rules (not hidden in a tooltip). "Forgot password" is visible, not buried.
- Errors are inline, next to the field, in plain language. Never a generic "Login failed" with no reason.
- No greeting headline. The title names the context ("Log in to Acme").
- Social login buttons use the real brand colors (Google multicolor, etc.) — never grey logos.
- After login, the user lands where they were going, not on a generic dashboard.

## Dashboard / App screen
- Neutral surfaces. Color lives in the content (charts, status, data) — not in the chrome.
- Navigation is the densest part (rows 32–36, 2–4 between). One column for icons, labels on one line.
- Numbers right-align, one number format, `tabular-nums`. Stat cards are numbers — no sparklines or icons to fill them. One main chart, one accent per chart.
- Empty states are real (see `content-states.md`) — a dashboard with no data shows what to do next, not a blank grid.
- The moment is content (real data, drawn with care) — not a decorative hero on a working screen.

## Settings
- Grouped by proximity, not dividers. Space inside a group is smaller than space between groups.
- Every setting shows its current value (not just its name). Toggles show their state clearly.
- Destructive actions (delete account, revoke access) are separate, clearly marked, and ask for confirmation. Never next to a harmless toggle.
- No settings page is a wall of identical rows — group, prioritize, and show what matters first.

## Pricing
- The price is the offer — set it big if it is the signature. Show price, billing period, auto-renewal, and how to cancel next to the pay button.
- One highlighted plan at most (not three "most popular" badges). The highlight is earned (the plan most users pick), never invented.
- Feature lists compare honestly — no checkmarks on features a plan doesn't have, no invented limits.
- A working cancel option exists and is findable. Never hide cancellation.

## Checkout / Payment
- The total is always visible. No surprise fees at the last step.
- One primary action ("Pay ₹X"). The amount is in the button.
- Errors are specific ("Card declined — try another card", not "Payment failed").
- Success confirms specifically ("Paid ₹499 — receipt sent to aisha@example.com") and shows the next step.
- Never a success page with nowhere to go.

## Onboarding
- At most 3 steps. Each step does one thing. Progress is shown (step 2 of 3), not hidden.
- Skip is always visible and honest (skipping doesn't break the product).
- The first screen after onboarding shows real value immediately — never an empty dashboard with a "now go do things" message.
- No onboarding that asks for information the product doesn't need yet.
