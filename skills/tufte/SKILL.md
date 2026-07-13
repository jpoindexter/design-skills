---
name: tufte
description: "The complete Edward Tufte canon (VDQI, Envisioning Information, Visual Explanations, Beautiful Evidence, Seeing With Fresh Eyes) as one skill — apply when designing, reviewing, or auditing any chart, dashboard, data graphic, statistical graphic, table, map, timetable, diagram, or slide deck; covers graphical excellence and integrity (Lie Factor), data-ink ratio and chartjunk removal, data density, small multiples, sparklines, micro/macro readings, layering and separation, color for information, typography for data, causal and analytical design, evidence corruption, links/arrows, mapped pictures, confections, and PowerPoint cognitive-style critique."
---
# Tufte — The Complete Canon

Consolidated from 27 single-topic skills. Sources: *The Visual Display of Quantitative Information* (VDQI, 1983/2001), *Envisioning Information* (EI, 1990), *Visual Explanations* (VE, 1997), *Beautiful Evidence* (BE, 2006), *Seeing With Fresh Eyes* (SWFE, 2020). One `##` section per source concept.

---

## Graphical Excellence (VDQI ch. 1)

Quality = true ideas delivered per unit of viewer time, ink, and space. Five criteria (all constraints — failing one disqualifies):
1. **Substance + statistics + design** together; none compensates for another.
2. **Clarity, precision, efficiency.**
3. **Maximum ideas, minimum time/ink/space.**
4. **Multivariate by default** — "Graphical excellence is nearly always multivariate."
5. **Truth** — distortion voids everything else.

