---
name: app-motion-and-animation
description: Platform-agnostic motion principles for any app — the six purposes of motion and when NOT to animate, the perception thresholds (~100ms instant, 230ms perceive, 80ms floor / 500ms ceiling), duration scales and named easing curves (standard/decelerate-entrance/accelerate-exit), spring physics and the modern duration+bounce model, choreography (stagger, shared-element, asymmetric enter/exit, anticipation/follow-through), 60/120fps performance rules, and reduced-motion/vestibular accessibility, with a compact duration-by-interaction reference. Use when deciding whether an interaction deserves motion, picking a duration/curve, choreographing a transition, or auditing animation for jank or accessibility.
tags: [motion, animation, ux, interaction, principles]
---
# App motion & animation — why, when, and how much

Source: **Material Design 3** motion (easing & duration tokens, spring schemes) + **Material 1/2** standard curves, **Apple HIG → Motion** + **WWDC23 "Animate with springs"** (`spring(duration:bounce:)`), **IBM Carbon** (productive vs expressive) + **Salesforce Lightning / Kinetics**, **Disney's 12 principles** as applied to UI (Val Head, *Designing Interface Animation*), and **WCAG 2.3.3** + `prefers-reduced-motion`. Cross-checked across these systems (June 2026). The through-line every system agrees on: **motion is functional first — it explains a change; it is not decoration.**

## 1. Why motion exists (the six jobs) — and when NOT to animate
Animate only when it does one of these jobs. If none apply, cut it.
- **Orient** — show where a thing came from / went to (a sheet rises from the button that summoned it).
- **Feedback** — confirm an input registered (tap → press-down, toggle → slide). The most valuable 100ms in the app.
- **Continuity / spatial relationship** — preserve object identity across a change so the user doesn't re-parse the screen (list row morphs into detail).
- **Status** — communicate ongoing/indeterminate work (progress, loading, sync).
- **Focus / direction of attention** — pull the eye to the one thing that changed (a new badge, an error).
- **Delight** — personality at a *milestone*, never on a routine action. Rare by definition.

