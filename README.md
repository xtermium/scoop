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

New releases reach the bucket on their own: [Excavator](.github/workflows/excavator.yml) checks every 4 hours.