**Four exemplary forms:** data maps (densest — U.S. cancer atlas: 3,056 counties on one map; Snow's cholera map), time-series (>75% of published graphics 1974–80; reserve for genuinely variable data), narrative graphics of space-and-time (Minard, Marey), relational/scatterplot ("the greatest of all graphical designs"; ~40% of scientific graphics).

**Minard's Napoleon map** — "may well be the best statistical graphic ever drawn" — six variables in one band: army size (width), longitude, latitude, direction (color), temperature (linked lower graph), time (dates).

**Graphics vs. tables:** small N, labeled, non-comparative → table. Large N, multivariate, comparative, pattern-driven → graphic (NYC weather chart: 1,888 numbers in one display). Playfair invented the modern forms (line/bar 1786, pie 1801); the oldest known time-series is a 10th–11th-c. planetary-orbit manuscript graph.

**Named failure modes:** substance failure (data too thin to deserve a graphic), decoration failure, univariate failure, distortion, chronological confusion (time-series read as causal), table-as-graphic, blot-map problem (area shading weights geography not population).

**Pre-publish checklist:** interesting/complex enough for a graphic? ≥2 variables? Cold viewer reads it in 10–30s? Every mark data-bearing? High density? Lie Factor ≈ 1.0? Reveals more than a single statistic? Right form (map / time-series / space-time / scatterplot)?

---

## Graphical Integrity & the Lie Factor (VDQI ch. 2)

```
Lie Factor = (size of effect shown in graphic) / (size of effect in data)
```
Effect size = % change. Honest band: **0.95–1.05**. >1.05 overstates; <0.95 understates; **2–5 is routine in the popular press; >10 falsifies the news in the data**. Compare over- vs. under-statement via logarithms of Lie Factors.

Tufte's two published computations: fuel-economy NYT 1978 graphic (data +53%, ink +783% → **LF 14.8**); Shrinking Family Doctor LA Times 1979 (**LF 2.8**, before perspective distortion).

**Six principles of graphical integrity:**
1. Marks proportional to the quantities represented (no scaled pictograms, perspective, truncated baselines).
2. Clear, detailed labeling on the graphic itself; annotate key events.
3. **"Show data variation, not design variation."** (no mid-chart scale changes, irregular intervals).
4. Money over time: **deflated and standardized (per-capita, constant-$) units beat nominal**.
5. Information-carrying dimensions ≤ dimensions in the data (no 2-D/3-D icons for a scalar).
6. **"Graphics must not quote data out of context."**

**Dimension trap:** value doubles → icon scaled in both dimensions reads +300% (LF 3.0); as volume +700% (LF 7.0). 1-D data gets 1-D ink: length/position on a common scale.

**Context — "compared to what?":** Connecticut traffic deaths: two-year before/after looks dramatic; full series shows normal swings; add neighboring states and the "effect" vanishes. Check baseline cherry-picking, pre/post trend, comparable groups.

**The "right direction" defense fails:** numbers carry magnitude, not just order; distortion can even reverse the story (nominal boom = real cut).

**Audit protocol:** compute the Lie Factor; one continuous scale; equal time steps = equal width; visual dims ≤ data dims; no perspective; money deflated + per-capita; every axis/unit/base labeled + source printed; events annotated; enough context/controls; neutral aspect ratio.

---

## Data-Ink Ratio (VDQI ch. 4)

```
data-ink ratio = data-ink / total ink
              = 1.0 − proportion erasable without loss of data-information
```
Work from the erasure form: hunt what can be deleted with zero information loss. Data-ink = "the non-erasable core... non-redundant ink arranged in response to variation in the numbers."

**Three ink classes:** data-ink (keep — changes when data changes), non-data-ink (frames, shading, grid mesh — erase first), redundant data-ink (bar fill, bilateral symmetry, duplicate axes — erase second). A shaded labeled bar encodes its one value ~6 ways (left edge, fill, right edge, top edge, printed number position, printed number).

**Five principles of graphical redesign, in order:** (1) Above all else show the data. (2) Maximize the data-ink ratio, within reason. (3) Erase non-data-ink. (4) Erase redundant data-ink. (5) Revise and edit.

**Two-pass erasure:** Pass 1 — background fills, grids/tick mesh, box frames (drop top+right at minimum), decorative borders, 3-D/shadows. Pass 2 — bar/area fill, mirrored halves (box plots, Chernoff faces), duplicate labels, second same-variable axis. Spend recovered space on direct labels or marginal distributions, not air.

**Convert non-data-ink to data-ink:** range-frame (axis drawn only min→max — the frame reports the range); dot-dash-plot (one tick per observation = marginal distributions replace regular ticks); direct labels where the grid was.

**Named redesigns:** box plot → quartile plot; solid bar → open bar → single line + top tick; range-frame scatterplot; half Chernoff faces.

**Justified redundancy:** cyclical wrap-around (Marey's train schedule repeats a cycle at the edges for continuous reading), orientation/navigation aid. Test: does the redundant ink help the reader *move through* the data, or merely restate a number? Restate → erase. Stop erasing when the next cut costs legibility — "within reason."

**Ratio killers, ranked:** full grid mesh; bar/area fill; 3-D perspective; bilateral symmetry; duplicate axis labels; four-sided frame; background fill.

---

## Chartjunk (VDQI ch. 5)

Three kinds — vibrations, grids, ducks. "Forgo chartjunk, including moiré vibration, the grid, and the duck."

**Vibrations (moiré):** crosshatch/hatching/dot-screen fills make the eye see shimmer that isn't data. Worst in software default fills. Bertin's "controlled moiré" rejected — no statistical graphic gains from it. Fix: solid fills, lightness ramp (white→gray→black), never patterns; proof at output resolution.

**Grids:** one legitimate job — value look-up. Weight hierarchy best→worst: no grid (data-derived ticks) → light **gray** grid well under data weight → white grid (gaps in filled bars) → mid-gray (marginal) → dark/black (chartjunk) → doubled lines (severe). Grid stroke ≈ 20–30% of data stroke (~10–20% gray, ~0.25pt vs 1pt data). Fix is gray, never thinned black (Marey timetable case). Plot on the reverse side of printed graph paper.

**Ducks:** decoration that *becomes* the structure (named for the Big Duck building). "It is all right to decorate construction but never construct decoration" (Venturi). Symptoms: fake perspective, 3-D extrusion (front face ≠ value), pictorial fills (coins, little people), gradients over area-encoded values, drop shadows, complexity-as-credential. "Boutique data graphics" = elaborate display, thin content. Sham dimension double-penalized: adds non-data ink AND distorts data ink (cross-check Lie Factor).

**Why it corrupts:** perceptual masking (raises noise floor), false complexity, displaced trust. Every chartjunk element lowers the data-ink ratio, so a chartjunk audit IS a data-ink audit.

**Diagnosis checklist:** fills solid/gray/open? No series relies on hatching? Grid lighter than data, gray, single? Data profile readable with grid hidden? Every mark encodes data or aids navigation? Ink ∝ data points? Flat (no fake perspective)? Would a table read better? (For <~10 numbers with many words: ship the table.)

---

## Data Density & the Size of the Data Matrix (VDQI ch. 8, + ch. 7)

Two co-equal quantities: **data density = matrix entries / graphic area** and **matrix size = total entries shown**. Maximize both, within reason ("Maximize data density and the size of the data matrix, within reason" — p.168). The typical published graphic: ~50 numbers at ~10/sq in.

**Resolution ceiling / yardstick:** eye locates 625 points/sq in under light grids; fine print runs ~185 chars/sq in actual (276 max, Statistical Abstract). Strong graphics approach printed-text density.

**Density benchmarks:** 4-entry bar chart 0.15/sq in; JASA histogram 3.8; NYC weather chart **181** (= text density); annual sunshine record ~1,000; Bertin communes-of-France map ~9,000 (240,000 numbers); galaxy map ~110,000 (6.8M numbers); USGS topo quadrangle ~250,000 bits/sq in.

**Publication survey (median numbers/sq in, 1979–80):** Nature 48 · JRSS-B 27 · Science 21 · WSJ 19 · Fortune 18 · Times (London) 18 · JASA 17 · Asahi 13 · NEJM 12 (max 923) · Economist 9 · Le Monde 8 · Psych Bulletin 8 · NYT 7 · JAMA 7 · Annuaire Stat. 6 · Business Week 6 · Newsweek 6 · Scientific American 5 · Statistical Abstract 5 · APSR 2 · Pravda 0.2. Nature also leads matrix size (~177 median; NEJM up to ~3,600).

**Shrink Principle:** most published graphics can be halved in area with no loss — doubling density free. Repeated shrinking → small multiples. Mark size must scale inversely with n (shrink dots/lines as data grows). If overcrowded, apply data-reduction (averaging, smoothing) before enlarging the canvas.

**Three viewing depths:** distance (overall structure), close-up (fine structure), implicit (what lies behind). **Viewing architecture:** organize reading paths (vertical rank, horizontal pair, diagonal slope) so each line of sight is steady and uncluttered.

**Density ≠ clutter:** density comes from a large matrix (preserve/increase); clutter from non-data-ink (erase). Chartjunk cost scales with density. Classify before cutting: non-data-ink → remove; data-ink → burden of proof on removal.

**Supertable:** "One supertable is far better than a hundred little bar charts" (p.179; NYT 410-number 1980 vote table). Use when many localized exact comparisons matter. Pies: lowest density, no visual ordering — never use, especially not several.

**Governing aphorism:** for non-data-ink, less is more (Mies); for data-ink, less is a bore (Venturi).

**Failure modes:** starting sparse ("clean") — summary graphics distill out of dense ones, never the reverse; small matrix packed tight; confusing density with clutter; enlarging to accommodate data; fixed mark size as n grows; pie reflex; labels exiled to legends; decorative grids over dense data.

---

## Multifunctioning Graphical Elements (VDQI ch. 6–7)

"Mobilize every graphical element, perhaps several times over, to show the data." Before adding any structural element ask: can this same ink also show data?

**Data measures built from data:** stem-and-leaf (digits plot distribution AND preserve values — Tukey: the simplest meaningful mark is a digit); Ayres' WWI chart (division ID numbers triple-function: count, identity, duration); Chernoff faces (a face per observation, features = variables; the outer limit of economy — use half-faces, symmetry is redundant).

**Data-based grids:** grid at instrument positions or historically significant events (Playfair) — erasing it erases data. **Double-functioning labels:** range-labels showing actual min/max instead of round numbers; ID codes ordered by publication date encode time; data-value labels replacing round-number scales.

**Named forms:** range-frame; dot-dash-plot (scatter + per-observation marginal dashes on both axes; best ≤ ~30 observations — note: dashes are per-observation, NOT quartile summaries); quartile plot (erased box plot: five-number summary only); white grid (thin white lines through filled bars).

**The verbal-vs-visual test:** if a graphic must be decoded verbally ("purplish means high on both"), it has failed. Gray has intrinsic light→dark order — use gray ramps for ordered amounts, color for categories. "Seeing is forgetting the name of the thing one sees" (Valéry).

**Viewing architecture:** engineer multiple steady lines of sight (the OECD tax table-graphic reads vertically = rank, horizontally = paired change, diagonally = trend slope).

**Do/don't:** grid at meaningful positions not round intervals; frame trimmed to data extent; actual values at their positions not 0/25/50/75/100 for data running 18–73; ask of every single-function element what data it could also show.

---

## Small Multiples (VDQI ch. 8; EI ch. 4)

> "Small multiples resemble the frames of a movie: a series of graphics, showing the same combination of variables, indexed by changes in another variable." — VDQI p.170

Same design structure, same scale, same encoding across panels; **only the data changes**. Because the design is constant, the eye stops re-learning each chart and attends entirely to shifts in the data. Tufte's verdict: the single most effective method for multivariate comparison — more honest, denser, and more legible than animation, sequential views, or overlays.

**Three invariants:**

| Invariant | Meaning | What breaks it |
|---|---|---|
| Same design structure | Identical chart type, layout, proportions | Switching line→bar mid-array |
| Same scale | Shared axis ranges across all panels | Per-panel auto-scaling |
| Same encoding | Identical color/size/shape/weight meaning | Changing what a color encodes per panel |

The **index variable** (time, category, condition, geography) can be one variable, or two at once → a 2D panel matrix ("flatland within flatland," EI p.78 — later named trellis/facets). Neurometric exemplar: frequency bands across columns, diagnostic groups down rows; both readings available at once.

**Mechanics:** Shrink Principle applied repeatedly (half the published area with virtually no loss) + a large underlying data matrix. Twin goals: maximize data density AND matrix size. Bertin fit 17 small graphics on one page. If the underlying table is small, an overlay/single chart is faster — the pattern earns nothing.

**Eyespan constraint:** "Comparisons must be enforced within the scope of the eyespan" (EI p.76). Scroll/tab/page-turn = comparison from memory = broken. 4–9 panels easy; 10–25 with aggressive shrinking; 25+ possible (23-panel LA air-pollution array); panels on separate pages or an animation are NOT small multiples.

**Panel structure:** shared axes, never auto-scale. Index label once per panel, smallest legible type. Implicit grid or hairlines between panels — dark surrounds generate disruptive white stripes (EI p.79). Single shared legend/scale at the array edge. Panel spacing may be proportional to uneven index intervals (spacing as data).

**VDQI exemplars:** LA air pollution (23 hourly panels, p.170); melanoma body-maps by sex (269 sites, p.171); 12 sampling-error histograms of 50 normal deviates (p.172); herring catch 1908–13 (the strong 1904 year-class bump migrates rightward — readable only via shared age axis, p.172); human/ape chromosome bands ×4 species (p.173); Consumer Reports repair matrix (12 models × 6 years × **19 rows = 17 trouble spots + Trouble Index + Cost Index**, fill density encoding rate, p.174 — "a particularly ingenious mix of table and graphic").

**Beats:** animation (can't hold prior frame in memory), overlaid series (crossing lines, color inflation), separate charts (eyespan violation).

**Seven-property conclusion (p.175):** well-designed small multiples are inevitably comparative; deftly multivariate; shrunken, high-density; usually built on a large data matrix; drawn almost entirely with data-ink; efficient to interpret; often narrative (revealing interaction/multiplicative effects as the index changes).

**Do/don't:** share axis ranges / never auto-scale per panel · shrink to minimum legible / don't oversize · one eyespan / never paginate or animate · large matrix / not a tiny table · implicit grid / no heavy borders · index label on panel / no repeated legends · meaningful order (time, magnitude) / never alphabetical · 2D indexing for two categoricals / don't flatten to one row · identical design throughout · proportional spacing for uneven intervals · almost all data-ink.

**Failure modes:** broken scale (spreadsheet auto-scale default — set explicit shared min/max); eyespan violation; structural drift (chart type changes → not a small multiple); disruptive borders; over-labeling (ticks outer edges only); alphabetical order; too few panels (<~4 → labeled overlay reads faster); tiny data matrix (array is just chrome); inconsistent aspect ratio (fix panel dimensions absolutely).

---

## Sparklines (BE pp. 47–63)

"Sparklines are datawords: data-intense, design-simple, word-sized graphics" (p.47). A small high-resolution graphic embedded in a sentence, table cell, or beside a number, showing the full shape/history of a measure at word scale. Solves the core problem: a lone number has no context, so readers over-weight the latest value (recency bias); a sparkline puts the current reading inside its entire past in the space of a word.

**Founding example:** `glucose 6.6` → replace with a data-line of the last 80 readings just left of the number; rightmost point anchored to the printed number; red ties the two representations of the latest reading; a gray band marks the normal range so above/below reads instantly. Stack glucose/respiration/temperature for parallel comparison. Reads like a sentence: "the last 80 readings of glucose, compared to normal limits, most recent in red" — *writing with data graphics*.

**Three non-negotiable properties:**

| Property | Meaning | Violation |
|---|---|---|
| Data-intense | Hundreds of points at typographic resolution | 3–5 points in sparkline space |
| Design-simple | No axes, ticks, gridlines, legends, labels on the mark | Adding an axis or point labels |
| Word-sized | Height ≈ text line/x-height; financial ~14 letterspaces wide | Taller than the type; needs its own frame |

NOT: a shrunk full chart (charts keep scaffolding; sparklines remove it), a thumbnail (miniaturizes the design rather than removing it), or a summary statistic (it preserves the full sequence's shape).

**Typographic argument:** at 11pt a letter makes 20–200 visual distinctions, a 6–7-letter word 100–1,000 — routine reading already operates at sparkline resolution. A new sparkline form is intelligible by its second publication. Precedents: Galileo's 1613 Saturn shapes set as visual nouns inside a sentence (the founding dataword); Book-of-Hours space-fillers; emoticons; Marey's smoked-plate traces; Swiss topo contours; multi-channel EEG.

**Density argument:** tables max ~300 chars/in²; graphical eye limit ~60,000 distinctions/in² (0.1mm); practice ~1,200 numbers/in². Euro FX table: 24 numbers at 5 significant digits + sparklines showing ~14,000 numbers at 1–2 sig digits — "The idea is to be approximately right rather than exactly wrong" (p.50). Mutual-funds redesign: data area only 21% larger, ~5,000 more numbers. Newspaper finance: ~160 sparklines/column → ~400,000 extra daily prices per 5-column page. Overall: **5–100× the resolution of conventional graphics and tables** (p.63).

**Design rules (do/don't):** strip all axes/ticks/gridlines · leave unlabeled, anchor with surrounding numbers · color only names a data fact (red = oldest+newest value; blue = yearly low/high; red whisker = binary flag; gray band = normal range) · height ≈ surrounding type · single color or flat 2-color mix (magenta+yellow=red) or stochastic — never 4-color process on fine lines (gritty misregistration) · thin lightweight lines (heavy strokes moiré when stacked) · no frames or hairlines only · one global scale when magnitudes must be compared.

**Four anchoring methods (quantification without labels, p.61):**
1. **Implicit data-scaling box** — flanking numbers form the scale (`1.1025 [line] 1.1907  low 1.0783 high 1.2858`) — probably the best method.
2. **Gray reference band** — normal limits; inside/outside reads without numbers.
3. **Color-linked endpoint numbers** — matched colors tie exact points to printed numbers.
4. **Global scale bars/labels** — one shared scale governs a compared cluster.

**Aspect ratio** — the most consequential production choice. Worked ratios: 12-month FX ≈ 5:1; 162-game baseball season ≈ 20:1; DNA chromosome ≈ 300:1. Apply **Cleveland's banking to 45°**: slopes judged best when hill-slopes average ~45°; aim lumpy, not spiky or flat (sunspots 1749–1924: 45° banking reveals fast-rise/slow-decline invisible in the spiky version). Procedure: take the max vertical the word-size allows → stretch horizontal until lumpy/~45° → for multiples compute one global aspect ratio averaged across all series → let the analytical task override.

**Variations:** endpoint markers (red first/last); reference band; anomaly highlight (one series colored vs. muted stack — PIMCO bond fund in red vs. 9 stock funds); binary data-whiskers (up=win, down=loss; a 162-game ribbon can carry five variables: direction, home/away line, red shutout whisker, whisker length = margin); variable-length whiskers (intensity); dataword (inline, no caption); dotdashplot (scatter whose frame axes are marginal-distribution sparklines); stacked/multiplied (2004 MLB: 6 paragraphs, 30 teams, 4,856 win/loss outcomes traced); bumps chart (800 interwoven rank-lines, 3,252 contests; crossings = overtakes).

**Domains:** finance (12/65-month daily lines beside numeric columns; multiple sparklines per noun); clinical (EEG polyspike bursts; glucose bands; mouse circadian grids); genomics (chromosome-7 map, 153M base pairs, 10 of 13 tracks at sparkline resolution); sports (win/loss ribbons; competitive path = wins − losses); any process emitting sequential numeric/binary outcomes.

**Layout at scale:** "make it wordlike and typographic" (p.63). Serious monitoring target: **500 sparklines on A3** = ~15 large screens or ~300 PowerPoint slides — data adjacent in space, not stacked in time; the entire history in one eyespan enables comparison, search, pattern-finding without navigation.

**Production:** currently needs page-layout + graphic-design + statistics programs integrated; templates then run on autopilot. Mode-segregating software contradicts the sparkline spirit (all is evidence — the Xerox Star document-centric model is the precedent). Paper >1,200 dpi beats screens (~10% of paper) for dense analysis; use the screen for interactivity.

**Failure modes:** FM1 moiré from equal figure/ground (lighten line weight); FM2 4-color grit (flat single/2-color); FM3 strong frames out-shouting data (hairlines or none); FM4 independent auto-scaling for a comparison task (global scale); FM5 spiky/flat aspect (bank to 45°); FM6 dequantification without any anchoring method; FM7 binary whiskers reading as white space (re-space/re-weight).

**Sparkline vs. full chart:** sparkline for shape/trend, inline placement, many compared series, hundreds of points, binary sequences, anomaly hunts across stacks; full chart for precise read-off values and standalone explanatory display.

---

## Aesthetics & Technique (VDQI ch. 9 + Epilogue)

"Graphical elegance is often found in simplicity of design and complexity of data." Beauty is a **by-product** of clarity + rich content — never added. Content comes first; decoration cannot rescue thin data.

**Qualities of attractive displays:** well-chosen format; words/numbers/drawing integrated; balance, proportion, relevant scale; accessible complexity of detail; narrative quality; professional drawing; no content-free decoration.

**Proportion:** default horizontal, ~1.5:1 toward the golden rectangle (φ ≈ 1.618:1); Playfair's range 1.4–1.8:1 (~92% of his 89 graphics wider than tall). Four reasons: horizon-reading, label ease, cause(x)/effect(y) elaboration, Tukey's counsel. If the data dictate a shape (map, matrix), follow the data. (Adjacent, not Tufte: Cleveland's banking-to-45° — treat aspect ratio as encoding when slope is the message.)

**Line weight:** thin lines, copper-plate benchmark. Hierarchy: data heaviest → frame/axes medium-thin → grid palest or erased → connectors thinnest → type quiet. A non-data line as dark as a data line = miscalibrated priorities.

**Friendly vs. unfriendly:** words spelled out, left-to-right; explanations near the data; **direct labels, no legend** (highest-leverage friendliness gain); no elaborate cross-hatching; colors safe for color-deficient readers (blue broadly safe; never essential red/green contrasts); upper-and-lower-case serif type, not all-caps sans.

**Format selection:** sentence for 2–3 numbers; text-table for a handful; table for exact values; supertable for many series; graphic for large/complex/narrative data; pie — avoid ("a table is nearly always better than a dumb pie chart"), never several.

**Technique = revision:** standard draft → data-ink erasure → proportion + line weight → direct labels → verify format → revise again. First-draft graphics ship as rarely as first-draft paragraphs.

**Epilogue license:** "It is better to violate any principle than to place graceless or inelegant marks on paper." Judgment, not ornament — break a rule only for the specific graphic it would harm.

**Failure modes:** portrait default; legend dependency; decoration-as-rescue; uniform line weight; pie proliferation; polish-before-format.

---

## Escaping Flatland (EI ch. 1)

The world is multivariate; paper and screen are 2-D. "Escaping this flatland is the essential task of envisioning information." **Two goals** (not six strategies): increase representable dimensions; increase data density per unit area. **Five methods:** micro/macro readings, layering and separation, small multiples, color, narratives of space and time. Density is a goal, not a peer method.

**Spectrum of escapes** (literal → encoded): physical models (Euclid 1570 fold-ups) → perspective → stereo pairs → rotating point clouds → mechanical simulation (orreries — failure: apparatus over content) → symbolic encoding (carries the most variables; demands a learned code). More abstract data → move right.

**Sunspot lineage:** Galileo's projection method (1610–12) → visual reasoning ("eye of the forehead" → "eye of the mind," 1613) → Scheiner's small multiples (1626–30, but emblems in blank regions = failure) → Maunder butterfly (1904: two areal dims reduced to latitude, freeing the surface for time; micro marks aggregate to the macro 11-year cycle) → modern butterfly (10× density, nine cycles, color = log area). "Measured assessments of variability are at the heart of quantitative reasoning" — show variation, never just the mean (Fisher).

**Java railroad timetable (1937):** 16 variables on one sheet; each train diagonal carries **six variables at once** (location, time, direction = slope sign, type = line style from a 4×4 type×seasonality matrix, relative speed = steepness, seasonal pattern). One mark doing six jobs beats six marks.

**Narrative exemplars:** Tomlinson's dance notation (1735 — double-functioning numbers sequence steps AND tie to musical measures); Japan weather cross-section (1985 — vertical side profile frees an axis for temperature/altitude).

**Tables multiply too:** LSAT bivariate grid (GPA × LSAT, two numbers per cell, margins = univariate sums); Gotti courtroom chart (69 crimes × 7 witnesses, readable both directions, 37% of cells marked, rhetorical edge placement). Tables beat speech: wideband + perceiver-controllable vs. linear non-reversible talk.

**Failure modes:** Pridefully Obvious Presentation (orrery gears), embellishment-for-data (Scheiner's emblems; Swift's elephants "for want of towns"), the Duck (content-empty third dimension), data posterization, contempt for the audience, pretend dimensions. "Readers of a report should be unaware of its design" (Paul Rand). If the numbers are boring, you've got the wrong numbers.

**Checklist:** name both goals; pick methods; variables in data vs. shown; every mark ≥1 job, any doing 2?; micro AND macro legible; honest seams when compressing scale (Ise Shrine); tables read both ways; density above the suspicion threshold; no ducks; container smaller than data.

---

## Micro/Macro Readings (EI ch. 2)

"To clarify, add detail" (p.37). "Clutter and confusion are failures of design, not attributes of information" (p.51). Detail *builds* the big picture; the same marks serve the close-up datum and the distant gestalt.

**Three reading modes must coexist:** macro (glance — pattern), micro (inspect — exact value), transition (how one resolves into the other). Density matches the mind: humans constantly select, filter, cluster, skim (~50 such verbs, p.50); sparse displays squander that apparatus.

**Four data layers** (resistivity/conductivity charts, p.39): individual points (cited by ID) → connected curves (per study) → conglomeration (agreement + scatter) → RECOMMENDED reference curve. Fifth layer free: order study IDs by publication date (61c = 3rd paper of 1961) → chronological convergence becomes visible.

**Canonical examples:** Anderson's axonometric Manhattan (60×92cm; 1,686 named buildings, 657 addresses, ~20 chars/in²; individual windows gray into building surfaces; exactly ONE distortion — streets widened for legibility); Senlis aerial photo (texture IS the pattern); Klutsis poster (many hands = one gesture); Tokyo mesh maps (Japan divided into 379,000 equal 1-km cells — fixes choropleth flaws: visual weight tracks data not land area); **Vietnam Veterans Memorial** (58,000 names; each name triple-functions: memorial + count + chronological position; Maya Lin insisted on chronological order — 600+ Smiths would make an alphabetical wall a telephone book; a separate alphabetical directory restores random access without polluting the display); Shinkansen timetable; stem-and-leaf (digit = value + bin-fill; 292 trains in 619 numbers vs. 1,396 for the plain listing); space-debris map (7,000 tracked objects, one dot each; scale felt, not stated).

**Capacity figures (p.49):** human eye ~150M bits; large topo map up to 150M; 35mm slide ~25M; dense printed page ~20M; c.1990 computer screen 8M. Displays should approach cartographic density, not slideware sparsity.

**Design patterns:** multifunctioning marks (every mark readable at ≥2 scales); layered hierarchy (glance 1–3s / scan 5–30s / inspect minutes); equal-unit encodings (one cell per km², one name per soldier — the macro assembles itself); a finder beside large displays (directory, index grid, zoom/search).

**Failure modes:** posterization trap (fanning one dense page across 10+ panels); choropleth distortion; severed micro/macro narrative (alphabetical order where sequence matters); context switching between layers (both must be spatially co-present); medium/density mismatch (screens can't hold the micro layer — reduce scope rather than fake detail); decoration mistaken for density.

---

## Layering & Separation (EI ch. 3)

Confusion and clutter are failures of design, not properties of information — fix by layering, never by thinning data.

**The 1+1=3 principle (Albers):** two marks always create a third — the activated negative space between them. Two strips separated by one width read as 3. Editing discipline: (1) find every 1+1=3 effect (white paths, halos, vibrating edges); (2) ask if each carries information; if not, mute or remove the causing mark.

**The noise formula:** "The noise of 1+1=3 is directly proportional to the contrast in value (light/dark) between figure and ground" (p.62). Gray marks generate far less noise than black at equal weight → prefer lighter colors for secondary layers. Worked move: thin two sides of every block (one thick + one thin line per street) so boundaries stop vibrating.

**Figure/ground:** the undifferentiated-surface test — do all elements share one value/texture/color/shape? (Simla map = jumbled failure; Tokyo 1884 map = separation by shape, value, size, especially color, on a dull ground not bright white.)

**Color layering (Imhof's rules quoted here):** large areas muted/grayish/neutral; strong saturated color only on small extremes — "only on a quiet background can a colorful theme be built." Small spots of intense color = the design secret of classical cartography.

**Weight hierarchy and grids (Tschichold):** first try no rules at all; thin horizontals beat thick; verticals only when columns so narrow reading fails; gray/screened grid behind dense data (ECG, music staves); black grid never — "Dark grid lines are chartjunk" (p.59); "Tables should not be set to look like nets with every number enclosed." Grid darkening earned only by genuine look-up interpolation, and still muted. Tukey plot case: doubled grid lines consumed 18% of the chart. Leader dots = a separator with almost no noise cost.

**Subtraction of weight (Calvino):** layering is achieved by removing, not adding. Marshalling-signals redesign: extend value range (gray silhouettes), color the lamps (small saturated spots), erase ~460 lamp-whiskers, differentiate the type — figure separates from ground with strictly less ink.

**Type as a layer:** never box running words (activated halo); place river/line labels from above — words have fewer descenders than ascenders, so the smoother edge sits against the graphic; watch for the white stripe between type and line.

**Failure modes:** data imprisonment; equal-weight surface; vibrating edges; moiré prison; information prison; ground louder than figure; proportionality inversion (least important datum most prominent — NJ Transit's giant train IDs); box-around-text; label white-stripe; decorative gridding.

**Audit:** name every layer → rank by priority → match weight to rank → find every 1+1=3 effect → lighten secondary contrast → gray the grid → saturate only small top-layer areas → unbox everything → fix label placement → extend value range → subtract (Calvino test) → design the blank space.

---

## Color in Information Design (EI ch. 5)

First principle: **"Above all, do no harm"** (p.81).

**Four functional uses** (all on the Swiss Matterhorn sheet): **label** (noun — water vs. stone vs. glacier; primaries + black for max separation), **measure** (quantity — altitude darkening; sequential light→dark, never rainbow), **represent** (imitate reality — blue water, brown land), **decorate** (must justify itself; strip if no data role). Assign each mark exactly one role.

**Capacity:** trained eye ~1,000,000 colors pairwise; ~20,000 practical; >20–30 colors for abstract encoding → *negative* returns (limit = visual memory, not discrimination). Practical categorical ceiling ≤ ~7 (Miller working memory, not Tufte).

**Color is 3-dimensional** (HSV/RGB/CMY) → one mark can carry multiple variables, but only for coarse cluster detection, never exact read-back; pair with position.

**Imhof's four rules:** (1) strong colors only on small areas; (2) no adjacent pastels over large areas; (3) muted grayish backgrounds, vivid small foregrounds — gray is the most versatile color; (4) interweave colors carpet-fashion rather than partitioning into blocks (Tufte's caveat: rule 4 over-generalized — Mondrian violates it well; apply to dense thematic data only).

**Sequential scales:** value light→dark. "The mind's eye does not readily give an order to ROYGBIV" (p.92) — rainbow = encipherment. Gentle hue variation may *extend* a value ramp (keeps natural sequence). GEBCO exemplar: 21 darkening steps, contours outlining each color field, four variables per mark.

**Contextual effects:** simultaneous contrast, edge fluting, Albers subtraction — perceived color depends on surround, so never carry a critical distinction on color alone. ~8% of males red–green deficient: never essential red/green contrasts. Constructive use exists (road-map red deepened by flanking blue).

**Redundant coding:** the cure for color's instability — but earned only when (1) a genuine ambiguity exists and (2) the technique reduces *that* ambiguity. Contours + color fields (Marr: vision weights contour decisively). Target crystalline redundancy, not committee clutter.

**Nature palette:** draw from nature's lighter side — sky blues, shadow grays, straw yellows — pre-calibrated harmony; muted ground + saturated focal accents.

**Screens:** low resolution (1/10–1/1000 of print), glaring white — soften the background, de-grid via color edges; the active-window frame needs light value + high saturation simultaneously → **yellow** is the only color satisfying both.

**Failure modes:** color inflation; color partition; rainbow encipherment; solo color encoding; pastel-on-pastel; decoration masquerading; 1+1=3 noise; contextual collapse; red–green solo; gratuitous multiplicity.

---

## Data Maps (EI ch. 1–2 application)

High-quality maps are the **gold standard of information design**: bountiful detail, layered close reading plus overview, rigorous survey data. Most failed graphics behave like **posters** (viewed across a room: strong image, big type, thin data). Test: does it reward BOTH a distant glance and nose-to-page inspection?

**Two levers:** more dimensions per plane; more data per unit area. Every available axis must carry data (Java timetable rule). Density benchmarks: Anderson Manhattan (1,686 names + 657 addresses on one sheet); LA smog (2,400 5-km cells × 12 maps = 28,800 readings, 5 variables); Java timetable (6 variables per diagonal, 16-variable sheet); modern butterfly (10× the 1904 density).

**The data question governs the projection:** profile/section view when the answer lives in the vertical (Japan ocean-eye weather map — works best for long thin countries); linear-distance/graphic-timetable when only along-path position matters; multi-scale/axonometric when local detail + global frame are both needed (Ise Shrine: perspective local view + flat national rail map, registers pointing at each other); plan view only when lat/long is literally the answer.

**Micro/macro on maps:** "to clarify, add detail"; "Simplicity of reading derives from the context of detailed and complex information, properly arranged" (p.37). Cluttered map → better arrangement of MORE detail, not less data.

**Maps as small multiples:** LA pollution 12-panel array — decode once, read every panel free; hold scale, projection, framing, color absolutely constant.

**Failure modes:** the duck (pretend dimension on thin data); map-as-poster; Swift's elephants (ornament in empty space); plan-view waste; relief masking (3-D peaks occlude values — rotate, use transparency, or split into multiples); marginal-only display (show the joint distribution, not just margins).

---

## Space-Time Graphics (EI "Narratives of Space and Time," pp. 101–113; VDQI pp. 115–116)

One axis = position along a path, other = time; a moving entity traces a line whose **angle = speed**, crossings = encounters, density = congestion. Invented by Ybry (1846 patent) for railway scheduling.

**Setup:** stations at TRUE proportional distance (equal spacing on unequal distances corrupts every slope); uniform clock time; extend past midnight (cylinder or prolonged grid). Reading: steep = fast; shallow = slow; horizontal = stopped (dwell length = minutes); vertical = impossible; opposite directions lean opposite ways.

**Crossings:** x = when, y = where two vehicles meet. Single track: crossings allowed only at station/siding bands — a crossing *between* stations is a designed collision. Railways planned passing sequences graphically for a century; the numeric table hides these conflicts entirely.

**Grid:** dark grid = chartjunk (moiré with dense diagonals); light gray at ~ten-minute intervals for transit ("The gray grid is set at ten-minute intervals in order to ease visual interpolation" — EI p.110). Grid subordinate always.

**Space vs. time detail tradeoff:** route topology (Czech air network 1933) ↔ minute precision; or layer both at full fidelity (Hoboken–NYC bus schedule: house-resolution aerial photo + complete graphical timetable).

**Universality** ("nearly boundless subtleties," p.110): transit; Jupiter/Saturn satellite corkscrews (Galileo 1613/Cassini 1668 — time runs *vertical*); Japanese-beetle life cycle (months + ground-position doubled on horizontal, depth vertical); esophageal transit (video frames summed to 1-px columns, 60 columns over 12s — standard orientation); Oxford Torpids bumps chart (rank × race-day, crossings = passes; depends on the river's physical no-passing constraint); Wagner opera development timelines.

**Conventional-table critique (Metro-North, EI p.104):** only **21%** of area shows train times; 41 in (104 cm) of rules; headings repeated 3×, 24 AM/PM markers, serpentine eye path; redesign in Bell Centennial with quiet dot separators.

**Failure modes:** equally spaced stations; dark grid; ignored single-track constraints; space+time collapsed to one table axis; midnight truncation; graphical form for the public without spatial anchoring; omitted dwell time; bumps logic without a passing constraint.

---

## Narrative & Sequence (VE ch. 1–6)

Visual explanations explain *why/how*. Two recurring epistemic failures: **dequantification** (images stripped of scales/labels/orientation) and **disinformation design** (magician tactics concealing rather than revealing).

**Ch.1 — quantify the image:** van Langren 1644 (12 longitude estimates vs. true 16°30' — first statistical graphic); Lambert 1765 quantified the plane. Compilation audit: of 134 color scientific images across 19 articles, **65% had no scales, 22% partial, 13% complete**. Thunderstorm-animation redesign: 3-D tripod of labeled scales (16 km / 100 km / N-E arrows) + six clouds as 3-D tick-marks on a red timeline — restoring scale converts television into evidence. Cleveland banking-to-45°: sunspots reveal fast-rise/slow-decline only at the right aspect ratio. Magellan Venus flyover: 22.5× vertical exaggeration — show natural and stretched as an honest before/after. Ethical floor: show the unprocessed image beside the manipulated one; document methods and the selection pool.

**Ch.2 — Challenger rules:** (1) show ALL data including zero-effect cases (engineers showed 7 damaged flights, omitted 17 undamaged); (2) put the causal variable on the axis (temperature, not flight number); (3) draw the decision boundary (29°F reference line). Correct display: temp 26–81°F × O-ring distress 0–6, all 24 flights, 29°F line.

**Six principles of evidence reasoning (p.53):** document sources; enforce appropriate comparisons; demonstrate cause-and-effect mechanisms; express them quantitatively; recognize multivariate nature; inspect alternative explanations. Clear seeing and clear thinking are one act.

**Ch.3 — magic inverted:** larger motions hide smaller motions (misdirection = visual masking; in a display, the same move makes a lie). "There is no magic in still-land" (p.63) — for analysis, self-paced still images beat video (viewer controls pace, sequence, direction, focus). ~80% of magic literature runs text and pictures as two separate stories — fuse shared verbs into one figure. Disinformation cases: masking staircase carpet (1,400+ falls in six weeks), framed all-caps Surgeon-General warning. Automaton Chess Player: Willis/Brewster diagrams were technically excellent and FALSE (the machine was a puppet on sticks); errors propagate because copying is cheaper than checking (California-as-island: 182 map variants; Dürer's rhino ~200 years). **Integrity test:** truthful? accurate representation? documented data? no spurious readings? appropriate comparisons/context?

**Presentation structure — PGP + six rules:** Particular → General → Particular. (1) State problem, why it matters, solution up front; (2) explain via PGP; (3) give everyone dense paper handouts; (4) analyze then master details by practice; (5) show up early; (6) finish early.

**Smallest effective difference (ch.4):** "Make all visual distinctions as subtle as possible, but still clear and effective" (p.73). Every non-data element (arrows, pointers, ticks, grids, frames, fills) as close to invisible as its function permits. The 25-thick-pointer ear diagram → muted pointers + direct labels. Just-*notable* differences, not just-noticeable.

**Faulty parallelism cases (ch.5):** Repton's "after" added nine boats and deer (embellishment beyond scope); NYT caption named the wrong man ("Chagnon, left"); HIV mortality charts scaled 0–65 vs 0–30. Rule: parallel panels differ only where the data differ.

**Six functions of multiple images (ch.6, p.105):** reveal, compare, dimensionalize, enumerate, narrate, intensify. Huygens' 32 Saturn images (1659); 13 wrong Saturn interpretations 1610–45 ("people can see more clearly if they have the right idea," p.107); graphical patient status (24 images/patient; 11,616 cells; 10–20× info-transfer over verbal); Reinhardt multiple wasted 42% of frame area on borders. Motion in stills: space takes over time's role; match frame density to motion abruptness (Huygens 1.8-yr spacing for smooth orbits; Muybridge 18 frames for seconds of leapfrog); always label the time scale.

---

## Parallelism (VE ch. 5)

Matched structure turns a pile of pictures into a comparison; congruent form (same viewpoint, scale, orientation, track) gives a stable baseline so the eye reads the *variation*. "Good form is clear but not a spectacle."

**Mechanisms:** position/adjacency, orientation, overlap (superimposition), synchronization, similar content, common track/scale, common centering.

**Central decision — space vs. time:** comparisons are usually more effective **adjacent in space, not stacked in time** (temporal sequence = memory test). Reach for time only when the medium forces it or an exact-overlay flip pays.

**Flip-parallelism (Repton's flaps):** temporal beats spatial only with exact registration and a flap scoped tightly to the changed region. UI: onion-skin/opacity-slider diffs — only when pixel-registered and change is localized.

**Superimposed:** overlay instances with a value gap (black over gray) for fine shape variation — Catich's Trajan letters proved brush-painting via overlays; needs shared registration + value contrast or it smears.

**Synchronized:** one clock drives all channels; highlight the active item in every channel (Beethoven 9th CD-companion — but its ornate frame ate ~30% of the screen: chrome tax).

**Common track:** many flows on one shared labeled scale (88 piano keys; Salyut-6 cyclogram — 8 parallel time-counting methods drawn in orbit, planned in ink vs. actual overwritten in red).

**Direct labels beat codes:** a code relays image → number → legend → noun; Catich redesign replaced ~48 scattered code numbers with direct labels and grew from 24 to 66 named parts. Codes justified only for genuinely dense fields (146-astronomer photo), and even then seed landmark signifiers; ~⅔ of codes are eliminable.

**Failure modes:** stacked-when-space-was-free; mismatched scales/baselines (the layout looks parallel, the numbers aren't); mis-caption; embellishment smuggling; diagram corruption (redraws breaking load-bearing invariants — Newton's equal refractions); frame/chrome tax; spectacle over clarity.

**Checklist:** adjacent in space? like against like (scale/axis/orientation/crop)? only the studied variable differs? direct labels? captions verified? overlays registered with a value gap? one clock for synced channels? invariants preserved in redraws?

---

## Causal Reasoning in Graphics (VE "Visual and Statistical Thinking")

The paired case studies: Snow's 1854 cholera map (correct causal display, epidemic ended) vs. the 13 Thiokol charts (right data, causal signal concealed, seven deaths). Arrangement determines whether causality is visible.

**Compared with what?** Snow's map argued equally from non-cases: the brewery (70+ workers, no cholera — drank malt liquor) and the workhouse (535 inmates, 5 deaths — own well; surrounding-street mortality predicted 100+). Thiokol mirrored the failure: 7 damaged flights shown, 17 undamaged omitted — the undamaged flights carry the statistical leverage.

**Temporal vs. causal structure:** "the passage of time is a poor explanatory variable" (p.29). Snow converted a 1-D date-ordered death list into a 2-D spatial display with all 13 pumps marked. Thiokol ordered 48 rocket icons by launch sequence with temperature sideways in small type; the corrected chart orders by temperature with 29°F marked — pattern visible in seconds (every launch below 66°F damaged; 29°F was 5.7 SD below mean, 37°F colder than any undamaged launch).

**Aggregation artifacts:** weekly cholera bins (Sept 1–7 vs 8–14) make the pump-handle removal look decisive; daily data show no break; shifting boundaries two days changes the story again. Monmonier's spatial re-binning erases or relocates the Broad Street cluster; the dot map survives all partitions (but shows counts, not rates — pair with a population-rate map). **Specification searching:** fast tools sift thousands of aggregations; treat any presented chart as the most favorable of many silently tried. A real signal survives reasonable changes of interval, bin, and boundary.

**Snow's four principles:** place data in the causal context (deaths + all pumps on one display); make quantitative comparisons; investigate contrary cases (each far-from-pump death explained: schoolchild, cabinet-maker, the widow's daily water delivery); assess errors in the numbers openly.

**The 13 charts' five failures:** wrong effect measure (blow-by, not erosion — inviting "hottest and coldest both had blow-by," n=2); selective data (92% of temperature data missing); wrong ordering (temporal); disappearing legend across slides; chartjunk (48 rocket silhouettes dominating the data marks). "A lack of visual clarity in arranging evidence is a sign of a lack of intellectual clarity in reasoning about evidence" (p.48).

**Six dual principles (design = reasoning, p.53):** document sources/data; enforce comparisons ("compared with what?"); demonstrate mechanisms; express them quantitatively; recognize multivariateness; inspect alternative explanations — each with a display-side and a reasoning-side obligation.

**Feynman's counter-example:** the one-glass ice-water O-ring demo was an experience, not an experiment (cold vs. wet vs. clamped unresolved); a control glass at 70°F was required. Single evocative examples never establish cause. "For a successful technology, reality must take precedence over public relations, for Nature cannot be fooled."

**Checklist:** non-cases included? causal variable on the axis? full dataset (state the fraction shown)? contrary cases explained on the display? the proposed intervention value plotted on the same axis? readable without oral explanation? aggregation sensitivity tested?

---

## Visual Confections (VE "Visual Confections")

A confection assembles many image-events — real and imagined — from different story-strands onto one still surface to argue, list, or narrate: "showing all at once what never has been together." "What collage is for art, confections are for the design of information" (collage = visual experience; confection = visual information, often derived from words).

**Two organizing structures:** imagined scene (Pugin's 25 churches; *Melencolia I*; Babar's Dream) · compartments (call-out grids) · or both (Hobbes' *Leviathan*: sovereign-body scene above, cross-linked grid below — cells pair across temporal/ecclesiastical columns; ~31,200 words to describe; multifunctioning elements are the mark of quality).

**Visual lists carry verbs:** the "Ultimate Weed" call-outs state what the weed *does*. Anti-pattern: Pugin's legend six pages away, printed vertically — a list whose key is unusable is decoration.

**Annotation and the instructed viewer:** integrate labels/captions into the image (Burton's stanzas keyed to compartments); design for the "out-of-towner" — reward, don't require, prior knowledge.

**Failure modes:** thin content; flimsy logic (adjacencies that don't reason); poor annotating text; heavy-handed structure; the cutter's art (tendentious selection — illuminate, don't score points); out-of-towner reliance.

**Interface as one-time confection:** information becomes the interface (National Gallery kiosk: ~90% substance, ~45 options at once; distribute in space, not down a decision tree; computer selects, paper prints the permanent record). Audit measures: content share of screen; typographic density vs. print; commands immediately available. Worked failure: the "Yearbook" book-metaphor screen — 18% substance, 82% chrome, 53 characters where a book spread carries 1,000–50,000. Anti-patterns: news-broadcast (architecture mimics the org chart), "standard computer practice" (binary decision trees, fake drop-shadows), interface-as-billboard. Potomac lesson: printed confection beats video — reader controls order, pace, entry; add searchable fine detail (57 victim portraits + 57 death-location dots) to activate viewers. Pioneer plaque = the ceiling: fully self-annotating for a viewer with no shared context.

---

## Analytical Design — the Six Principles (BE pp. 122–139)

"The principles of analytical design are derived from the principles of analytical thinking" (p.137). Name the intellectual task first; the design follows. The principles are universal — across media, eras (6,000-year-old stone maps to future displays), and minds; producer and consumer share one standard ("we're all in it together"). Never excuse weakness with "it's only a slide/dashboard."

1. **Comparisons** — make contrasts explicit and visible; the central question of statistical reasoning is *compared with what?* (Matisse: "I paint only the differences between things.") Failure: the Floating Fact ("sales were $4.2M" with no baseline). Minard: 422,000 in / ~10,000 back ≈ 1:42 survival (bands as drawn at the Niemen ≈ 1:28 — the encoding is approximate; don't conflate).
2. **Causality, mechanism, structure** — show why, not just what; policy decisions ARE causal decisions. Minard's temperature curve is the mechanism. Failure: Effects Without Causes (outcomes with no agent).
3. **Multivariate analysis** — show >1–2 variables; nothing interesting is bivariate; flat displays train flat thinking. Multivariateness should be routine, not an achievement. Benchmark: Nature/Science graphics median >1,000 numbers; Lancet ~45. Failure: Forced Flatland.
4. **Integration of evidence** — completely integrate words, numbers, images, diagrams; evidence doesn't care what mode it arrives in. Minard fuses map, flow-lines, temperature, dates, text on one 25×21-in surface; Galileo wrote time/identity/distance onto his 1610 sketches. Failures: Mode Segregation ("see Figure 3"), Single-mode Research.
5. **Documentation** — detailed title, named authors (people, not agencies), sponsors, data sources, complete measurement scales, caveats — on the face of the display. Minard names 5 sources, 3 scales (1 mm = 10,000 men), place, date, assumptions. Benchmark: in 13 CS visualization books only 20% of images had complete scales; 60% none. Failure: Anonymous Authorship.
6. **Content counts most of all** — the supremacy principle; no technique salvages weak content; the direct route to a better presentation is better content. Minard never names Napoleon. Failures: Chartjunk as Substitute, Technology-Driven Presentation.

**Analytical vs. decorative:** first question "what content task?" vs. "how can it look good"; shows complexity/uncertainty vs. suppressing them; documentation required vs. optional. Core test: could a skeptical expert assess evidence quality, provenance, and completeness from the display alone?

**Checklist:** compared to what, visible in the display? mechanism or mere correlation, agents named? how many variables does the phenomenon have vs. shown? modes assembled where needed? author/sources/scales/date on the display? content substantively adequate? excused anything as "only a slide"?

---

## Evidence Corruption (BE ch. 6, pp. 140–155)

"Making a presentation is a moral act as well as an intellectual activity." Five named corruptions, each with a detection method.

**1. Effects without causes / passive-voice evasion.** 9/11 Commission passage: 5 passive verbs, 3 active with a vague subject — no agent named for seven failures. Passive voice enables "immaculate conception" analysis: ends without means, actions without actors. Bullet lists collaborate: "Accelerate Revenue Recognition!!!" names no who/what/how/when; "Bullets leave critical assumptions about how the business works unstated" (HBR); three different causal structures fit the same three bullets. Detection: count passives; demand subject + predicate + named agent; draw the causal arrows. Anti-causal statistics (data mining, factor analysis) generate effects from nowhere — exploration, not explanation.

**2. Cherry-picking.** The most widespread obstacle to truth; invisible because the audience can't see omissions. Sign: too good to be true. **Evidence Decay Cycle:** first (poorly controlled) study shows the strongest result it will ever achieve; better-controlled follow-ups decline; RCTs sometimes ask only whether the treatment harms. **Chalmers portcaval-shunt data (53 studies):** of 6 RCTs, 0 markedly enthusiastic; of 47 poorly designed, 34 (72%) markedly enthusiastic. The Peacock anecdote ("Which half?") is the human engine. Detection questions: filtered evidence? findings from evidence or evidence-selection? survives a fraud investigator? field notorious for advocacy? replicated? who paid?

**3. Model-searching.** Four compounding factors: imprecise theories, many "notions" (ad-hoc exclusions, dummies, logs, lags), many operational measures per concept, data slack (endpoints — a notorious financial cheat; cut-points; missing-data choices). 2^k − 1 models × notions → routinely 10⁴–10⁷ computable models, one published. **Shrinkage:** R² of a searched model always drops on fresh data — the quantitative signature; fresh-data validation is mandatory. Ioannidis 2005 ("Why Most Published Research Findings Are False") formalizes the default state.

**4. Evidence reduction chain:** raw data → reduction/construction/representation → report → secondary/tertiary bureaucracies (PR, advertising, journalism, textbooks). Integrity rests on the whole chain. Audience scaling: technical reviewers = a handful; ad viewers = millions; ~100,000 mediated readers per original reader. Barnum explains why producers feed the machine: without publicity, nothing happens.

**5. Punning, overreaching, "economisting."** Galenson case: "value" slides from price to merit — Fischer's **fallacy of equivocation**; the term carries 7 meanings and "Concepts that explain everything explain nothing" (p.149; Geertz's all-seasons "culture"). Book had 15 tables, 2,029 entries, ZERO actual prices. Statistical puns: "significance/confidence/optimal" trading technical authority for everyday meaning; a metaphor extended to a new domain must earn new domain-specific evidence (Weinberg on quantum mechanics). *Economisting* = e-CON-o-MIST-ing: con + mist (+ German *Mist* = manure).

**Chartjunk as corruption:** "gratuitous and cartoonish decoration... provides evidence about the presenter's integrity and statistical skills: little integrity, no statistical skills" (p.152). 3-fold revenue growth drawn as 7-fold area change. Graph bureaucracy: grid prisons, empty framing (the Boeing Columbia spreadsheet). Sports/weather/financial pages have little chartjunk — the content is too important.

**Rage to conclude (Flaubert):** repackagings deny uncertainty; news wins out over olds. **Pitching out corrupts within:** external advocacy eventually corrupts internal evidence standards (agencies fixed on a policy line become "perpetually unintelligent"). Defenses: publish primary reports directly; prepare your own secondary versions; police the repackagings. Consumers: hopeful and curious, open mind but not an empty head; corrupt maneuvers also "place the truth in disrepute."

---

## The Cognitive Style of PowerPoint (BE pp. 156–185)

Format is not neutral: chopping evidence into bullet fragments on low-resolution serial slides degrades analytical thinking. "PowerPoint is presenter-oriented, not content-oriented, not audience-oriented." Evidence base: 10 case studies, ~2,000 slides, 32 control samples; PP loses every comparative test except beating *Pravda*. Harm distribution: helps the bottom 10% of presenters, spares the top 10%, damages the middle 80%.

**Ten deficiencies:** foreshortening of evidence; low resolution; forced deep hierarchy for all content; fragmentation into slides; rapid temporal sequencing instead of spatial analysis; chartjunk and PP Phluff; logo branding; format preoccupation; incompetent data-graphic designs; smirky commercialism.

**Bullets vs. sentences:** a bullet list carries only three relationships, one at a time — sequence, priority, set membership. It cannot express causality, conditionality, exception, mechanism, or quantified comparison; the sentence (agents + verbs + effects) can. The deeper the hierarchy, the greater the loss. Gerstner killed the projector ("Let's just talk about your business"); Feynman covered physics in 1,800 pages with zero bullets and 2 hierarchy levels. Orwell adapted: the slovenliness of PowerPoint makes it easier to have foolish thoughts.

**Density (chars/in²):** Physicians' Desk Reference 168 · World Almanac 232 · news sites ~43 · Boeing Columbia slides 7 · median PP report slide 3 · PP textbook slide 1. One PDR page = 54 slides; best-sellers run 10–50× deck density. Readers do 300–1,000 wpm vs. speakers' 100–160 — thin slides waste that 3× capacity. "The PP slide format has the worst signal/noise ratio of any known method of communication on paper or computer screen."

**Pravda table (median data-matrix entries):** Science >1,000 · Nature >700 · NYT 120 · NEJM 53 · Economist 32 · 28 PP textbooks 12 · Pravda 5. Doing a bit better than Pravda is not good enough. **Miller myth:** the 7±2 paper concerns recall of unrelated meaningless items; Miller's own answer for optimal bullets and slides: zero and zero.

**Sequentiality:** the Dreaded Build (line-by-line reveal at the presenter's tempo). **Pairwise-comparison formula:** n cells → n(n−1)/2 comparisons; Graunt's 1,855-count mortality table = 1,719,585 comparisons in one eyespan; split over 155 slides ≈ 10,230 (6 per 1,000), time patterns blocked.

**Columbia case (2003, not Challenger):** decision made while Columbia was in orbit. Key slide "Review of Test Data Indicates Conservatism for Tile Penetration": 6 hierarchy levels for 11 phrases; "significant(ly)" used 5 incompatible ways; the actual finding — debris volume **640× beyond the tested range** (1920 vs 3 cu in) — buried as a 4th-level bullet; title reassures; analysis scoped to tile while the wing RCC failed. CAIB: the slide format highlighted what management already believed; the Return to Flight Task Group: PP presentations "should never be allowed to replace, or even supplement, formal documentation."

**Remedy — the written report / 4-pager:** one A3 sheet folded = up to 60,000 characters, tables worthy of the sports pages, or ~1,000 sparklines showing 500,000 numbers — equal to 50–250 slides. Procedure: hand it out, let people read (readers beat speakers 3×), then lead discussion. "At a minimum, we should choose presentation tools that do no harm to content." Full-screen images/video are the one harmless projector use.

**Self-check:** claims stated as full sentences with agents? key comparison within one eyespan? causal variable displayed? headline = actual finding? any word carrying incompatible meanings? scoped to the real risk? all data incl. disconfirming? author + sources named? structure = argument or org chart (Conway's Law)? would a handout beat the deck?

---

## Links & Causal Arrows (BE pp. 64–81)

Every line in a diagram is a claim — that a relationship exists, of a specific kind, direction, strength, certainty. **Nouns are specific; connectors are usually generic, identical, ambiguous** — "The more generic the arrows and lines, the greater the ambiguity" (p.68). Sameness of mark falsely asserts sameness of process; variation between connections is the norm.

**Four framing questions for any link diagram:** What precisely do the arrows mean? What do the lines stand for? Where is their dictionary? How could they carry more precise meanings?

**Barr chart lessons:** 51 identical arrows = the verbs of the analysis all drawn alike; erasing connectors guts the diagram (they carry the analytical content); **absent arrows are silent non-influence claims** — audit the white space.

**Baxandall's differentiated verbs** (the strongest idea): "influence" reverses agency — Y did something *with* X. Run the **reversal test** (arrowhead on the wrong end? actually mutual ⇄?). Single-headed arrows forbid feedback by construction. Replace the generic arrow with the verb that applies: adapt, appropriate from, react to, quote, parody, absorb, resist, subvert, transform...

**The cartographic standard:** map legends make 34/15/17 line distinctions; finely textured lighter lines, like good typography. "The metaphor is the map, not stupidity" (p.79). "Maps don't put boxes around city names" — drop org-chart boxes; position locates nodes.

**Annotate links AND nouns:** Verrocchio's horse — each dimension line carries a number and words; a sparkline can BE a linking line (variation, strength, reliability over time). SARS chart annotates every patient (strain, clinical, travel) and grades link certainty (dotted = uncertain routes).

**Encoding channels:** line style = type/certainty; weight = strength (Feynman's classic error: equal weight for pointer lines and object lines); color = category (must match expectation); length = quantity; on-link text/sparkline = mechanism. Applied defaults (extension, not Tufte): solid heavy = confirmed; solid light = probable; dashed = inferred; dotted = speculative; ⊣ = inhibition; ↔/⇄ = mutual.

**Six analytical practices (SARS synthesis):** focus on causality with graphic uncertainty; multiple sources and levels of data; annotated linking lines; annotated nouns; maplike efficiency (no PowerPoint connectors); credibility (expose alternatives; honest precision — no 4-sig-digit indices from crude data, no "feel-good pitch words").

**Failure modes:** generic undifferentiated link; implicit non-influence claim; one-directional influence fiction; equal line weight for all elements; box-around-every-noun; chartjunk connectors; mismatched color code; suspicious precision; legend displacement; style collision. Galileo's 1610 annotated optics drawing is the 400-year-old bar: "we should do as well."

---

## Mapped Pictures (BE "Mapped Pictures")

A representational image shows what something looks like; a **mapped picture** lets a viewer measure, place, compare, and test it: "Mapped pictures combine representational images with scales, diagrams, overlays, numbers, words, images." Image contributes the specific real case; diagram contributes context, abstraction, focus. Test: could a stranger extract a measured value and locate any feature without leaving the image?

**Scale of measurement — the most-skipped obligation:** Galileo measured Jupiter's moons in Jovian radii on the sketch; Crick–Watson model photographed with a 0–10 Å bar (1 cm = 10⁸ Å); Earth beside Saturn; a ruler drawn in the plate; explicit rescale factors ("multiply by 9.4"). Anti-example: Bloch's 216 fishes in identical boxes → "every fish has both a different and unknown scale" — no two comparable; fix = a real cm ruler per image.

**The map metaphor:** labels belong ON images; external grids scale them (weight below the data); context confers credibility. **Universal grid:** every image should sit on x, y, z, t; the grid travels through every zoom/crop/rescale; relative-only scaling ("this bird bigger than that") breaks on any external comparison.

**Labels:** names on the thing; the **dreaded letter code** (A/B/C → distant legend) is the last resort; when the image is too dense/precious, an adjacent profile-outline diagram is the legitimate workaround.

**Explanatory vs. exploratory:** explaining → annotate aggressively (Peterson pointer-keys); exploring → premature mapping forecloses readings — show the clean image first, and show unmapped + mapped versions so the viewer can audit the mapping.

**Explanatory tightness — credible vs. crank mapping:** a mapping is a claim and must be specific, coherent, credible, testable. Crank mappings (Mössel's Ur-Forms, golden-section-everywhere) fit everything: "no possible empirical evidence can ever refute a Mössel, who explains everything and therefore nothing." Why they always "work": too many degrees of freedom; alignment-to-please (±3° free by tilting your head; build the mapping blind to the wanted answer); the flatland–spaceland mismatch (mapping one flat photo of a 3-D object and claiming truths about the object).

**Motion in still-land:** small multiples with a constant frame (the 1762 contredanse: 8 movements, figures + floor-plans + tracks + music per cell); comparison images must share one scale/grid — "looks bigger" is not a measurement.

**The Vigilante (1823):** plan/elevation/cross-section of a slave ship with a Scale of Feet, water line, and 347 counted figures — engineering-diagram precision is what makes the moral evidence undeniable.

**Failure modes:** different-and-unknown scale; dequantified celebratory image (deep-space PR shots the least quantified); dreaded letter code; flatland–spaceland mismatch; unfalsifiable mapping; alignment-to-please / premature closure.

---

## Redundant & Multi-Channel Encoding (EI ch. 3–5 synthesis)

"INFORMATION consists of differences that make a difference." Riding one variable on multiple channels is defensible exactly when the extra channel buys separation, robustness across media, or accessibility — never "completeness."

**Three outcomes — diagnose with the channel-removal test:** delete one channel. Still fully readable → **redundant** (keep only with a named purpose). A layer of meaning lost → **layering** (always justified; don't cut it to "save ink"). Clearer without it → **collision** (1+1=3 noise; cut).

**Colliding pairs:** heavy rule + adjacent type; box + word; near-equal hue + saturation; pattern fill + hue (moiré); dark grid + data trace. **Reinforcing pairs:** color field + contour edge (different perceptual systems); shape + color (shape survives grayscale/photocopy); position + direct label; gray grid + data.

**Swiss map — redundancy done right:** altitude on hypsometric color (gestalt) + contour lines (precise value; density = steepness) + shadow hachure (rate of change). Any one channel legible; the stack survives grayscale, reduction, and color-deficient viewing — fault tolerance, not decoration. Imhof's co-registration constraint: color boundaries must align exactly with contours or a phantom step-edge appears.

**Cyclic redundancy:** repeat a cyclic axis so the longest continuous feature plots unbroken (Marey's schedule; ocean currents at "one and two-thirds times around") — no new information, removes an arbitrary cut; size the overlap to the longest path, not a round number.

**Small-multiple connection:** mute the repeated frame, foreground the differentiator; keep comparisons in one eyespan; dark surrounds breed white stripes.

**Accessibility extension (post-Tufte, consistent with the robustness argument):** ~8% of males CVD (red/green collapse). Stack in order: (1) value/lightness monotonic with the data — design the grayscale version first; (2) hue via perceptually uniform ramps; (3) shape/texture per category; (4) direct label. Contrast floor: WCAG 4.5:1 text, 3:1 large text and meaningful graphical objects — apply 3:1 to data marks.

**Warrant test, in order:** removal → interference at smallest size → named purpose (separation / robustness / accessibility / cyclic continuity — else erase) → field check (saturated color confined to small extremes on a muted ground, edges co-registered).

---

## Typography for Data (SWFE ch. 2; EI; VDQI; BE)

"Typography exists to honor content" (Bringhurst, cited by Tufte). The governing split: **content-responsive** (space and linebreaks driven by the data's structure) vs. **content-hostile** (production grids, squared margins, legend boxes). On screens the marginal cost of space is zero — grid-driven layouts are now a choice, not a constraint.

**Linebreaks:** break lists at existing commas/semicolons/stops, one element per line (the Ioannidis six-condition list; Maugham's clauses). **Darwin calculation:** re-setting 133 topic lists costs +2–3 pages in a 500-page book and removes ~2–5 billion reader impediments accumulated since 1859. Alignment as signal: ragged-right general; centered lets the eye see the next line's length; ragged-left marks the speaker. Poetry (the line as meaning) and code (KMP ≈ 37 lines, ~75% whitespace — minify and it's unreadable) are the models.

**Idiosyncratic paragraphs:** typographically uniform paragraphs defeat memory retrieval; give tables, code, callouts, quotations distinct treatments so passages can be re-found.

**LittleDataGraphics:** pies and small bars encode a tiny dataset into areas/angles the viewer must decode back — a one-off local code with zero transfer. For small data, show the numbers as numbers, or a data paragraph (NWS briefing: 18 measurements, 28 words, 4 links, serving expert and casual reader from the same ink).

**Direct labels over legends:** a legend is a memorized code and can eat >40% of a display — "trillions of legends — coffins of dead conventions." Placement priority: line terminus → adjacent to the characteristic feature → leader line from whitespace → never a detached box when direct placement is possible. Swiss topo maps: type size IS a data dimension (BERN → Sumvitg → *Le Plan* → smallest italic for a single house).

**New Haven timetable (EI pp. 104–107):** 21% of area for actual times; 41 in of rules; headings ×3, 24 AM/PM markers; redesign in Bell Centennial with a quiet dot replacing the active colon.

**Weight hierarchy:** data series heaviest → labels/annotations medium → axis labels medium → ticks/grids hairline → frames hairline/none → legend border eliminated. Type parallel: never bold the structure while data values sit light.

**Annotation as evidence:** annotated Galileo sketches are evidence; unannotated are pictures. Scale bars are part of the news. Density test: remove every label — still self-explanatory → labels were redundant; ambiguous → they were evidence, keep them.

**Typeface for data:** legible at 6–8pt; distinct 0/O 1/l/I 6/G 5/S; light regular weight; **tabular lining figures mandatory in aligned columns**; avoid all-caps at points of semantic ambiguity; Bell Centennial for dense schedules.

**Failure modes:** LittleDataGraphics; content-indifferent linebreaks; legend tax; inverted weight hierarchy; scale suppression; clotted lettering; serpentine reading; rotated (90°) labels — stretch horizontally or transpose instead; active punctuation in dense data; unanchored annotation; uniform paragraph styling.

---

## Visual Thinking — Seeing With Fresh Eyes (SWFE, 2020)

Visual thinking and analytical thinking are one cognitive act; the shared enemy is the self-confirming word — the inherited name or default model accepted without looking.

**SEE–REASON–ACT:** See intensely, actively, skeptically, at multiple scales, with "vacation eyes" — forget the name of the thing. Defamiliarization sequence: defamiliarize → decontextualize → recontextualize → remodel. Reason about **verbs** — what things DO, not what they're called; standing questions: "How do I really know that?" / "How could I ever know that?" Act: producing and remodeling divide spectator from player, anecdote from evidence.

**Seeing vs. naming:** the Big Dipper's stars sit at 58–124 light years — the "dipper" is a viewpoint artifact (kite at 50,000 BCE, swan at 50,000 CE). Named failure — **Flatland Projection**: reasoning from a 2-D model as if it were the 3-D reality.

**Space as content:** ghostlier grids allow keener distinctions (Bell Burnell's pulsar traces; Marey's ghost grids; Curie/Pauling/Knuth notebooks). **Grid Dominance** failure: a medical interface whose loudest elements were cyan grid bars; an image matrix only ~42% images. Ghosted global context: FT COVID small multiples — each country foregrounded against all others grayed behind. Image quilts: unframed, abutting, varied sizes — over-framing blocks comparison. Remodel scatterplots with images of the actual things at their coordinates (brain vs. body mass with little animals — self-labeling); remodel spreadsheet cells with sparklines (264-sparkline PAC-MAN memory map).

**Models:** to choose a model is to choose its unseen assumptions. **Discipline Capture:** insiders control what counts as evidence; reform comes from outsiders (Berners-Lee, Tversky & Kahneman). **Default Format Acceptance:** "We've always done it this way" (Hopper: the most dangerous phrase). Maps are the outsider comparison set — they already solved color, content-located type, density, simultaneous diverse users.

**Graphical sentences:** an unannotated arrow x→y asserts nothing; a link should be a sentence with subject, verb, object (1957 Disney profit diagram: 37 graphical sentences — "feeds record material," "provides interchange of stars"). **Stacklists** organize complex material in 2-space (Galileo's copy of Ausonio's mirror diagram: a 218-word, 29-branch tree). Fox vs. hedgehog (Berlin) as a model-quality frame: many-ends skeptics vs. one-big-idea believers; precision medicine (n=1) vs. vaccination (n≈3B).

**Data-analysis integrity:** Feynman — "you must not fool yourself, and you are the easiest person to fool"; Mosteller — "It is easy to lie with statistics; it is easier to lie without them." Prevalence: image duplication 3.8% of 20,621 papers (~half deliberate); Excel gene-name errors in ~20% of supplementary lists (704 papers); only 44% of medical articles even mention measurement error, and 7% of those address it; 267 secondary articles cited retracted Mediterranean-diet data; of 522 biostatisticians surveyed, reported requests included deleting records and suppressing missing data. **Sampling to Please:** the river-polluter's boat dips for the cleanest-looking water — observe data at the moment of measurement. Three traceability questions (Lucent 2002): traceable to primary data? evidence the data don't come from the described measurements? mitigating circumstances? Forensic audit ≠ data cleaning (cleaning fixes duplicates, not bias/falsification/too-good-to-be-true).

**Clarity vs. simplicity:** for complex data, simplicity is dishonest and clarity is required — **False Simplicity** presents the simpler model as reality. **Cute Puppy Problem:** abstractions can't be compared, only concrete instances can (Kocienda: demos). **Empty-Head Remodeling:** skepticism without standards.

**Fresh-eyes checklist:** name the model and its assumptions; what does the 2-D projection lose?; what does the content DO?; outsider comparison set pulled in?; any grid louder than the data?; space doing work?; format = content's shape or the production system's?; complexity shown honestly?; concrete and specific?; links annotated with verbs?; data traceable to the moment of measurement?; fox or hedgehog — optimizing locally at the cost of global pessimizing?

---

## Master Audit — Run Before Shipping Any Data Display

1. **Format:** does this deserve a graphic at all (vs. sentence/table/supertable)? Right form: map, time-series, space-time narrative, scatterplot, small multiples, sparkline, table?
2. **Truth:** Lie Factor 0.95–1.05; visual dims ≤ data dims; money deflated + per-capita; one continuous scale; context answers "compared with what?"
3. **Ink:** two-pass erasure done; frames → range-frames; ticks → data rugs; grid gray or gone; no fills/3-D/shadows; recovered space spent on labels.
4. **Chartjunk:** no moiré fills, no dark grids, no ducks.
5. **Density:** matrix as large as the question warrants; graphic shrinkable by half?; marks sized to n; density is data, not decoration.
6. **Multivariate:** how many variables does the phenomenon have vs. shown? Small multiples or layering available?
7. **Comparison:** everything compared sits in one eyespan; like against like (same scale/orientation/crop); causal variable on the axis; all data including zero-effect cases; decision boundary drawn.
8. **Layering:** weight ∝ importance; 1+1=3 effects hunted; large areas muted, small extremes saturated; nothing boxed.
9. **Color:** role named (label/measure/represent/decorate); light→dark for quantity; ≤ ~7 categories; no red/green solo; non-color backup for critical distinctions.
10. **Type:** direct labels, no legend; horizontal; tabular figures; weight hierarchy; content-responsive linebreaks; scale bars on images.
11. **Documentation:** author, sources, scales, units, date, assumptions on the display itself.
12. **Integrity:** data traceable to measurement; no cherry-picked baselines, bins, or models; disconfirming cases shown; the headline is the actual finding.
