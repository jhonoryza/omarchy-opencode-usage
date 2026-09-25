# OpenCode Usage for Omarchy agents panel

Menampilkan usage OpenCode di panel `omarchy.agents`, pola sama seperti
`dell.commandcode-usage` dan `wellatleastitried/omarchy-copilot-panel-usage`.

## Cara kerja

* `bin/omarchy-agent-usage-opencode` baca SQLite `~/.local/share/opencode/opencode.db`
  (tabel `message`, kolom JSON `data`), hitung prompt/token per hari dan per model.
* Tulis ke `~/.local/state/omarchy/agents/usage/opencode.json`.
* `ui/main.qml` jalan tiap 5 menit + saat usage dir berubah.

## Test manual

```bash
~/.config/omarchy/plugins/dell.opencode-usage/bin/omarchy-agent-usage-opencode | head -n 40
~/.config/omarchy/plugins/dell.opencode-usage/bin/omarchy-agent-usage-opencode --write
omarchy plugin validate ~/.config/omarchy/plugins/dell.opencode-usage
omarchy-shell shell rescanPlugins
```
