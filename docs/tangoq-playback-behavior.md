# TangoQ playback behavior

This document records user-visible playback contracts for TangoQ. These notes
describe current behavior rather than implementation history, so they remain
useful when the UI, storage, or transition internals change.

## Start marker, first audible sample, and clear/reset semantics

TangoQ exposes a visible start marker as `S` in the overview and `START` in the
waveform. This marker is backed by Mixxx's stock Intro Start cue.

There are two related but distinct positions:

- FAS is the analyzer's first audible sample, stored in the analyzed
  audible-range cue.
- S is the user-visible start marker, stored as the Intro Start cue.

On a freshly analyzed track, S and FAS commonly start at the same position
because silence analysis creates the default Intro Start cue at FAS.

If the DJ sets S to a timestamp `t`, only S moves. FAS remains the analyzer's
first audible sample.

Clearing S removes the user-visible start marker. Auto DJ then falls back to
FAS internally, but the waveform and overview do not draw an S marker.

Resetting S is different from clearing it. Reset sets S to `00:00`, meaning the
DJ intentionally wants the track or cortina to begin at the physical start of
the file, including any leading silence.

The Auto DJ list title may show a display-only start-time mark when S is a
DJ-authored start point, for example `[-- 00:15 --] El Choclo` or
`[-- CORTINA -- 00:15 --] Crawling`. New Set Start and Reset actions persist
that authorship on the Intro cue itself. Existing older markers without that
flag are still shown when S differs from FAS; this preserves useful legacy
start points without tagging every analyzer-created default Intro cue.

In short:

- Set Start moves S to the chosen timestamp.
- Clear Start removes the visible S marker; Auto DJ falls back to FAS.
- Reset Start sets S to `00:00`.
