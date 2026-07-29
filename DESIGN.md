# Design

<!-- impeccable:design-schema 1 -->

## Visual World

Manga panel. The tracker reads as a page from a Hunter x Hunter action chapter — thick black ink borders, offset paper shadows, halftone screentone shading, katakana ruby labels, and one electric-blue spot color for Killua's lightning. Cream paper ground, pure black ink, dynamic panel arrangements. Each server is a manga panel, not a card. Big Anton display type sits on the page like a chapter title. Sound-effect words are lettered, not styled. The page is dense with content because a manga page is dense; whitespace exists only inside panels, not between them.

## Color Language

| Role | Token | Value |
|---|---|---|
| Paper | `--paper` | `#f6f1e4` |
| Paper-2 | `--paper-2` | `#ede6d3` |
| Ink | `--ink` | `#08080a` |
| Ink dim | `--ink-dim` | `#454548` |
| Ink mute | `--ink-mute` | `#7a7a7d` |
| Halftone | `--halftone` | `rgba(8, 8, 10, 0.22)` |
| Bolt (accent) | `--bolt` | `#00a5ff` |
| Bolt strong | `--bolt-strong` | `#0080d4` |
| Bolt paper | `--bolt-paper` | `#c9ecff` |
| Blood | `--blood` | `#d93441` |
| Warning | `--warning` | `#e3a02a` |

Strategy: **Ink on paper**. Cream paper is 65% of the surface. Solid black ink is the second color, used at 25% coverage (borders, fills, type). Electric bolt-blue is the single spot color, reserved for the primary action (CONNECT), the live LED, and the header number for players online — never used for supporting UI. Blood-red only for offline/error. Warning-amber only for outdated version.

## Typography

- **Display:** Anton (400). Huge, condensed, all-caps. Sits on the page like a chapter title or panel headline.
- **Katakana / decorative Japanese:** Noto Sans JP (700, 900). Used as ruby-style secondary labels above or beside display type — a real second language on the page, not decoration mistaken for English.
- **Impact / sound effects:** Bungee (400). Reserved for interactive-state labels like "LIVE", "GO", "LOST" — sound effects lettered into the page.
- **Body:** Special Elite (400). Typewriter-feel serif for server names, narration, and roster names. Reads as inked lettering.
- **Numeric / tabular:** JetBrains Mono (500, 700). Addresses, durations, timestamps — everywhere a monospaced digit matters.

## Composition

- Paper page, full-bleed. No centered content column — panels extend edge-to-edge with 12px paper margin.
- **Chapter head:** Title bar reads "第一話 // SGP HVH" with the katakana huge and the roman text as furigana; a solid black band underneath with the live LED and refresh action.
- **Splash panel:** Full-width, offset-shadow, halftone-shaded panel with the SG flag as a solid ink block, oversized display copy in the middle, and the PLAYERS ONLINE giant number in electric blue on the right.
- **Stat panels:** Three small side-by-side panels for servers tracked / watching / status. Each has a katakana label above and a mono value inside.
- **Server panels:** Each server is a full-width panel, ink-bordered with 5px offset shadow. Layout inside is: left ink-block (halftone with server number "NO. 01"), server name huge in Special Elite, katakana subtitle, stat row (players / map thumb / region), big blue CONNECT action panel and copy IP action.
- Player rosters open below each panel as a nested speech-bubble style list with mono names.
- Panel numbering runs continuously ("NO.01", "NO.02", "NO.03") like manga panels on a page.

## Component Language

- **Panels:** 3px solid `--ink` border, 6px solid `--ink` offset shadow (bottom-right), no border-radius. Halftone screentone SVG background allowed at low opacity for shaded areas.
- **Panel tags:** Small ink-outlined tag ribbons at top-left of each panel with panel number and katakana glyphs.
- **Live LED:** Solid ink circle with a red dot inside, pulses on a slow 1.4s beat.
- **Buttons:** Rectangular, thick black border, offset shadow. Primary (CONNECT) fills with `--bolt` and has white ink type. Press animation snaps the shadow to zero offset and slides the button 3px right + 3px down (like a real button press).
- **Pills / tags:** Black ink outline pills, uppercase Special Elite type. Status uses a colored dot inside the pill.
- **Sound-effect banner:** When status changes, a Bungee-lettered sfx word (LIVE!, LOST!, WAIT!) appears in the corner of the status panel.

## Motion

- Panel entrance: 8px slide-up + 200ms shadow-collapse-to-full — appears one at a time on first load only.
- Button press: `translate(3px, 3px)` + shadow offset drops to `0 0` in 80ms.
- Live LED: `opacity` pulse 1.4s between 0.35 and 1.
- Panel hover (server panels): lift by 2px in top-left direction, deepen shadow to 8px offset.
- Reduced motion: no slide-in, no shadow shift, LED stays static.

## Responsive

- 900px: Splash panel stacks flag + copy + score vertically. Stat panels stay 3-wide.
- 640px: Server panels reduce inner grid to two rows: name over stats-row / action panel below.
- 440px: Chapter head simplifies to just the title, refresh + status move below.

## Name

"CS2 HVH" as the roman title. Furigana-style katakana `シービーツー・エイチブイエイチ` above it in the chapter head. `HVH` gets a bolt-blue underline.
