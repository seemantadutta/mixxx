# Linux packaging follow-ups

The application metadata is TangoQ-specific, but several inherited Linux
packaging details still need implementation work. These items affect Debian or
Flatpak packaging and should be handled in focused code or packaging changes,
not in the 1.0.2 documentation cleanup.

Scope tags: **[deb]** Debian-only, **[shared]** Debian and Flatpak, and
**[flatpak]** Flatpak-only.

## User-visible

- [ ] **[deb] Rebrand and rename the man page.** The package still generates
  `mixxx.1` from `packaging/debian/mixxx.sgml`. Rename it to `tangoq.1`, update
  `packaging/CPackDebInstall.cmake`, and replace its Mixxx-specific title,
  description, URLs, and maintainer details.
- [ ] **[shared] Publish TangoQ screenshots.** The AppStream metadata omits
  screenshots until real TangoQ captures are available at stable URLs.
- [ ] **[flatpak] Decide whether TangoQ will publish a Flatpak repository.** If
  so, replace the inherited Mixxx values in
  `packaging/flatpak/repo.flatpakrepo`; otherwise remove that unused file.

## Packaging internals

- [ ] **[shared] Exclude unused Mixxx icons from the hicolor installation.**
  TangoQ's desktop file uses its own icon, but the shared icon-directory install
  also copies inherited Mixxx icons.
- [ ] **[shared] Shorten the desktop-file `GenericName`.** Localized values use
  the generic "Digital DJ system" while the default value is a longer tagline.
- [ ] **[deb] Review the inherited udev rule name.** The rule is still named
  `mixxx-usb-uaccess`; rename it only with all package references updated.
- [ ] **[deb] Review `CPACK_DEBIAN_PACKAGE_REPLACES "mixxx-data"`.** Confirm
  whether a TangoQ package should replace stock Mixxx data before distributing
  Debian packages to users who may have both applications installed.
