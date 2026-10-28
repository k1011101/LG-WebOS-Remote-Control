# UF778 remote fork

Based on upstream release 2.1.0 (41c29a8bc10f9e9c46ad4419f3d0797e0642b67d).
MIT license and upstream attribution are retained.

This fork registers `lg-uf778-remote` and its own editor, allowing the original
HACS card to coexist. Volume overrides use upstream 2.1.0 `keys` support.

Additional YAML fields:
- `audio_output_entity`: HA select with options `Динамики ТВ`, `HDMI ARC / оптика`, `ТВ + внешний выход`.
- `audio_input_entity`: HA select with options `HDMI ARC`, `Оптика / Coax`.
- `source_order`: optional source names, default PS5, ONKYO, APPLE.
- A `sources` item may include `button: MENU` for a TV settings shortcut.

ARC/optical buttons use the receiver selector, not unsupported LG output codes.
Selected highlighting requires both actual external TV output and receiver state.
Unavailable selectors do not send commands. Headphone, line-out and Bluetooth
buttons are hidden for this UF778 setup. HDMI is placed before optical.

## Updating

Keep upstream releases separate from the UF778 commits. Fetch upstream tags,
merge the selected release into the UF778 branch, resolve conflicts in source,
then run `npm ci`, `npm test`, `npm run rollup` and `npx tsc --noEmit`.
Do not patch minified bundles. Build a versioned release after tests.
Back up the live resource and dashboard before deployment. Verify the rendered
card and selector routing; restore the previous resource for rollback.

Do not commit household dashboard exports, MAC/IP addresses, credentials or
Node-RED flows to this public repository. Use generic examples only.
