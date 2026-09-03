# The Other Half — e-bike safety in Irvine

An informational website about Adriana's e-bike safety project: the research, the
argument, and the proposal she's bringing to the Irvine City Council. It's built
to stand on its own for anyone who finds it, and to double as the backdrop for
her three-minute public comment.

Everything lives in `index.html`. No build step, no dependencies, no server —
open the file and it works, including from a USB stick with no wifi.

## Two ways to use it

**As a website.** Scroll or use the top nav. A visitor who has never heard of any
of this can read the problem, what the Council already did, the proposal, the
options that were ruled out, and an FAQ, then check the sources.

**As a presentation.** Click **Present** in the nav, or press <kbd>P</kbd>. The
page strips down to the projected version: nav and body prose disappear, each
section fills the screen, and the headlines and numbers scale up. Advance with
<kbd>→</kbd>, <kbd>↓</kbd>, or <kbd>space</kbd>; go back with <kbd>←</kbd>.
<kbd>Home</kbd> and <kbd>End</kbd> jump to either end. <kbd>Esc</kbd> or
<kbd>P</kbd> returns to the website.

Presentation mode shows eight sections — the argument, in speech order. The FAQ,
About, and footer are skipped, since they're for readers rather than the room.

For the actual presentation, press <kbd>F11</kbd> (Windows) or <kbd>⌃⌘F</kbd>
(Mac) for fullscreen first. Ordinary scrolling still works in both modes, so
nothing breaks if a clicker sends scroll events instead of arrow keys.

## Sections

| Section | In presentation | Purpose |
|---------|:---------------:|---------|
| Hero | ● | Who she is, what this is |
| The problem | ● | Statistics, e-bike classes, failure modes |
| What passed | ● | Ordinance 26-05, fairly described |
| The gap | ● | Why enforcement is only half |
| The proposal | ● | The two asks, explained |
| Four pillars | ● | The longer program |
| Options weighed | ● | Research depth, for questions |
| Closing | ● | The last line |
| FAQ | — | Fair objections, answered |
| About & sources | — | Who, why, and where the numbers come from |

## Before publishing or presenting

**Verify the facts.** Every Irvine-specific claim comes from
`Public Policy Adriana.pdf` and none of it has been independently checked.
Confirm each against the Council's own minutes:

- The 50% / 69% collision statistics attributed to Police Chief Michael Kent.
- Ordinance No. 26-05, its 6–1 vote, and that it amends Division 7 of Title 4.
- The "a full-blown crisis" quote attributed to Mayor Agran.
- Councilmember Carroll as the lone no vote, objecting to sidewalk speed limits.

**One contradiction to resolve.** The research notes date the ordinance to
January–February 2026, but the speech draft says "Last November, Chief Kent told
this Council." Those can't both be right. The site deliberately avoids naming a
date — pin it down and add it back if you want the specificity.

**Background that wasn't in the source document.** The "What the classes mean"
panel (Class 1 / 2 / 3 e-bike definitions) is general California vehicle code,
added so a stranger to the topic can follow the argument. It's standard, but
it's not from Adriana's research — check it before she's asked about it.

**Fill in the placeholder.** The About section has a `you@example.com` contact
link. Replace it or delete the sentence.

## Editing

Each section is one `<section>` with two layers:

- `.stage` — the visual: headline, statistic, card, or table. Always visible.
- `.prose` — the explanatory writing. Hidden in presentation mode.

Put anything meant for readers in `.prose`, and anything meant for the projector
in `.stage`. Add `data-present="skip"` to a `<section>` to leave it out of the
presentation entirely.

The palette and type scale are CSS custom properties at the top of the file:

```
--asphalt      page background      --lane        green: the proposal
--thermo       primary text         --amber       amber: the problem
--asphalt-lift raised panels        --sign-red    red: used once, for the quote
```

Color carries the argument — amber marks the problem, green marks what she's
asking for, red appears exactly once. Keep that mapping if you add sections.

### If the venue has no internet

The three typefaces (Archivo, Source Serif 4, DM Mono) load from Google Fonts.
Without a connection they fall back to Helvetica, Georgia, and the system mono —
the layout holds, it just looks less distinctive. To make it fully offline-proof,
download the font files and swap the `<link>` for a local `@font-face` block.
