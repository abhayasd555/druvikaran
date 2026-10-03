# Druvikaran (ध्रुवीकरण)

A browser game about polarisation. Light from a laser travels through a fibre into a three-paddle fibre polarisation controller (λ/4, λ/2, λ/4) and then a polarimeter, which plots the output on a Poincaré sphere. Rotate the paddles to steer the output onto the target before time runs out.

It's a single self-contained `index.html` with no build step and no dependencies. Open it in a browser, or serve it with GitHub Pages.

## Sanrekhan (संरेखण), the alignment game

`sanrekhan.html` is a classical optics game about beam walking. A laser reflects off two kinematic mirrors and has to pass through two small irises to reach a power meter. Each mirror has a horizontal and a vertical thumbscrew (Mirror 1: A/D, S/W; Mirror 2: J/L, K/I). Every turn moves the spot on both irises, so the trick is to iterate: mirror 1 centres the beam on the near iris, mirror 2 on the far one. Hold the power above 90% of the best possible for a second to lock. Levels shrink the irises and shorten the clock, and from level 3 the beam drifts.

## Sanyojan (संयोजन), the combining game

`sanyojan.html` is about overlapping two lasers on a dichroic mirror. The red 633 nm beam passes straight through and is the fixed reference. The green 532 nm beam reflects off a steering mirror and then the dichroic, and you steer it with both mounts (steering mirror: A/D, S/W; dichroic: J/L, K/I) until it lies on top of the red beam at a near and a far camera. Where the spots overlap they add to yellow. The score is the Gaussian mode overlap at both cameras; hold it above 90% for a second to lock. Tilting the dichroic also shifts the transmitted red beam slightly, as a real glass substrate does. From level 3 the red reference drifts.

## Tantu (तंतु), the fibre coupling game

`tantu.html` is about launching a laser into a single-mode fibre. Two mirrors steer the beam into an 11 mm lens that focuses it onto a fibre with a 2.2 µm mode radius, and a power meter reads what comes out the far end. Coupling depends on three things at once: where the focused spot sits on the core, the beam's angle (set by where it crosses the lens), and focus. Mirror 1: A/D, S/W; mirror 2: J/L, K/I; fibre focus: F/R. An end-face view helps you find the core; after that only the power meter and its 12-second trace guide you, and the angle has to be fixed by walking the beam with both mirrors. Lock by holding the power above the level's target.

## Vyatikaran (व्यतिकरण), the interference lab

`vyatikaran.html` is an untimed interference bench with six experiments: single slit, Young's double slit, a diffraction grating, and Michelson, Mach–Zehnder and Sagnac interferometers. Everything is adjustable: laser pointing, mirror tilts, a delay stage with a piezo, slit sizes, polarisers and wave plates, and the screen's distance (drag it along the rail or type it in millimetres). Slits use exact Fresnel diffraction, so the pattern changes from near field to far field as the screen moves; interferometers add two Gaussian beams with their real offsets, tilts, curvatures, path lengths, polarisations and the source's coherence length.

The screen updates live with an intensity profile, visibility, contrast and measured against predicted fringe period, and interferometers have a delay scan. Sources include HeNe, green, violet and 810 nm lasers and a white LED. After aligning with a laser you can swap in heralded single photons (810 nm, 3 or 10 nm filter): detections build the pattern one by one, visibility is fitted with an uncertainty, and a heralded g⁽²⁾(0) measurement shows they are single photons. A Help tab diagnoses what's wrong with the current setup, says what to move and by how much, offers one-click fixes, and keeps a self-ticking checklist of alignment steps.

## Tomography lesson

`tomography.html` is a learning page rather than a game. It walks through two-photon polarisation state tomography in six sections: prepare an entangled state (or a hidden mystery state), choose analyser settings, collect simulated coincidence counts with shot noise and accidentals, then reconstruct the density matrix by linear inversion and by maximum likelihood, and compare fidelity, purity and concurrence with the true state.

## How to play

Each round, the fibre scrambles the input polarisation at random and a new target appears on the sphere. Hold the output (red) inside the target ring (violet) for 0.8 s to lock it. Every level shortens the clock and shrinks the ring. Free practice mode has no timer.

| Paddle | Waveplate | Keys |
|---|---|---|
| 1 | λ/4 | Q / A |
| 2 | λ/2 | W / S |
| 3 | λ/4 | E / D |

Hold a button or key to rotate a paddle, or tap it for a small step. Hold Shift (or turn on "Fine control") for slow rotation. Drag the sphere to change the view.

## The trick

A paddle at angle θ rotates the Stokes vector about the equatorial axis (cos 2θ, sin 2θ, 0). A λ/4 paddle turns it by 90° and the λ/2 paddle by 180°. Read the target's azimuth ψ from the readout, then:

1. Set paddle 3 to the target's ψ. The target now lies on the great circle through the poles that paddle 3 maps linear light onto.
2. Turn paddle 1 until the output reaches that circle, which happens when the output ψ equals the target ψ (or differs by 90°). This step depends on paddle 1 alone.
3. Turn paddle 2 to slide the output along the circle onto the target. It moves at 4× the paddle angle, so use fine control.

Setting all three paddles to the same angle makes the controller act as the identity, which shows you the raw input state.

## Model

Each paddle is an ideal fixed-retardance waveplate with its fast axis at θ ∈ (−90°, 90°] around the fibre. The output is the input Stokes vector rotated by paddle 1, then paddle 2, then paddle 3. The S₃ > 0 hemisphere is labelled right-circular. Real paddles have limited travel (about ±117° on common controllers), and fibre after the controller adds its own birefringence. Neither is modelled here.
