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
| Hero | ● | Aerial of Irvine, the headline, the asks |
| Intro | — | Who she is and what the page is |
| Poster | — | The Irvine Safe Ride campaign poster |
| Team | — | Portraits of the people involved |
| The problem | ● | Statistics, e-bike classes, failure modes |
| What passed | ● | Ordinance 26-05, fairly described |
| The gap | ● | Why enforcement is only half |
| The proposal | ● | The two asks, explained |
| Four pillars | ● | The longer program |
| Options weighed | ● | Research depth, for questions |
| Closing | ● | The last line |
| FAQ | — | Fair objections, answered |
| About & sources | — | Who, why, and where the numbers come from |

## Sources — verified September 2026

Every factual claim on the page now carries a superscript citation linking to the
Sources list at the bottom. The five sources are real and were checked against
primary reporting and official pages:

1. **Collision figures, the 6–1 vote, the dissent** — Lt. Shaheen Jahangard, Irvine
   PD traffic bureau, to the City Council; reported by *Voice of OC*, 2 Feb 2026.
2. **Ordinance No. 26-05** — City of Irvine staff report (Granicus). Amends Division
   7 of Title 4; first reading 27 Jan 2026, back before Council 10 Feb 2026.
3. **The Agran quote** — Irvine City Council, 12 Nov 2025; reported by *Voice of OC*,
   3 Dec 2025.
4. **E-bike classes and helmet rules** — Irvine Police Department's own guide.
5. **The CHP safety course** — AB 544, via the California Highway Patrol.

### What the research document got wrong

The original `Public Policy Adriana.pdf` had four errors. All are fixed on the site,
**but the speech draft in that PDF still contains them** — it needs the same edits
before she delivers it:

| Claim in the PDF | What the sources actually say |
|---|---|
| "about half" / 50% of bicycle collisions | **53%**, per the IPD traffic bureau |
| Attributed to **Police Chief Michael Kent** | The 53%/69% figures came from **Lt. Shaheen Jahangard**. Kent spoke at the November 2025 meeting, but these numbers are Jahangard's |
| Agran's "full-blown crisis" said at the ordinance vote | Said at the **12 November 2025** meeting, two months earlier. Full quote: "We're in the midst of a full-blown crisis that is not soon to go away" |
| "Councilmember Carroll" | **Mike Carroll** |

