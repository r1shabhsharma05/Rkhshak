# Mobile App Design — native patterns, gestures, navigation

A mobile app is not a small website. It has its own patterns: thumbs, gestures, and navigation that a website never needs. Design for the phone in the hand, not the browser window.

## Navigation
- **Bottom tab bar (3–5 tabs max).** The primary navigation lives at the bottom, where the thumb is. More than 5 tabs is a menu, not navigation.
- **One primary action per screen.** A floating action button (FAB) or a bottom CTA — one, not three.
- **Back is a gesture, not just a button.** Swipe-back works everywhere. A screen that traps the user (no back, no close) is a bug.
- **Deep links land on content.** A link opens the thing it names, not the home screen. (Security: deep links are validated — see `security-audit`.)

## The thumb zone
- **Primary actions in the bottom half.** The top of the screen is for reading; the bottom is for doing. A primary button at the top of a tall phone is unreachable.
- **Touch targets ≥ 44px.** Fingers are bigger than cursors. A 24px target on mobile is a miss.
- **No hover states.** There is no hover on a phone. Anything that only appears on hover doesn't exist.

## Gestures
- **Standard gestures only.** Swipe to go back, pull to refresh, long-press for options, pinch to zoom. A custom gesture nobody knows is a hidden feature.
- **Every gesture has a visible alternative.** A swipe-to-delete also has a delete button. A user who doesn't know the gesture can still do the thing.
- **Undo, not confirm.** A destructive action (delete, archive) gets an undo snackbar, not a confirmation dialog. Undo is faster and kinder.

## Content + states
- **One column.** Mobile is one column. Two columns of dense content is a website squeezed into a phone.
- **Loading, empty, error, offline — all designed.** A phone loses signal. The offline state is a first-class screen, not a crash.
- **Safe areas respected.** Content never hides under the notch, the home indicator, or the status bar. The tab bar never overlaps the home indicator.

## Platform honesty
- **Follow the platform.** iOS patterns on iOS, Android patterns on Android. A bottom tab bar on iOS, a navigation drawer where Android expects one. Fighting the platform makes the app feel foreign.
- **System fonts, system components** unless the brand demands otherwise. A custom everything is a maintenance cost and a familiarity cost.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Bottom tabs ≤ 5, primary action reachable by thumb | Top navigation for primary actions, or 6+ tabs |
| 2 | Touch targets ≥ 44px | 24px targets on mobile |
| 3 | No hover-dependent UI | Something only appears on hover |
| 4 | Every gesture has a visible alternative | Swipe-only delete with no button |
| 5 | Destructive actions get undo, not confirm dialogs | A confirmation dialog for every delete |
| 6 | Offline state designed | App crashes or blanks on no signal |
| 7 | Safe areas respected (notch, home indicator) | Content hidden under the notch |
| 8 | Platform patterns followed | iOS app with Android navigation (or vice versa) |
