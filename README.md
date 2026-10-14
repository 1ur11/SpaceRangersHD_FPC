# Space Rangers HD — Free Pascal Port

An experimental Free Pascal port of **Space Rangers HD: A War Apart**, based on the
recovered Delphi source and intended to preserve the original game behavior.

Supported platforms:

- Linux x86_64
- macOS ARM64
- Windows x86 / x86_64
- Android ARM64 (8.0+)
- iOS (15+; tested only in the simulator)
- WebAssembly (browser)
- Nintendo Switch homebrew (tested only in emulators)

See [BUILDING.md](BUILDING.md) for dependencies and build/run instructions.

[Download Linux x86_64, Windows x86_64 and Android ARM64 builds](https://github.com/pakompom/SpaceRangersHD_FPC/releases).
You need your own game data. Releases are built automatically from source changes on `main`.

## Known issues

- Some Android screens and controls look rough or out of place. The original UI
  uses fixed desktop layouts and bitmap artwork, and adapting them for smaller
  touchscreens is still in progress.
- The robot battle engine is not integrated yet; planetary battles automatically
  count as victories and grant the normal rewards.

## Logs

Find `rangers-fpc.log` here (the error dialog also shows its path):

- Windows: `%USERPROFILE%\Documents\SpaceRangersHD\` (paste into File Explorer's address bar).
  If Documents was moved, enter `shell:Personal` instead, then open `SpaceRangersHD`.
- macOS: `~/Library/Application Support/SpaceRangersHD/`.
- Linux: `$XDG_DATA_HOME/SpaceRangersHD/`, or `~/.local/share/SpaceRangersHD/`.

Attach this file when reporting a problem. Set `SR_LOG_LEVEL=debug` before launch
for more detail, or `warning` / `error` for less output (default: `info`).

## Layout

- `source/`: game source, organized by subsystem.
- `tools/`: build, run, compiler bootstrap, and formatting scripts.
- `platform/`: Pascal windowing, input, graphics, audio, and OS services.
- `platform/wasm/`: browser page and adapters to Emscripten's host runtime.
- `platform/android/`: Android launcher, SDL activity, resource import and native entry point.
- `platform/switch/`: libnx entry point and controller input for Switch homebrew.
- `native/`: OKGF and SDL build integration for desktop, Android and the browser.
- `vendor/okgf/`: pinned [OKGF](https://github.com/pakompom/okgf) submodule.
- `vendor/fpc/`: pinned [FPC fork](https://github.com/pakompom/fpc_sr) submodule.

## Documentation

- [Build setup](BUILDING.md)
- [Development gotchas](DEVELOPING.md)
- [Porting and behavior reference](CHANGES.md)
- [Attribution](NOTICE.md) and [license](LICENSE)
- [Personal branch with enhancements](https://github.com/pakompom/SpaceRangersHD_FPC/tree/personal)

Development uses LLMs such as GPT-6 Astra through Codex.

The port follows the recovered source from
[SpaceRangersHD_decomp at `cd488c5`](https://github.com/pakompom/SpaceRangersHD_decomp/tree/cd488c5be075beec9e97e54c2dd92a7ff8e5b1a7),
which reconstructs the **2026-10-06 prerelease** build. It retains the platform
adaptations and behavior corrections described in [CHANGES.md](CHANGES.md).
