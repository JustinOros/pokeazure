# 🎮 PokéAzure — Learn Azure Cloud

A Pokémon-style Game Boy Advance browser game for learning **Microsoft Azure** and preparing for the **AZ-900** exam!
Play it on your phone, tablet, or PC — progress is saved automatically to your browser.

## 🚀 Play It Live
👉 [Launch PokéAzure](https://justinoros.github.io/pokeazure)

---

## 🗂️ Files

```
pokeazure/
├── index.html        ← Game screens & structure
├── style.css         ← GBA Pokémon aesthetic, fully responsive
├── game.js           ← Game engine, controller, walking, save system
├── config.js         ← Game-specific config (name, text, badges, milestones)
├── questions.json    ← 100 AZ-900 questions & answers
├── player.png        ← Player sprite sheet (24 frames, 16×32px)
├── oak.png           ← Professor Oak NPC sprite
├── gary.png          ← Rival Gary NPC sprite
├── joy.png           ← Nurse Joy NPC sprite
├── jenny.png         ← Officer Jenny NPC sprite
├── brock.png         ← Brock NPC sprite
├── misty.png         ← Misty NPC sprite
├── taro.png          ← Hiker Taro NPC sprite
├── ralph.png         ← Fisherman Ralph NPC sprite
├── music.mp3         ← Background music (overworld)
├── music-rival.mp3   ← Background music (rival/battle)
├── favicon.ico       ← Browser tab icon / Pokéball
└── README.md
```

---

## 🕹️ Host on GitHub Pages (free)

1. Create a GitHub repo named **`pokeazure`**
2. Upload all files listed above
3. Go to **Settings → Pages → Source: `main` branch, `/ (root)` folder**
4. Hit **Save** — live in ~60 seconds at `https://justinoros.github.io/pokeazure`

No server, no database, no cost.

---

## 🎮 GBA Controller Overlay

On mobile, a semi-transparent Game Boy Advance-style controller overlays the bottom of the screen:

| Control | Action |
|---|---|
| **D-pad** | Walk the player around the map |
| **A button** (red) | Talk to NPC · Confirm answer · Advance dialog |
| **B button** (blue) | Talk to NPC · Advance dialog |
| **SELECT / START** | Decorative |

The controller is hidden on desktop (≥900px wide) — use the keyboard instead.

---

## 🕹️ Xbox / Gamepad Support

Plug in any Xbox, PlayStation, or USB gamepad and it works automatically:

| Input | Action |
|---|---|
| **Left stick / D-pad** | Walk on map |
| **A button** | Talk to NPC · Confirm answer · Advance dialog |
| **B button** | Talk to NPC · Advance dialog |
| **Start** | Confirm / advance on all screens |
| **X / Y / LB / RB** | Quick-pick answers 1/2/3/4 in battle |

---

## ⌨️ PC Keyboard Controls

| Key | Action |
|---|---|
| **WASD / Arrow keys** | Walk player on map |
| **E / Enter** | Talk to NPC · Confirm answer · Advance dialog |
| **X** | Talk to NPC · Advance dialog |
| **1 / 2 / 3 / 4** | Quick-pick answer directly |
| **Space** | Advance dialog |

---

## 🗺️ Map & Walking

- The player sprite walks freely around the overworld map using the D-pad, WASD, arrow keys, or Xbox controller
- Walking animations use the `player.png` sprite sheet with directional frames
- A blinking `▶` arrow on the right edge points toward the next NPC
- A `...` speech bubble appears above the player if you press talk before reaching the NPC
- Press **A**, **B**, **E**, or **Enter** when near the NPC to start the question
- Tapping the NPC sprite directly also triggers the conversation

---

## 💾 Save System

Progress is stored in the player's browser (`localStorage`) automatically:

- **Auto-saves** after every answered question and on map return
- **Shuffled question order** is saved so continuing a game resumes the exact same sequence
- **Continue screen** appears on next visit showing trainer name, progress %, and score
- **New Game** option always available — prompts confirmation before erasing save
- Save clears automatically on completion so the next run starts fresh

---

## 🎵 Music

- Background music plays automatically on the map (`music.mp3`)
- Music pauses during questions and resumes on return to the map
- **🎵 / 🔇 toggle** in the map header to mute/unmute
- Music resumes correctly after switching browser tabs on mobile

---

## 🎯 Features

| Feature | Detail |
|---|---|
| GBA controller overlay | D-pad + A/B buttons, semi-transparent, mobile only |
| Xbox / gamepad support | Full navigation on all screens including name entry |
| Walking player | Pixel sprite sheet, directional walk animations |
| Mobile-first design | Full-screen on phones with safe-area support, framed on desktop |
| localStorage save | Auto-save with shuffled order preserved on continue |
| Starter Pokémon selection | Choose Charmander, Squirtle, or Bulbasaur at the start |
| Wild Pokémon encounters | Wild Pokémon spawn on the map — walk into them to catch |
| Pokéball & catching system | Throw Pokéballs to catch wild Pokémon and build your party |
| Pokémon party | Manage a party of caught Pokémon, switch your active battler |
| 100 AZ-900 questions | Randomised order every new game, shuffled answer slots |
| Multi-select questions | Some questions require choosing two correct answers |
| Numbered answers | Options labelled 1/2/3/4 — no A/B/C/D pattern to exploit |
| PNG NPC sprites | NPCs can use image files or emoji |
| Name entry | On-screen pixel keyboard navigable by gamepad |
| Typewriter text | Authentic dialog effect, tap/press/gamepad to skip |
| `...` proximity bubble | Shows above player when pressing talk too far from NPC |
| Background music | Loops on map, pauses during questions, mute toggle |
| Streak bonuses | 3× correct = +150 pts 🔥, 5×+ = +200 pts 🔥 |
| Milestone badges | Earned at Q25, Q50, Q75, Q100 |
| Correct answer reveal | Wrong answers show the right answer + full explanation |
| Scanline overlay | Authentic CRT/GBA screen effect |

---

## 📚 Topics Covered

| Questions | Topics |
|---|---|
| 1–15 | Regions, availability zones, VPNs, virtual networks, resource tags, reservations, locks |
| 16–25 | Azure Cloud Shell, CLI tools, Advisor, Monitor, Service Health, Application Insights |
| 26–35 | Subscriptions, management groups, VMs, serverless, Blob storage tiers |
| 36–50 | Defense in depth, SSO, Conditional Access, RBAC, MFA, cloud models (public/private/hybrid) |
| 51–65 | IaaS / PaaS / SaaS, cloud pricing, Cost Management, regions, resource groups, Entra ID |
| 66–80 | NSGs, ExpressRoute, Load Balancer, App Service, Cosmos DB, CapEx vs OpEx, Well-Architected Framework |
| 81–100 | ARM Templates, Azure Portal, CLI, least privilege, Defender, shared responsibility, Blueprints, GRS, CAF, Private Link, Arc, DevOps, Sentinel, MFA, elasticity |

---

## ➕ Adding Questions

Edit `questions.json`, add to the `questions` array inside `levels[0]`:

```json
{
  "id": 101,
  "npc": "Professor Oak",
  "text": "Your question here?",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answer": 0,
  "explanation": "Why Option A is correct."
}
```

For a multi-select question (choose two), use `answers` instead of `answer`:

```json
{
  "id": 102,
  "npc": "Misty",
  "text": "Which two of these are Azure compute services? (Choose two)",
  "options": ["Azure VMs", "Azure Blob", "Azure Functions", "Azure DNS"],
  "answers": [0, 2],
  "explanation": "Azure VMs and Azure Functions are both compute services."
}
```

`answer` / `answers` use the **0-based index** of the correct option(s). The game shuffles display order randomly at runtime.

---

## 🧑 Adding NPCs

In `game.js`, add to the `NPC` object:

```js
const NPC = {
  'Your NPC Name': 'npc.png',   // PNG sprite file in repo root
  'Another NPC':   '🧑',        // or an emoji
};
```

Then reference `"npc": "Your NPC Name"` in `questions.json`. PNG files are auto-prefixed with `./` so just use the filename.

---

## ⚙️ Customising the Game

All game-specific text lives in **`config.js`** — the only file that differs between PokéAzure and its sister game PokéSQL. Edit it to change the game name, town name, intro dialog, badge names, battle move names, and more without touching `game.js` or `index.html`.

---

## 📱 Mobile Tips

- Add to Home Screen on iOS/Android for a full-screen app-like experience
- The game uses `100dvh` and `env(safe-area-inset-bottom)` for notched phones (iPhone X+)
- Tap anywhere on the dialog box during the intro to skip the typewriter and advance
- Tap the NPC sprite directly on the map as an alternative to pressing A/B
