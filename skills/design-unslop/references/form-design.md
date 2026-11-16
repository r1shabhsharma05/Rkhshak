# Form Design — inputs, validation, and multi-step forms

Every app has forms. Most forms are where users give up. Design the form so the user finishes it.

## Rules
### 1. One question per line (mostly)
- One input per row, label above the input. Two columns only for fields that belong together (first/last name, city/ZIP). A form that looks like a tax return feels like one.
- Labels are always visible — never placeholder-only. A placeholder disappears the moment the user types, and then they can't tell what the field was.

### 2. Labels say what you need, placeholders show an example
- Label: "Phone number". Placeholder: "+91 98765 43210". The label is the instruction, the placeholder is the format.
- Never put the instruction in the placeholder. It vanishes.

### 3. Validation is inline, immediate, and kind
- Validate as the user types (or on blur), not only on submit. A user who fills 10 fields and gets 10 errors at the end will leave.
- Errors say what to do, not what went wrong: "Enter a 10-digit phone number" beats "Invalid input". The error sits next to the field, in text + an icon — never colour alone.
- Success is visible too: a checkmark when a field is right. The user should know they're making progress.

### 4. The submit button is honest
- The button says what happens: "Create account", "Send message", "Pay ₹499" — not "Submit".
- While submitting, the button shows it's working (spinner + "Creating…") and can't be double-clicked. A double-submit creates two accounts, two orders, two charges.
- After submit, show what happened: a success screen, a confirmation, or the next step. Never leave the user on the same form wondering if it worked.

### 5. Multi-step forms
- Break long forms into steps (3–5 max). Show progress ("Step 2 of 4") and what's in each step.
- Each step asks for one kind of thing (account → details → payment). Never mix.
- The user can go back without losing what they typed. A back button that wipes the form is a bug.
- Save progress if the form is long. A user who loses 10 minutes of typing will not start over.

### 6. Only ask for what you need
- Every field must have a reason. A field with no reason is deleted. "Company" on a signup form nobody uses is friction, not data.
- Optional fields are marked optional. If everything is required, the form is asking too much.

### 7. Mobile first
- Inputs are at least 44px tall, the keyboard matches the field (numeric for phone, email for email), autocapitalise off for emails and usernames.
- The form works at 360px with no horizontal scroll and no zooming to read a label.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Labels always visible, placeholders show format only | Placeholder-only labels |
| 2 | Validation inline + immediate, errors say what to do | All errors only on submit, or "Invalid input" |
| 3 | Submit button names the action, can't double-submit | "Submit" button, or double-click creates two records |
| 4 | Success state shown after submit | User left wondering if it worked |
| 5 | Multi-step: progress shown, back preserves data | No progress, or back wipes the form |
| 6 | Every field has a reason | A field nobody uses |
| 7 | Mobile: 44px inputs, right keyboard, no sideways scroll | Tiny inputs or wrong keyboard |