**Do NOT animate:** high-frequency repeated actions (typing, scrolling content, list reordering the user drives), anything on the critical path to a result the user is waiting for (don't gate data behind a 400ms flourish), destructive-action confirmations (be instant and clear), or motion that fires on every keystroke/poll. **If it plays more than a few times per session and isn't feedback, it will annoy.** When unsure: ship it static, add motion only where the static version feels confusing or abrupt.

## 2. Perception science — the numbers that bound everything
These are human-perceptual constants, not style preferences:
- **~80–100ms = "instant."** RAIL/NN-group: a response under ~100ms feels like direct manipulation. Below ~**80ms an animation reads as a glitch/flicker** — the user can't perceive it as motion, so skip the tween and just change state.
- **~230ms = time to visually perceive + register** a change (Model Human Processor). This is why sub-200ms animations can feel "snappy but barely there," and why 200–300ms is the comfortable home for most UI.
- **>~500ms on a phone = sluggish.** The interface feels like it's waiting on *you*. Reserve >500ms only for large, full-screen, or first-run/celebration moments.
- **~1s = upper limit of flow-of-thought.** Past this, attention wanders; never block interaction this long for a transition.
- **60fps (16.7ms/frame) is the smoothness floor; 120fps (8.3ms) on ProMotion/high-refresh.** Humans detect dropped frames and variable frame rate easily — *consistent* 60 beats *jittery* 90.

## 3. Duration scales
Faster for small/local changes, slower for large/distant ones — **duration should scale with how far or how much an element moves** (Carbon's explicit rule; Material's size buckets). Enter slower than exit (§5).

| Tier | Range | Use |
|---|---|---|
| **Micro** | 100–200ms | hover, press, toggle, checkbox, small fades, icon state |
| **Standard** | 200–300ms | most transitions: cards, menus, tabs, inline expand/collapse, snackbars |
| **Large / complex** | 300–500ms | full-screen / page / sheet transitions, shared-element morphs, multi-property |
| **Expressive / milestone** | 500–1000ms | onboarding hero, celebration, first-run — sparingly |

**Material 3 duration tokens** (verbatim): short1 50 · short2 100 · short3 150 · short4 200 · medium1 250 · medium2 300 · medium3 350 · medium4 400 · long1 450 · long2 500 · long3 550 · long4 600 · extra-long1–4 700/800/900/1000ms. **Apple HIG** lands the same: enter ~225ms, exit ~195ms, full-screen ~375ms. **Carbon** splits *productive* (fast, utilitarian micro-interactions) from *expressive* (slower, gentler — for system-initiated interruptions like notifications). Pick one default scale and reuse it; ad-hoc per-component durations are the #1 "uncoordinated" tell.

## 4. Easing / curves — the shape of time
**Never use `linear` for anything that moves position or size** — real objects have mass, so they accelerate and decelerate. Linear is only correct for **continuous/looping** motion (spinners) and **non-spatial** property changes (color, opacity) — Salesforce's rule: *"ease-out for things that move, linear for things that don't."*

| Curve | cubic-bezier | When |
|---|---|---|
| **Standard** (ease-in-out, asymmetric) | `(0.4, 0, 0.2, 1)` | on-screen → on-screen moves; the everyday default. Decelerates longer than it accelerates. |
| **Decelerate / entrance** (ease-out) | `(0, 0, 0.2, 1)` | elements **entering** the screen. Arrive fast, settle gently. **The most important curve** — entrances should ease-out. |
| **Accelerate / exit** (ease-in) | `(0.4, 0, 1, 1)` | elements **leaving** the screen. Start gently, fly off fast — no need to watch it land. |
| **Sharp** | `(0.4, 0, 0.6, 1)` | temporary elements that may return (a menu snapping shut). |

**Why ease-out for entering:** the element decelerates *into* its resting place, which matches how the eye expects an arriving object to settle and keeps attention on the destination, not the motion. Ease-in (accelerate) on an entrance feels like it's running away from you.

**Material 3 "emphasized"** curves add personality on hero/large transitions (longer, more pronounced deceleration): emphasized-decelerate `(0.05, 0.7, 0.1, 1)`, emphasized-accelerate `(0.3, 0, 0.8, 0.15)`. Use the standard set for utility, emphasized for key moments.

## 5. Asymmetric enter/exit (do this everywhere)
Entrances and exits are **not** mirror images:
- **Enter:** slightly **longer**, **decelerate** curve — the user needs time to register the new thing and where it is.
- **Exit:** slightly **shorter**, **accelerate** curve — the thing is gone; don't make them wait for it. (HIG ~225 in / ~195 out.)
Reusing one symmetric ease-in-out for both is a subtle amateur tell. The asymmetry is what makes navigation feel "right."

## 6. Spring physics
Springs replace fixed duration+curve for anything **interruptible, gesture-driven, or that should feel physical** (a card you fling, a sheet you drag, a toggle). They carry velocity through, so an animation interrupted mid-flight continues naturally instead of snapping — curves can't do that.

- **Classic parameters:** *stiffness* (how hard it pulls to rest — higher = faster/snappier), *damping* (friction that kills oscillation — higher = less bounce), *mass* (inertia — higher = slower, heavier). These are powerful but unintuitive to tune by hand.
- **Modern parameterization (prefer this):** **duration + bounce**, as in SwiftUI's `spring(duration:bounce:)` (WWDC23). *duration* is a **perceptual** settle time (~0.5s default) that stays stable as you change bounce; *bounce* runs **0 → 1** (0 = no overshoot / smooth, ~0.15–0.3 = lively, higher = playful, springy). This maps directly to designer intent — set roughly how long and how bouncy, done.
- **Spring vs curve:** spring for **interactive/continuous/physical** (drag, fling, anything that can be interrupted); curve for **discrete, one-shot, precisely-timed** transitions (a fade, a scheduled reveal). MD3's Expressive scheme is spring-based by default; its Standard scheme keeps near-zero bounce for utilitarian products.

## 7. Choreography & orchestration
- **Stagger:** when many items enter (a list, a grid), offset each by a small delay (**~20–50ms**, total cascade capped ~**200–300ms**) so the eye reads order instead of a wall of simultaneous motion. Don't stagger more than ~5–8 visible items — beyond that, animate as a group.
- **Shared-element / continuity transition:** the single highest-value technique. A persistent element (thumbnail, title, FAB) physically moves/morphs from screen A to its position on screen B, so identity is preserved and the user never loses context. This is what makes a navigation feel like one space instead of a slideshow.
- **Anticipation** (Disney): a tiny opposite/wind-up move before the main action (a button dips *in* before a panel springs *out*) primes the eye for what's coming. Use sparingly on key actions.
- **Follow-through & overlapping action** (Disney): elements don't all stop dead together — secondary parts settle slightly after the leader, and a fast object can overshoot and settle back. This (and a touch of spring bounce) is what reads as "alive" vs "robotic."
- **Squash & stretch / weight:** even subtle scale-on-press (0.96–0.98) gives an element mass and makes a tap feel tactile.
- **One focal point:** a transition should have a clear protagonist. If three regions animate independently at once, the user doesn't know where to look — sequence or unify them.

## 8. Performance — animate cheap properties only
The browser/renderer is cheapest when it can move pre-painted layers on the GPU:
- **Animate only `transform` (translate/scale/rotate) and `opacity`.** These are **compositor-only** — no layout, no repaint — and hit 60/120fps even on weak hardware.
- **Avoid animating layout/paint properties:** `width/height/top/left/margin`, `box-shadow`, `background-color`, `filter`, `border-radius` — each forces re-layout or re-paint every frame and causes jank. Need a size change? Animate `scale`. Need to move? Animate `translate`, not `top/left`. (On iOS the same rule holds: SwiftUI/Core Animation are cheap on transform & opacity; animating expensive layout is the usual culprit when a transition stutters.)
- **Jank causes:** layout thrash (read-then-write geometry in a loop), animating during heavy main-thread work (parse, decode, big list diff), too many simultaneously animating layers, oversized images/blurs. Keep work off the main thread; promote animating elements to their own layer; profile with the frame/performance tools, don't guess.
- **Target the device:** assume 60fps as the contract, 120fps where available — and never design motion that *requires* a high-end GPU to not stutter.

## 9. Accessibility — non-negotiable
- **Honor reduced-motion** (`prefers-reduced-motion: reduce` / iOS **Reduce Motion** / Android Remove animations). This is a real user need (vestibular disorders → motion can cause **dizziness, nausea, migraine**), not a preference to ignore. **WCAG 2.3.3 Animation from Interactions (AAA):** non-essential motion triggered by interaction must be disable-able.
- **Vestibular triggers to kill under reduced motion:** large **parallax**, big **zoom/scale** transitions, **spin/rotation**, fast **slide** across large distance, anything full-screen and sweeping.
- **Safe fallback = crossfade.** Replace slide/zoom/parallax with a simple **opacity** crossfade (or instant change). Apple's explicit guidance: under Reduce Motion, swap sliding transitions for crossfades and drop autoplay/parallax. **Don't ship zero feedback** — keep the essential state change, just remove the spatial/scaling drama. Functional feedback (a thing turned on) stays; gratuitous travel goes.
- Never **autoplay** looping motion the user didn't trigger; never convey information by motion alone (pair with a static cue).

## 10. Mistakes that read as cheap / amateur
- **Linear easing on spatial motion** — the instant "this was made by an engineer not a designer" tell.
- **Everything 300ms, everything symmetric** — no enter/exit asymmetry, no duration scaling by size.
- **Animating layout/`box-shadow`/`background`** → visible jank/stutter.
- **Bounce on serious/utilitarian UI** — spring overshoot on a delete confirmation or a form error feels flippant.
- **Motion on the critical path** — gating data the user is waiting on behind a flourish.
- **Over-animation** — every element fading/sliding on every screen load; motion everywhere = motion nowhere. Restraint reads as premium.
- **No reduced-motion path** — accessibility failure and an App Store / WCAG risk.
- **Decorative loops** that never stop, and transitions with no clear focal point (3 things animating at once).

## Reference table — duration + easing by interaction
| Interaction | Duration | Easing | Notes |
|---|---|---|---|
| Press / tap feedback | 100–150ms | ease-out / decelerate | scale 0.96–0.98 + opacity; instant-feeling |
| Toggle / switch / checkbox | 150–200ms | standard or low-bounce spring | a little spring bounce reads tactile |
| Hover (pointer) | 100–150ms | standard | desktop/iPad only |
| Small fade / inline reveal | 150–200ms | ease-out (in), ease-in (out) | |
| Menu / popover / dropdown | 200–250ms | sharp (returns) | exit faster than enter |
| Card / list-row → detail | 250–350ms | standard / shared-element | morph identity if possible |
| Tab / segment switch | 200–250ms | standard | crossfade content; slide indicator |
| Sheet / modal present | 300–400ms | decelerate (in) / accelerate (out) | spring if drag-dismissable |
| Full-screen / page transition | 300–500ms | standard or emphasized | longest acceptable on phone |
| Snackbar / toast in-out | 200ms in / 150ms out | ease-out / ease-in | auto-dismiss; never block |
| Progress / loading loop | continuous | **linear** | the one place linear is correct |
| List/grid stagger | 20–50ms/item, ≤300ms total | decelerate | cap visible items |
| Celebration / milestone | 500–1000ms | emphasized / springy | rare; reduced-motion → static |
| **Reduced motion (all of above)** | ≤150ms or instant | **crossfade / opacity** | strip travel, keep the state change |

## Greg application
Greg is a native SwiftUI iOS 26 nutrition app (cobalt #2C50F0 + Figtree, color-blocked macro tiles, Progress screen for metrics). Spend motion where it does a job; keep the log loop fast and undramatic.
- **Calorie ring fill (Progress):** animate the ring's `trim`/stroke with a **decelerate or low-bounce spring** when the daily total updates — it earns motion because it shows *progress toward a goal* (status + focus). Keep it **~300–400ms, bounce ≤0.15**; the number counts up with `.contentTransition(.numericText())` + `.monospacedDigit()`. Under Reduce Motion: snap the ring, crossfade the number — no sweeping arc.
- **Log-confirm feedback (the hot path):** logging food happens dozens of times — make it **fast and tactile, not flashy**. Row commits in **~150–200ms** (press scale 0.97 → settle), a brief checkmark, success haptic. **No celebratory animation on a routine log** — that's the over-animation trap.
- **Macro tiles updating:** when a log changes today's macros, the affected tile's value does a quick numeric transition + subtle scale-settle (**~200ms, standard**); don't re-animate all tiles together — animate only the one that changed (single focal point).
- **Adaptation card (plan→adapt):** this is a *meaningful* moment — the plan responding to reality. Use a **shared-element / continuity** feel: the card expands in place with an **emphasized-decelerate ~350–400ms**, content staggered ~30ms, so it reads as "the plan is adapting," not a generic modal. Reduced-motion: crossfade in, no expand.
- **Streak celebration (milestone):** the rare place delight is licensed. A **500–700ms springy** moment (bounce ~0.3) on hitting a streak — fires once per milestone, never on every open. Reduced-motion: a static celebratory state, no confetti/spin (vestibular-safe).
- **Don't animate:** food-search results list as you type (instant), scroll content, settings toggles beyond their native 180ms, anything blocking the logged value from appearing. **Audit:** flip on Reduce Motion in the simulator and confirm every flow still communicates with crossfades only.

Pairs with: `ios-motion-and-animation` (SwiftUI implementation — Animation APIs, springs, transitions), `interaction-and-motion` (web/CSS implementation — view transitions, scroll-driven, `linear()`, `@starting-style`), `ios-gestures-and-haptics` (gesture-driven motion + haptic pairing), `accessibility-and-inclusive-design` (full reduced-motion / vestibular guidance).
