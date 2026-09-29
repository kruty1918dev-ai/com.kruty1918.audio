# com.kruty1918.audio

Reusable audio runtime extracted from Moyva.

## Install (Unity Package Manager)

Package Manager → **+** → **Add package from git URL**:

```
https://github.com/kruty1918dev-ai/com.kruty1918.audio.git
```

or in `Packages/manifest.json`:

```json
"com.kruty1918.audio": "https://github.com/kruty1918dev-ai/com.kruty1918.audio.git#v0.1.0"
```

The repository is private — Git credentials (PAT / Git Credential Manager)
are required on every machine that resolves the package.

## Features

- `IAudioService`/`AudioService`: key-driven playback over an AudioMixer with
  buses, named channels, ducking, pooling, per-scene overrides. Catalog arrives
  via `IAudioCatalog` + `IAudioSceneOverrides` (implemented by host config
  assets).
- `IMusicService`/`MusicService`: scene-matched music profiles
  (`IMusicSceneProfile`) with crossfade.
- Contracts (`AudioBus`, `AudioSoundDefinition`, `AudioPlayOptions`,
  `AudioHandle`, …) are game-agnostic.

## API surface

| Type | Purpose |
|---|---|
| `IAudioService` | One-shot/looping playback, pooling, ducking, per-scene overrides |
| `IAudioCatalog` / `IAudioSceneOverrides` | Host-supplied sound catalog and per-scene tweaks |
| `IMusicService` / `IMusicSceneProfile` | Music profile per scene with crossfade |
| `AudioBus` | Mixer bus/channel routing |

## Model

Lifecycle (`Initialize`/`Tick`/`Dispose`) is driven by the host composition
root — the package never reaches into scenes on its own.

## Dependencies

- `com.unity.ugui`
