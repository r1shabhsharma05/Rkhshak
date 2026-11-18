# Motion Vocabulary — the exact term for a described effect

Distilled from the animation-vocabulary skill (a reverse-lookup glossary; terms are the standard names, wording is our own). Use when the user describes a motion effect without knowing its name and wants the right word — to prompt a designer or an agent with. For naming an effect, not designing or building one.

## How to use it
Match the user's description to a family, then to a term. Give the term, one line of what it is, and stop. If two terms fit, say which one fits better and why. Never invent a term — if none fits, say so.

## Entrances & exits — how elements appear and disappear
| Term | What it is |
|---|---|
| Fade in / Fade out | Opacity only, no movement |
| Pop in | Scale from ~0.95 + opacity, quick and snappy |
| Slide in | Translates from an edge into place |
| Rise / Drop in | Slides up (or down) a short distance while fading in |
| Scale in | Grows from a smaller scale (never from 0) |
| Clip reveal | Revealed by an animated `clip-path`, like a curtain lifting |
| Stagger in | A group enters one after another, 30–80ms apart |
| Dismiss / Exit | The reverse of its entrance, along the same path |

## Sequencing & timing — coordinating multiple elements
| Term | What it is |
|---|---|
| Stagger | Sequential delays across a group |
| Cascade | A stagger that follows a path (down a list, across a grid) |
| Choreography | Multiple elements moving as one composed sequence |
| Orchestration | Entrance, content, and exit timed as a single story |
| Scrub | Motion driven 1:1 by scroll position |
| Pin / Pinned section | Content held in place while the scroll drives change inside it |

## Movement & transforms — changing position, size, or angle
| Term | What it is |
|---|---|
| Translate | Move along x/y without changing size |
| Scale | Grow or shrink (children scale too) |
| Rotate | Turn around an axis |
| Skew | Slant along an axis |
| Flip | A 180° rotation that swaps one face for another |
| Morph | One shape becoming another |
| Parallax | Layers moving at different rates with scroll or pointer |

## Transitions between states — connecting one state, view, or element to another
| Term | What it is |
|---|---|
| Crossfade | One state fades out as the next fades in |
| Shared-element transition | One element moves and resizes between two screens, keeping its identity |
| Layout animation | An element animates to its new layout position when the layout changes |
| FLIP | First–Last–Invert–Play: measure, then animate the difference |
| View transition | The platform's built-in cross-document transition |
| Morphing transition | A control grows into the view it opens |

## Scroll — motion tied to scrolling
| Term | What it is |
|---|---|
| Scroll reveal | Content enters as it scrolls into view, once |
| Scroll-linked / scrubbed | Motion progress bound to scroll progress |
| Sticky / pinned | An element that stays while the rest scrolls |
| Progress spine | A rule or bar that fills with scroll progress |

## Feedback & interaction — responding to the user
| Term | What it is |
|---|---|
| Press | The 0.97-scale + opacity response to a tap or click |
| Hover lift | A small rise on hover (pointer devices only) |
| Ripple | A spreading circle from the touch point |
| Shake | A short horizontal oscillation for an invalid input |
| Pulse | A repeating scale/opacity cycle (use only for genuinely live things) |
| Haptic | A vibration that confirms an action |

## Easing — how speed changes
| Term | What it is |
|---|---|
| Ease-out | Fast start, gentle stop — entrances |
| Ease-in | Slow start, fast stop — almost never right for UI |
| Ease-in-out | Slow at both ends — movement on screen |
| Linear | Constant speed — progress, marquees |
| Spring | Physics-based, overshoots and settles |

## Spring animations — physics-based motion
| Term | What it is |
|---|---|
| Damping ratio | Controls overshoot; 1.0 = no bounce |
| Response | How quickly the value reaches the target |
| Overshoot | Passing the target and settling back |
| Bounce | Repeated overshoot before settling |
| Velocity handoff | The animation continuing from the gesture's release velocity |
| Rubber-banding | Resistance that grows as a drag passes its limit |

## Looping & ambient motion — animations that run on their own
| Term | What it is |
|---|---|
| Loop | Repeats indefinitely |
| Idle animation | Subtle motion on an element at rest (use sparingly — usually delete) |
| Drift | A slow, continuous positional move |
| Marquee | Content scrolling in a loop |

## Polish & effects — the small touches
| Term | What it is |
|---|---|
| Blur mask | A brief blur hiding a transition seam |
| Skeleton | A placeholder shape shown while content loads |
| Shimmer | A moving highlight over a skeleton (use sparingly) |
| Number tick / count-up | A number animating to its value |

## Principles to know
| Term | What it is |
|---|---|
| Interruptibility | Motion that retargets cleanly from its current value |
| Spatial consistency | An element keeps its identity and origin through a transition |
| Reduced motion | Fewer and gentler animations, never zero comprehension |
| Compositor thread | Where `transform`/`opacity` animations run, off the main thread |