Two things I had added were also wrong and are corrected: Class 3 e-bikes are
defined by a 16-year age minimum and a helmet requirement (not by being "most often
involved when speed is a factor" — I made that up), and AB 544 lets a minor cited
for a *helmet violation* clear it with the CHP course, rather than requiring all
cited minors to take one.

### Still worth checking

- The Granicus staff report is a **scanned PDF**, so its text could not be read
  directly. The ordinance details come from that document's listing plus the *Voice
  of OC* reporting. Confirm the adoption date at the 10 February 2026 meeting.
- A second figure the traffic bureau gave — ~70% of collisions over three years
  involved a juvenile rider, ~65% of those an e-bike — is on the page but is a
  different measure from the 53%/69% pair. Don't mix them in the speech.

### The "more than 1 in 3" figure

The bar chart derives it: 53% × 69% ≈ 37 in every 100. That multiplication is
labelled as arithmetic in the caption, because it is **not** a separately reported
statistic. If anyone asks, the two source numbers are the citable ones.

**The hero image.** The header is a full-bleed aerial of Irvine — the arterial
grid, the curvilinear villages, and the Woodbridge lakes — under a navy scrim
that keeps the headline readable. The file is `irvine-aerial.jpg`.

It came from the **USGS National Map orthoimagery service**, which is US federal
imagery and therefore public domain: free to use, including for a public
presentation, with no attribution required. It's credited in the corner of the
hero anyway, as good practice. The exact request was:

```
https://basemap.nationalmap.gov/arcgis/rest/services/USGSImageryOnly/MapServer/export
  ?bbox=-117.855,33.6692,-117.755,33.7108&bboxSR=4326
  &size=2400,1200&imageSR=3857&format=jpg&f=image
```

Change the `bbox` (west,south,east,north in degrees) to re-frame on a different
part of the city, then re-export at quality ~55 to keep it near 600–700 KB.

To use a different photo, replace `irvine-aerial.jpg` or point the `<img>` inside
`<div class="hero-bg">` at a new file — the CSS crops and scrims whatever you
give it. Make sure it's a photo Adriana took or is licensed to use.

Do not substitute an AI-generated "photo" of Irvine. A synthesized image of a
real city, shown to that city's own council, would undercut the credibility the
rest of the page is built on.

**Adjusting the scrim.** If a replacement photo is brighter or busier and the
headline stops reading, raise the alpha values in the two `.hero-bg::after`
gradients — the first darkens top-to-bottom, the second left-to-right where the
headline sits.

**The campaign poster.** The section under the intro reproduces
`Irvine safe ride official poster!.html` at its native 1200 x 1800 and scales it
to fit, so the type stays real text rather than a flattened screenshot. Its own
palette (stone, cream, Fraunces) is intentional and is scoped under `.poster`, so
it can't leak into the rest of the page.

The photo was extracted out of the original file's base64 into `poster-rider.jpg`
so the browser can cache it and `index.html` stays small. Edit the poster's text
directly in the `<section id="poster">` block; the original file is still in the
repo and linked underneath the poster.

Scaling is set by a few lines of script (`--poster-scale` = frame width / 1200).
The CSS default matches the 880px maximum, so the poster still looks right on a
desktop if the script never runs.

**⚠ The poster contradicts the speech.** This one matters. The poster asks the
Council to *"adopt the e-bike safety ordinance — helmets on, speeds down"*, and
its second card asks them to *"set and enforce clear speed limits on sidewalks,
trails."* But the rest of the page argues that Ordinance 26-05 already did
exactly that, and the options table explicitly rules re-proposing enforcement out
of the three minutes: *"26-05 covers it. Re-proposing it wastes the three
minutes."*

As it stands the page argues against itself. The poster's third card ("pair
enforcement with real safety education") is the only one that matches the actual
ask. The fix is to rewrite the poster's ask line and first two cards around the
education pilot and the reporting map — the photo, layout, and headline all still
work. Until that's resolved the poster is set to `data-present="skip"`, so it
stays off the projector during the speech; remove that attribute to include it.

**The team section.** `#team` sits between the FAQ and About. Eight portraits in a
responsive grid (4 across on desktop, 3 on tablet, 2 on phone), each cropped to 4:5.

Photos live in `photos/team/person-1.jpg` … `person-8.jpg`, resized to 1000px on the
long side (~60–140 KB each). The full-resolution originals are in `photos/originals/`
— about 11 MB, so delete that folder before pushing if you have them elsewhere.

Displayed in this order; the filenames stay tied to the photos, not the position:

| Order | Name | Title | File |
|---|------|-------|------|
| 1 | Adriana Lee | Founder | `person-7.jpg` |
| 2 | Denes Garda | Webmaster | `person-8.jpg` |
| 3 | Kailen Lee | Outreach Officer | `person-1.jpg` |
| 4 | Jia Yoon | Research & Data | `person-2.jpg` |
| 5 | Harrison Nguyen | Writing & Research | `person-3.jpg` |
| 6 | Alex Lin | Treasurer | `person-4.jpg` |
| 7 | Caroline Lu | External Affairs | `person-5.jpg` |
| 8 | Sophia Nagel | Marketing | `person-6.jpg` |

To reorder again, move the `<div class="member">` blocks in `#team`.

Framing uses `object-position` per image rather than cropped files, so nothing is
destroyed and any portrait can be nudged without re-exporting.

- **Two photos are stylistically off** from the rest: Sophia's is a bathroom mirror
  selfie and Caroline's is a travel snapshot, while the other six are plain-background
  headshots. They work, but a consistent set would look considerably better.
- **Consent**: full names now sit beside faces, several of them young. Get everyone's
  agreement — and a parent's for anyone under 18 — before this page goes public.

### About copy

The "Why I built this" text is Adriana's own, lightly reworked to read as a web page
rather than an email. Four editorial calls worth knowing about:

- **"about half" became 53%.** Her draft said about half; the site uses the cited
  figure everywhere else, and two different numbers on one page invites a question
  she doesn't need.
- **"provided by Michael Kent" is not on the page.** The published 53% / 69% figures
  were given to the Council by Lt. Shaheen Jahangard of the IPD traffic bureau. Chief
  Kent spoke at the November 2025 meeting but those specific numbers are Jahangard's.
  If Kent supplied the data to Adriana directly then her sentence is true and should
  go back in, worded so it doesn't read as the source of the published statistic.
- **The incident is described without assigning blame.** Her draft said the child was
  "playing around with no parental supervision." The page says "while out riding with
  no adult around." Same fact, and it avoids a public page blaming an unnamed
  neighbour's family, which also sits badly next to her own argument that this is a
  systems problem rather than a parenting one.
- **"It isn't an organization" is gone.** Her text calls Irvine Safe Ride an
  independent community initiative, which settles the positioning question raised
  below. The footer disclaimer now says it isn't affiliated with the City or IUSD,
  which is the part that actually matters.

### ⚠ Three different versions of the ask are now on one site

This is the thing to fix before anyone reads the page end to end.

| Where | What it asks for |
|---|---|
| **The Proposal section** | Safety workshops at one school with IUSD, plus a crowdsourced crash-reporting map |
| **The poster** | Require helmets, enforce speed limits, support families |
| **About (new)** | Protected bike lanes on school routes, a required under-16 course with IUSD, quarterly public collision reporting |

Only the IUSD course appears in all three, and even then the Proposal section asks for
a voluntary pilot while About says "required."

Two direct contradictions:

- The options table rules protected infrastructure out of the near-term ask
  ("Phase two. Study and pilot one corridor, not a citywide overhaul"), but About now
  leads with protected bike lanes.
- "Why so small" argues that a council will fund a small pilot and send a multi-part
  programme to committee, while About describes a three-part programme.

The likely explanation is that the proposal moved on and the Proposal section, written
from the original research PDF, is the oldest thing on the page. If that's right, the
fix is to rewrite the Proposal section, the options table verdicts and the "Why so
small" paragraph around the three current asks, and to revise the poster to match.
That is a real editing pass rather than a find and replace, so it needs a decision
first: which three asks is she actually taking to the Council?

### ⚠ The team titles contradict the site's copy

The page is written throughout as **one resident acting alone**. That framing is not
decorative; it is what makes a three-minute public comment land as a citizen speaking
rather than a group lobbying. The team titles now say something different, and in two
places they directly contradict sentences already on the page:

| On the page now | In the team section |
|---|---|
| "It isn't a campaign and it isn't an **organization**. It's **one resident** with a proposal" (About) | Founder, **Treasurer**, External Affairs, Outreach Officer |
| "This is **my own research**, gathered on **my own time**" (About) | Jia Yoon, **Research & Data** |
| "An independent project" (hero) | An eight-person officer structure |

A *Treasurer* in particular implies funds and a constituted body. A reader — or a
councilmember — who scrolls from "it isn't an organization" to a treasurer will notice.

Two coherent ways to fix it, and it is a positioning call rather than a copy edit,
so I have not picked one:

1. **It is an organization.** Rewrite the About paragraph and the hero meta to say so
   — a student-led initiative with Adriana as founder. Honest, and the officer titles
   then make sense. Costs the "just a resident" advantage at the podium.
2. **It stays a personal project with helpers.** Keep the solo framing and soften the
   titles to contributions (Outreach, Research, Writing, Design) rather than offices —
   drop Treasurer and Founder. The team page then reads as "people helping," which
   matches the rest of the site.

Whichever you choose, the About paragraph and the hero's "An independent project"
line need to agree with it.

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
--paper      #ffffff   page background
--paper-tint #f1f7fc   raised panels, cards
--rule       #cfe0ee   hairlines and dividers
--navy       #0d2b4e   headlines, body text, the weight
--navy-deep  #07203c   emphasis inside body copy
--navy-soft  #5c7793   captions, secondary text
--sky        #2e9bd6   light blue: rules, fills, large accents
--sky-ink    #0f6ea8   light blue for small text (--sky fails contrast there)
--sky-pale   #eaf5fc   tinted fills
```

Color still carries the argument, but through weight rather than hue: **navy is
the problem and the settled ground, light blue is the proposal.** The statistics
are heavy navy; the asks, the open half of the gap bar, and the two accented
headline words are blue. The "full-blown crisis" quote is white knocked out of a
solid navy block — the one loud moment on the page.

One rule to keep: `--sky` is 3.1:1 on white, which passes for large text, rules,
and borders but **fails for body-size text**. Use `--sky-ink` anywhere the type
is under ~24px.

## Favicon and GitHub Pages

`favicon.svg` is the icon: a bike in white on a navy tile, drawn at a 32-unit grid so
it still reads at 16px. The solid tile matters, since a bare outline disappears
against a dark browser chrome. Two rasterised fallbacks sit beside it,
`favicon-32.png` for browsers that don't take SVG icons and `apple-touch-icon.png`
(square and full-bleed, because iOS composites transparent corners onto black and
applies its own rounding).

Regenerate the PNGs after editing the SVG:

```sh
qlmanage -t -s 512 -o . favicon.svg
sips -s format png -z 32 32 favicon.svg.png --out favicon-32.png
sed 's/ rx="7"//' favicon.svg > sq.svg && qlmanage -t -s 512 -o . sq.svg
sips -s format png -z 180 180 sq.svg.png --out apple-touch-icon.png
rm -f sq.svg sq.svg.png favicon.svg.png
```

**The icon paths are relative on purpose.** A GitHub Pages *project* site serves from
`https://<user>.github.io/<repo>/`, so `/favicon.svg` would 404. Every asset path on
the page is relative for the same reason. If you ever move this to a user site or a
custom domain the relative paths still work, so leave them alone.

A `.nojekyll` file is in the repo root. GitHub Pages runs Jekyll by default, which
skips files beginning with an underscore and can surprise you; `.nojekyll` tells it to
serve the directory as-is.

One thing to fix before deploying: the poster file is named
`Irvine safe ride official poster!.html`. The link on the page is URL-encoded so it
works, but a filename with spaces and an exclamation mark is asking for trouble.
Renaming it to `poster.html` (and updating the one link in `#poster`) would be safer.

### If the venue has no internet

The three typefaces (Archivo, Source Serif 4, DM Mono) load from Google Fonts.
Without a connection they fall back to Helvetica, Georgia, and the system mono —
the layout holds, it just looks less distinctive. To make it fully offline-proof,
download the font files and swap the `<link>` for a local `@font-face` block.
