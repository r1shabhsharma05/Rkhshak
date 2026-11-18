# WebGL 3D — Three.js only with purpose

Distilled from the Three.js usage playbook (Three.js, MIT, mrdoob/three.js). Method in our own words; the playbook's install and API details live in that source. Use when a page earns a 3D scene — a product viewer, a WebGL hero background, scroll-driven 3D — and never as ornamental background noise.

## When 3D earns its place
Spatial depth, texture transition, displacement, or pointer response that materially supports the art direction. One clear responsibility, subordinate to content. If the scene can be removed without the page losing meaning, remove it.

## Minimal scene (the shape every 3D piece starts from)
Scene + camera + renderer + one light set + the object. Resize handler updates `camera.aspect` and `renderer.setSize`. Cleanup on unmount disposes the renderer and removes the canvas. Nothing else is added until the scene needs it.

## Loading models
Load `.glb` models with the GLTF loader; keep the loader, the model URL, and the fallback in one place. A model that fails to load shows the static poster, never a blank canvas and never an error to the user.

## Shaders and post-processing
Custom shaders and post-processing are one effect each, budgeted like any other motion: one shader pass that carries the idea, not a stack of them. Cap the work — heavy shader scenes get a lower pixel-ratio cap.

## Performance rules
- **Cap pixel ratio at 2** (1.75 on heavy shader scenes). Reuse geometries and materials; dispose of anything removed.
- **Pause rendering** when the canvas is offscreen (IntersectionObserver) or the tab is hidden. No continuously animated offscreen content.
- **Throttle pointer input.** Pointer-driven scenes sample the pointer at a bounded rate; the scene never re-renders per mousemove event without a throttle.
- **`prefers-reduced-motion`:** render a composed static frame (or a slow idle rotation) instead of continuous motion — never a blank canvas. WebGL failure gets the same static poster.
- **Static first frame:** the design is complete without WebGL. The canvas is additive, never required.

## Taste rules
- The scene supports the art direction; it does not replace it. A 3D background behind a weak layout is still a weak layout.
- One 3D responsibility per page. A viewer and a hero background on the same page compete; pick one.
- Credit the model and texture sources in the footer, like any other asset.
