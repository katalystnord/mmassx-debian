# Status and next steps (2026-09-08)

## Where things stand

- ITP filed and acknowledged by the BTS: Bug#1147163.
- Debichem team notified at debichem-devel@alioth-lists.debian.net.
- Upstream PR https://github.com/SCIENCE-OPEN/mmassx/pull/2, bundling all
  eight of this package's patches (0001-0008), was **merged** into
  mmassx's `main` branch on 2026-09-08.

The package still builds from the `v6.0.1` tag, which predates the merge,
so all eight patches stay in `debian/patches/series` unchanged for now.
Nothing to rebase until upstream cuts a new tag.

## What's actually next

1. **Debichem review** is the real wait. Nothing to do but give it time;
   follow up on debichem-devel@ if it goes quiet for a while.
2. **Watch for a new mmassx release/tag** past this merge. When one
   appears, rebase: drop whichever patches are now upstream, bump the
   packaged version.
3. **Open TODOs, independent of the merge** (also tracked in
   `debian/README.source`):
   - confirm the actual Debian package name/version for the wxPython 4.1
     bindings (`python3-wxgtk4.0` is currently a guess).
   - `mmass.py` resolves submodules relative to cwd, not script location
     (`sys.path.insert(0, './mspy')`); worked around in
     `debian/mmassx.wrapper` with a `cd`. Not part of PR #2; would need
     its own upstream report/PR if fixed there.
   - `gui/config.py` hardcodes `version = '5.5.0'` even at the v6.0.1
     tag; worth its own small upstream report.
   - no automated upstream test suite, so `dh_auto_test` stays a no-op.

None of item 3 blocks on Debichem, so if there's a want to keep moving
rather than idle, the wxPython package-name check or the `config.py`
version report are the next useful, self-contained bites.
