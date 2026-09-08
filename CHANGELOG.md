# TangoQ Changelog

This changelog summarizes the major user-facing TangoQ work since the project
branched from Mixxx 2.5.6 at commit `3ebac449e7`. It focuses on the changes that
support Argentine tango DJing; features inherited unchanged from Mixxx are not
repeated here.

## 1.0.2 - Early-access candidate #2

TangoQ 1.0.2 is planned for a wider early-access soft start. If that rollout
does not reveal release-blocking issues, the same version will become TangoQ's
first general public release.

### Tango-first interface

- Made TangoQ's tanda workflow the permanent default and renamed the inherited
  Auto DJ surface, menus, and preferences around TangoQ.
- Added a tango-focused default library layout and let DJs rename tandas for the
  event without changing track metadata.
- Added configurable queue colors for Tango, Vals, Milonga, Alt/Nuevo,
  cortinas, and performance tracks, with distinct current-item markers.
- Added a High Contrast scheme for daylight and bright venues, plus adjustable
  library text size.
- Simplified the skin, menus, deck controls, and queue actions around the tools
  used during a milonga while retaining a familiar deck-based DJ layout.

### Safer live operation

- Prevented track double-clicks and disruptive add-to-top or replace-queue
  actions from changing a prepared set.
- Kept the preview deck seekable while LIVE mode protects the playing decks and
  queue.
- Added a waveform envelope for the active cortina fade and kept it accurate
  when the cortina length changes during playback.
- Improved end-of-set stopping, set and selection timing, tanda selection, and
  cockpit status around cortinas and pause markers.

### Product identity and upgrades

- Completed TangoQ branding across the application, installers, icons, package
  metadata, logs, and support links.
- Gave TangoQ its own settings, library database, application identity, and
  Windows installer identity so it can coexist with stock Mixxx.
- Added an explicit first-run import for DJs who choose to bring an existing
  Mixxx library into TangoQ.
- Separated TangoQ configuration migrations from the inherited Mixxx version,
  preserving customized settings during supported upgrades and recording the
  migration result in `tangoq.log`.
- Improved fresh-install window sizing and positioning, and fixed a crash when
  the application is closed during startup.

## 1.0.1 - Early-access Candidate #1

The 1.0.1 builds established the core tango workflow and were distributed only
for limited testing.

### Prepared tanda sets

- Introduced an ordered queue that keeps played tracks visible, follows edits
  without losing its place, and stops after the final track.
- Added grouping for Tango, Vals, Milonga, and Alt/Nuevo tandas, including
  collapsible headers and progress pips.
- Added session labels for cortinas and performance tracks, plus pause-after
  markers for announcements and other planned interruptions.
- Added Set Start markers so a DJ can define the exact musical entry point for
  a track independently of beat quantization.

### Tango transitions and timing

- Added Tanda Transition, which uses a real silent gap between tracks and
  honors the next track's Set Start marker.
- Added dedicated cortina length and fade behavior instead of treating cortinas
  like ordinary songs.
- Added milonga duration, target end-time comparison, selected-track duration,
  next-transition status, tanda progress, and a prominent playback countdown.

### Performance safeguards

- Added LIVE mode with guarded stopping and protection against accidental
  queue reordering, clearing, replacement, randomization, and disruptive
  keyboard input.
- Added reset and resume behavior designed around an in-progress tanda set,
  including safe deck handling and recovery when tracks are appended after the
  queue runs dry.
- Added a dockable TangoQ queue panel so the prepared set remains visible while
  the DJ browses the library.

### Initial TangoQ product

- Introduced the TangoQ name, version, artwork, dedicated skin, settings
  location, and application packaging while retaining clear credit to Mixxx.
- Defaulted new installations to silence-aware transitions and a simplified,
  centered first-run layout suited to a live tango set.

For changes inherited from the underlying audio engine and library, refer to
the upstream Mixxx 2.5.6 changelog.
