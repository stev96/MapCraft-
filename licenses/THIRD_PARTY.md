# THIRD_PARTY.md

Direkte Abhängigkeiten und gebündelte Assets. Transitive Abhängigkeiten werden durch
`cargo deny check` gegen die Lizenz-Allowlist (playbook.md 5.5) geprüft.

## Crates (direkt)

| Crate | Lizenz | Zweck |
|---|---|---|
| egui | MIT OR Apache-2.0 | Immediate-Mode-UI |
| eframe | MIT OR Apache-2.0 | App-Rahmen für egui (wgpu-Backend) |
| skrifa (MIT OR Apache-2.0), tiny-skia (BSD-3-Clause) | – | Text-Generator: Glyphen-Konturen aus IBM Plex Sans, gefüllt mit Kantenglättung (beide ohnehin über egui/resvg im Baum) |
| snap | BSD-3-Clause | Snappy-Entpacken von HAP-Videoframes |
| cpal (Apache-2.0) mit coreaudio-rs (MIT), dasp_sample (MIT OR Apache-2.0), mach2 (BSD-2-Clause OR MIT OR Apache-2.0) | – | Audio-Ausgabe für den Ton von Videos (CoreAudio, ALSA, WASAPI) |
| egui_extras (Feature `svg`) mit resvg/usvg (Apache-2.0 OR MIT) und tiny-skia (BSD-3-Clause) | MIT OR Apache-2.0 | Rastert die eigenen SVG-Icons aus `assets/icons` |
| image | MIT OR Apache-2.0 | PNG-Encoding für den Screenshot-Design-Check |
| wgpu | MIT OR Apache-2.0 | GPU-Rendering (Metal/Vulkan) |
| naga | MIT OR Apache-2.0 | WGSL-/GLSL-Parser und Validierung für Nutzer-Shader |
| glam | MIT OR Apache-2.0 | Vektor-/Matrixmathematik (Homographie) |
| lyon | MIT OR Apache-2.0 | Polygon-Tessellierung für Masken |
| pollster | MIT OR Apache-2.0 | Blocking-Executor für wgpu-Futures (nur Tests) |
| objc2 | MIT | Objective-C-Bindings (macOS) |
| objc2-foundation | MIT | Foundation-Bindings: NSProcessInfo, NSString u. a. |
| objc2-app-kit | MIT | AppKit-Bindings: NSScreen (Display-Erkennung) |
| objc2-core-foundation | Zlib OR Apache-2.0 OR MIT | CFMessagePort, Run-Loop, Benachrichtigungen (Syphon, ADR 0009) |
| objc2-io-surface | Zlib OR Apache-2.0 OR MIT | IOSurface (Syphon-Bilder) |
| objc2-metal | Zlib OR Apache-2.0 OR MIT | IOSurface als Metal-Textur (Syphon) |
| ffmpeg-next / ffmpeg-sys-next | WTFPL (Bindings) | Rust-Bindings an FFmpeg (ADR 0004) |
| crossbeam-channel | MIT OR Apache-2.0 | Kanäle für Decode-/Thumbnail-/DMX-Threads |
| socket2 | MIT OR Apache-2.0 | UDP-Sockets mit Broadcast/Multicast/Reuse (Art-Net, sACN) |
| if-addrs | MIT OR BSD-3-Clause | Netzwerk-Interfaces für die Interface-Auswahl |
| uuid | MIT OR Apache-2.0 | sACN-CID (UUID v4) pro Installation |
| midir | MIT | MIDI-Eingang (CoreMIDI auf macOS, ALSA unter Linux, WinMM unter Windows) |
| rosc | MIT OR Apache-2.0 | OSC-Kodierung/-Dekodierung |
| notify | CC0-1.0 | Dateisystem-Watcher für die Media-Library |
| rfd | MIT | Native Datei-/Ordnerdialoge |
| serde / serde_json | MIT OR Apache-2.0 | Projektdatei-Serialisierung (.mapcraft) |

## Systembibliotheken (dynamisch gelinkt)

| Bibliothek | Lizenz | Zweck |
|---|---|---|
| FFmpeg (libavcodec/-format/-util, libswscale, libavdevice) | LGPL-2.1+ (dynamisch gelinkt, ADR 0004) | Video-Decode, Kamera-Capture, Pixelformat-Konvertierung. Im Mac-Installer: eigener Build ohne GPL-Teile (`scripts/build-ffmpeg.sh`, ADR 0011), Lizenz und Quelle unter `Contents/Resources/Licenses` |
| AVFoundation, CoreMedia, IOSurface (macOS) | Systemframeworks | Kamera-Liste und -Modi, Syphon-Bilder |

## Protokolle

| Protokoll | Lizenz der Referenz | Nutzung |
|---|---|---|
| Syphon | BSD-3-Clause (Syphon-Framework-Quellcode) | Eigene Implementierung des Protokolls; kein Code übernommen, nichts gelinkt oder ausgeliefert (ADR 0009) |

## Assets

| Asset | Lizenz | Quelle | Zweck |
|---|---|---|---|
| IBM Plex Sans (Regular, Medium) | OFL-1.1 | github.com/IBM/plex, Release `@ibm/plex-sans@1.1.0` | UI-Schrift |
| IBM Plex Mono (Regular) | OFL-1.1 | github.com/google/fonts `ofl/ibmplexmono` | Zahlen, Koordinaten, DMX-Werte, Code |

Lizenztexte: `assets/fonts/OFL-IBMPlexSans.txt`, `assets/fonts/OFL-IBMPlexMono.txt`.
