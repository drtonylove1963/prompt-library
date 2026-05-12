<p align="center">
  <img src="src-tauri/icons/icon.png" width="80" alt="Prompt Library" />
</p>

<h1 align="center">Prompt Library</h1>

<p align="center">
  A lightweight desktop app for organizing, searching, and copying AI prompts.<br/>
  Built with <a href="https://v2.tauri.app">Tauri v2</a>, Rust, and vanilla JavaScript.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Windows%20%7C%20macOS-blue?style=flat-square" alt="Platform" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License" />
  <a href="https://github.com/sponsors/Leonxlnx"><img src="https://img.shields.io/badge/GitHub%20Sponsors-support%20the%20project-ec4899?style=flat-square" alt="GitHub Sponsors" /></a>
</p>

---

## Features

**Organization**
- Folders with custom colors, drag-and-drop reordering
- Tag prompts, star your favorites
- Move prompts between folders by dragging cards to the sidebar

**Productivity**
- One-click copy to clipboard
- Global quick-save shortcut (`Ctrl+Shift+S`)
- Search across names, text, and tags
- Sort by name, date, or last edited
- Keyboard shortcuts: `Ctrl+N` new prompt, `Ctrl+F` search, `Ctrl+B` sidebar

**Extras**
- Attach images to prompts (paste, drag, or browse)
- Character counter with token-limit warnings
- Dark and light theme
- ~5 MB installer

---

## Install

### Download a prebuilt installer

Grab the latest installer from the [GitHub Releases](https://github.com/Leonxlnx/prompt-library/releases) page:

- **Windows** — `Prompt Library_*_x64-setup.exe` (NSIS, ~5 MB)
- **macOS** — `Prompt Library_*_universal.dmg` (Universal: Apple silicon + Intel)

> The macOS build is unsigned. On first launch, right-click the app and choose **Open** to bypass Gatekeeper, then confirm.

If no release has been published yet, see "Build from source" below.

### Build from source

You need [Rust](https://rustup.rs), [Node.js 18+](https://nodejs.org), and `cargo install tauri-cli`.

On macOS, also install Xcode Command Line Tools:
```
xcode-select --install
```

On Windows, install [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) with the "Desktop development with C++" workload.

Then:

```bash
git clone https://github.com/Leonxlnx/prompt-library.git
cd prompt-library
npm install
npm run dev      # run in dev mode
npm run build    # produce a release installer
```

Installers are generated here:

```text
src-tauri/target/release/bundle/
```

Typical files:

- Windows: `src-tauri/target/release/bundle/nsis/Prompt Library_1.0.0_x64-setup.exe`
- macOS: `src-tauri/target/release/bundle/dmg/Prompt Library_1.0.0_*.dmg`

### Cutting a release

Releases are produced by GitHub Actions (`.github/workflows/release.yml`). To publish a new version:

1. Bump the version in `package.json`, `src-tauri/Cargo.toml`, and `src-tauri/tauri.conf.json`.
2. Commit and push the version bump.
3. Tag and push: `git tag v1.0.1 && git push origin v1.0.1`.
4. The workflow builds Windows + macOS (universal) installers and opens a **draft** release. Edit it, add notes, and publish.

You can also trigger the workflow manually from the Actions tab (`Run workflow` → enter the tag name).

### Reinstall or update on Windows

1. Close Prompt Library.
2. Run `Prompt Library_<version>_x64-setup.exe`
3. Finish the installer.
4. Open Prompt Library again from the Start menu or:

```text
C:\Users\<your-user>\AppData\Local\Prompt Library\prompt-library.exe
```

---

## Project structure

```
prompt-library/
├── renderer/            # Frontend (HTML, CSS, JS)
│   ├── index.html
│   ├── styles.css
│   ├── app.js
│   ├── quicksave.html
│   └── quicksave.js
├── src-tauri/           # Rust backend
│   ├── src/lib.rs       # Core logic and commands
│   ├── src/main.rs      # Entry point
│   ├── tauri.conf.json  # App config
│   ├── capabilities/    # Permission definitions
│   └── Cargo.toml
├── package.json
├── ROADMAP.md
├── LICENSE
└── README.md
```

## Tech stack

| | |
|---|---|
| Framework | [Tauri v2](https://v2.tauri.app) |
| Backend | Rust |
| Frontend | HTML / CSS / JS (no framework) |
| Storage | Local JSON file |
| Font | [Inter](https://fonts.google.com/specimen/Inter) |

## Roadmap

See [ROADMAP.md](ROADMAP.md).

## Contributing

1. Fork the repo
2. Create a branch (`git checkout -b feature/your-feature`)
3. Commit (`git commit -m 'add your feature'`)
4. Push (`git push origin feature/your-feature`)
5. Open a PR

## Support

If Prompt Library helps your workflow, you can support ongoing development on [GitHub Sponsors](https://github.com/sponsors/Leonxlnx).

## License

MIT — see [LICENSE](LICENSE).
