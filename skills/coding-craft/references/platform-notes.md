# Platform Notes — mobile feel, Swift, typed AI

Distilled from three sources, in our own words: mobile-native, write-swift (BSD/MIT), typesafe-ai (MIT). Full detail lives in those sources. Use when a web app must feel native on a phone, when writing Swift, or when integrating a typed AI decision model.

## Feeling native on mobile (web)
A website in a browser feels wrong on a phone for small, specific reasons. Fix the symptom, not the vibe:
- **Hover stuck after tap:** hover styles must not linger on touch — scope hover to devices that actually hover.
- **Gray or blue flash on tap:** remove the tap highlight where it fights the design.
- **Wrong height:** the viewport height changes as the browser chrome shows and hides — size to the real viewport, not a fixed number.
- **Page zooms into the input:** an input with a small font size triggers auto-zoom on focus; size inputs so it does not.
- **Tap feels laggy:** remove the tap delay; make the response immediate.
- **Pull-to-refresh hijacks scroll:** disable the gesture where the app handles scrolling itself.
- **Content stops at the notch:** respect the safe-area insets.
- **Long-press selects button text:** disable selection on controls.
- **Carousel scrolls vertically:** lock the scroll axis.
- **Status bar colour does not match:** set the theme colour to match the app.
- **Right in desktop Chrome, wrong on the phone:** verify on a real device or an accurate emulator — desktop emulation is not proof.
- **Baseline:** define the minimum acceptable mobile behaviour and check it on every change. Never ship a regression against the baseline.

## Writing Swift well
- **Model data with value types** first; reach for reference types only when identity or sharing demands it.
- **Make failure paths visible:** errors and optionals are explicit — no silent nils, no swallowed errors.
- **Concurrency:** stay single-threaded until profiling says otherwise. Swift 6 is strict about data races: main-actor-by-default, actors, task groups, `@concurrent` where it fits. Respect actor reentrancy — an `await` inside an actor can interleave with other work.
- **Sendable and sharing data:** only `Sendable` types cross concurrency boundaries; design the types so the compiler can prove safety.
- **Structured concurrency:** tasks in groups with clear lifetimes; never a detached task that outlives its purpose.
- **Protocols and generics:** `some` for an opaque single type, `any` for a truly dynamic one; prefer the narrower.
- **API design:** clarity at the point of use — the call site should read like a sentence.
- **Performance:** measure first, then choose. ARC and object lifetime matter; retain cycles are real bugs, not theory.
- **Testing:** Swift Testing by default; macros where they remove boilerplate without hiding intent.
- **Unsafe code and interop:** isolate it, document why it is needed, and keep it small.
- **Migrating to Swift 6:** one module at a time, with the strict checks on from the start — do not migrate with the checks off.

## Typed AI integration (TypeSafe)
For decision models that answer typed questions about text, images, or application state:
- **Design the state first:** what the model may read, what it must decide, what the code does with each answer.
- **Write the questions** as typed queries with clear criteria; a vague question gets a vague answer, typed or not.
- **Compose requests** from small, checkable pieces; read the answers against the criteria, not against a feeling.
- **Confidence is rarely the gate:** a high-confidence wrong answer is still wrong. Gate on the criteria, on agreement between independent checks, and on test cases — not on the confidence number.
- **Test with the live API:** when an answer looks wrong, check the input, the question wording, and the state it was given — in that order — before blaming the model. Record the yellow flags (repeated near-misses, systematic biases) and fix the question or the state, not the model.
