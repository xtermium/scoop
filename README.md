# xtermium for Scoop

A [Scoop](https://scoop.sh) bucket for [xtermium](https://xtermium.com), the terminal with a session manager.

```powershell
scoop bucket add xtermium https://github.com/xtermium/scoop
scoop install xtermium/xtermium
```

## Portable, with your data kept

Scoop unpacks xtermium without running an installer, and sets `XTERMIUM_HOME` (xtermium's portable mode) to `~\scoop\persist\xtermium`. Sessions, tabs, trusted host keys, settings, restore points and session logs live there, so `scoop update xtermium` and reinstalls keep them. `scoop uninstall --purge xtermium` deletes them.

- `XTERMIUM_HOME` is a user environment variable: every xtermium you start uses this folder, not only the Scoop copy.
- The files are encrypted with a key kept in Windows Credential Manager. Set a recovery passphrase (Settings › Security) to open them on another computer or after the key is lost.
- Coming from the `.msi` or setup `.exe`: in that copy, Settings › Import and export › Back up everything…, then Restore everything in the Scoop copy.

## Nightly builds

`xtermium-nightly` is main as it stands, built every night it has changed: what the next release will carry, before it has been used for long. It takes the release's place and opens the same data (`~\scoop\persist\xtermium`), so keep a backup you trust (Settings › Import and export › Back up everything…).

```powershell
scoop uninstall xtermium          # the release, if it is installed: your data stays
scoop install xtermium/xtermium-nightly
scoop config update_nightly true  # once: Scoop then updates nightly builds, by their date
scoop update xtermium-nightly     # the latest night's build (close xtermium first)
```

- Scoop doesn't check a nightly download against a hash: the file changes every night.
- Without `update_nightly`, Scoop calls any installed nightly build the latest; `scoop update -f xtermium-nightly` then gets the current one. With it, `scoop update xtermium-nightly` and `scoop update *` take a new build once a day.
- Back to the release: `scoop uninstall xtermium-nightly`, then `scoop install xtermium/xtermium`.

New releases reach the bucket on their own: [Excavator](.github/workflows/excavator.yml) checks every 4 hours.
