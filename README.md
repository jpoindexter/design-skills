# design-skills

**Design Skills — 18 agent skills.**

Cross-platform design fundamentals — tokens, layout, components & states, color & elevation, accessibility, iconography, UX writing — with a dispatcher that routes tasks to the right skill.

Works with any agent that reads markdown skills: Claude Code, Codex CLI, Gemini CLI, Copilot, Cursor.

## Install

```bash
npx skills add jpoindexter/design-skills
```

Or manually: clone and symlink the folders under `skills/` into your agent's skills directory (e.g. `~/.claude/skills/`).

## The Skills

| Skill | Covers |
|---|---|
| [`accessibility-and-inclusive-design`](skills/accessibility-and-inclusive-design/SKILL.md) | Reference-grade guide to shipping WCAG 2.2 AA accessible, inclusively designed interfaces across web, native iOS/Android, and desktop — semantic-first markup… |
| [`app-motion-and-animation`](skills/app-motion-and-animation/SKILL.md) | Platform-agnostic motion principles for any app — the six purposes of motion and when NOT to animate, the perception thresholds (~100ms instant, 230ms percei… |
| [`color-and-elevation`](skills/color-and-elevation/SKILL.md) | Build perceptually-uniform color palettes and physically-consistent depth systems with OKLCH ramps, WCAG/APCA contrast, semantic tokens, and elevation-as-lig… |
| [`components-and-states`](skills/components-and-states/SKILL.md) | Reference-grade guide to designing and building UI components — anatomy, the full interaction-state matrix, variants vs sizes vs states, sizing tokens, per-c… |
| [`data-visualization`](skills/data-visualization/SKILL.md) | Choose, encode, color, label, and ship accurate accessible charts and dashboards — perceptual encoding ranking, chart-by-intent selection, data color scales,… |
| [`dense-no-scroll-layout`](skills/dense-no-scroll-layout/SKILL.md) | Designing mobile screens that fit one viewport with minimal vertical scrolling — viewport budgeting per device, above-the-fold prioritization, swapping tall … |
| [`design`](skills/design/SKILL.md) | Use when the user invokes /design, or asks to design/build/audit/polish any web or cross-platform UI — screen, component, layout, table, chart, form, color s… |
| [`design-tokens`](skills/design-tokens/SKILL.md) | Architect, name, format, and export design tokens as the single source of truth across Figma, code, and multi-platform builds using the W3C DTCG format, a pr… |
| [`ethical-design-and-dark-patterns`](skills/ethical-design-and-dark-patterns/SKILL.md) | Reference-grade guide to ethical interface design and the recognized deceptive-pattern taxonomy (Brignull / deceptive.design × Mathur et al.) — every dark pa… |
| [`grid-and-spacing`](skills/grid-and-spacing/SKILL.md) | Reference-grade system for spacing scales, column/baseline grids, responsive breakpoints, and modern CSS Grid/container-query layout built on an 8pt base wit… |
| [`iconography-and-imagery`](skills/iconography-and-imagery/SKILL.md) | Reference-grade guide to building and shipping icon systems (grids, optical sizing, variable axes, SVG delivery) and imagery (aspect ratios, art direction, m… |
| [`inclusive-design`](skills/inclusive-design/SKILL.md) | The inclusive-design philosophy and practice — Microsoft's 3 principles + Persona Spectrum, the social model of disability as mismatch, and deep cognitive, n… |
| [`interaction-and-motion`](skills/interaction-and-motion/SKILL.md) | Reference-grade motion and micro-interaction system — duration scales, easing tokens, choreography, modern CSS (view transitions, scroll-driven, @starting-st… |
| [`laws-of-ux-and-psychology`](skills/laws-of-ux-and-psychology/SKILL.md) | Reference-grade catalogue of the attributed cognitive laws behind interface design (Fitts, Hick-Hyman, Miller, Jakob, Tesler, Postel, Doherty, Peak-End, and … |
| [`layout-and-composition`](skills/layout-and-composition/SKILL.md) | Reference-grade system for composing any screen — visual hierarchy, Gestalt grouping, alignment, whitespace, scanning patterns, and modern intrinsic CSS layo… |
| [`tufte`](skills/tufte/SKILL.md) | The complete Edward Tufte canon (VDQI, Envisioning Information, Visual Explanations, Beautiful Evidence, Seeing With Fresh Eyes) as one skill — apply when de… |
| [`usability-heuristics`](skills/usability-heuristics/SKILL.md) | Reference-grade guide to the canonical usability principles — Nielsen's 10 heuristics, Norman's design fundamentals, Shneiderman's 8 golden rules, Rams' 10 p… |
| [`ux-writing-and-content`](skills/ux-writing-and-content/SKILL.md) | Reference-grade guide to UX writing and content design — voice and tone systems, every UI string type with before/after examples, terminology consistency, in… |

## License

MIT — see [LICENSE](LICENSE).
