# Bug fixes applied in this patch

- Electron now serves the desktop app from a fixed localhost port (`47831`) so IndexedDB remains attached to the same origin after restart. If that port is already occupied, Prism shows an explicit startup error rather than silently switching to another port.
- Pressing Play when the timeline is already at its end restarts from time zero.
- Removing a currently active timeline clip now stops its audio source and pauses its video.
- Double-clicking an existing timeline clip no longer bubbles to the empty-track handler and adds another clip.
- Dragging the listener, speakers, or sounds in the 2D room view updates x/y only and preserves each object's own z height.
- MediaEditor no longer resets its duration state when trim values are saved, preventing the Start/End sliders from disappearing during the update.

## Important notes

- The app build could not be verified in this environment because dependency installation did not complete and `vite` was unavailable. `electron/main.cjs` passes `node --check`.
- The fixed port makes future launches use the same IndexedDB origin. Shows saved under a previous randomly assigned port may still need a one-time recovery/import; this patch does not delete that old browser data.
- `.env`, `.git`, `.vs`, and `node_modules` are intentionally excluded from the patch archive. Keep your original environment file private and restore it locally if needed.
