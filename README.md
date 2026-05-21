# 🎮 PokéAzure — Azure you ready?

A Pokémon-style Game Boy Advance browser game for **studying Microsoft Azure certification exams**!
Journey through towns, each covering a different Azure exam. Play on your phone, tablet, or PC — progress saves automatically.

> *"Gotta cert 'em all!"*

**Current towns:**
| Town | Exam | Status |
|---|---|---|
| 🏘️ AZ-900 Town | AZ-900: Azure Fundamentals | ✅ Available |
| 🏙️ Administrator City | AZ-104: Azure Administrator | 🔜 Coming soon |
| 🏗️ Developer District | AZ-204: Azure Developer | 🔜 Coming soon |
| 🔒 Security Stronghold | AZ-500: Azure Security | 🔜 Coming soon |

---

## 🚀 Play It Live
👉 [Launch PokéAzure](https://justinoros.github.io/pokeazure)

---

## 🗂️ Files

```
pokeazure/
├── index.html        ← Game screens & structure
├── style.css         ← GBA Pokémon aesthetic, fully responsive
├── game.js           ← Game engine, controller, walking, save system
├── questions.json    ← Questions & answers (organised by town/exam)
├── music.mp3         ← Overworld background music (looping)
├── music-rival.mp3   ← Battle/question screen music (looping)
├── player.png        ← Player sprite sheet
├── oak.png           ← Professor Oak NPC sprite
├── gary.png          ← Rival Gary NPC sprite
├── joy.png           ← Nurse Joy NPC sprite
├── jenny.png         ← Officer Jenny NPC sprite
├── favicon.ico       ← Browser tab icon
└── README.md
```

---

## 🕹️ Host on GitHub Pages (free)

1. Create a GitHub repo named **`pokeazure`**
2. Upload all files to the root of the repo
3. Go to **Settings → Pages → Source: `main` branch, `/ (root)` folder**
4. Hit **Save** — live in ~60 seconds at `https://justinoros.github.io/pokeazure`

No server, no database, no cost.

---

## 🎮 Controls

### Mobile Portrait
A semi-transparent GBA-style controller overlays the bottom of the screen, split into two panels:
- **Left panel**: D-pad + SELECT/START
- **Right panel**: A and B buttons

### Mobile Landscape
The controller moves to side panels flanking the game screen:
- **Left panel**: D-pad + SELECT/START (stacked vertically)
- **Right panel**: A and B buttons (diagonal layout)

### PC Keyboard
| Key | Action |
|---|---|
| **WASD / Arrow keys** | Walk player on map |
| **E / Enter** | Talk to NPC · Confirm answer · Advance dialog |
| **X** | Talk to NPC · Advance dialog |
| **1 / 2 / 3 / 4** | Quick-pick answer |
| **Space** | Advance dialog |

---

## 🗺️ Map & Gameplay

- Player walks freely in all 4 directions across a large 2D world
- A directional arrow indicates where the next NPC is — hides when the NPC is on screen
- Walk up to an NPC and press E/A to start a question
- After answering, the next NPC spawns in a random direction (never the opposite of the last)
- Trees render above the player for depth
- NPCs float with a gentle animation

---

## 🎵 Music

- **Overworld** (`music.mp3`): plays while walking the map
- **Battle** (`music-rival.mp3`): plays during question/answer screen
- **Result screen**: silent
- Toggle mute with the 🎵 button in the HUD

---

## 💾 Save System

- **Auto-saves** after every answered question
- **Continue screen** on return visits showing trainer name, progress, and score
- **Shuffled question order** is saved so continuing always resumes at the correct question
- **New Game** option prompts confirmation before erasing

---

## 🎯 Features

| Feature | Detail |
|---|---|
| Free 2D movement | Walk in any direction, camera follows player |
| Random NPC directions | Next NPC spawns in a random direction each leg (no U-turns) |
| PNG NPC sprites | NPCs use pixel art PNG files; emoji fallback for unassigned NPCs |
| Mobile portrait & landscape | Fully optimised controller layout for both orientations |
| Single & multi-select questions | "Choose two" shows CONFIRM button; single select is immediate |
| Shuffled question order | Different order every new game |
| Streak bonuses | 3× correct = +150 pts 🔥, 5×+ = +200 pts 🔥 |
| Milestone badges | Cloud Explorer (Q25), Azure Apprentice (Q50), Cloud Practitioner (Q75), AZ-900 Champion (Q100) |
| Correct answer reveal | Wrong answers show the right answer + full explanation |
| Tap anywhere to continue | Result screen advances on any tap/click, not just CONTINUE button |
| Rival battle music | Separate music track plays during questions |
| Player faces last direction | Idle sprite faces the last direction walked |

---

## 📚 AZ-900 Topics Covered (AZ-900 Town)

| Domain | Topics |
|---|---|
| Cloud Concepts | IaaS / PaaS / SaaS, public / private / hybrid cloud, CapEx vs OpEx, elasticity, scalability, high availability, disaster recovery |
| Core Azure Services | Regions, availability zones, resource groups, subscriptions, management groups, VMs, App Service, Azure Functions, Blob/File storage tiers, VNet, VPN Gateway, ExpressRoute, Load Balancer, Cosmos DB, Azure SQL |
| Security & Identity | Microsoft Entra ID, RBAC, MFA, Conditional Access, SSO, Key Vault, NSGs, Azure Firewall, DDoS Protection, Microsoft Defender for Cloud, defence in depth, shared responsibility model |
| Management & Governance | Azure Policy, Blueprints, Resource locks, Tags, ARM templates, Azure CLI, Azure PowerShell, Cloud Shell, Azure Portal, Azure Arc, Azure Migrate, Microsoft Purview |
| Monitoring & Health | Azure Monitor, Azure Advisor, Azure Service Health, Application Insights, health advisories, RCA reports |
| Pricing & Cost Management | Pricing Calculator, TCO Calculator, Azure Reservations, Spot VMs, Cost Management + Billing, budgets, pay-as-you-go |

---

## ➕ Adding a New Town (Exam)

Add a new level object to the `levels` array in `questions.json`:

```json
{
  "levels": [
    {
      "id": 1,
      "name": "AZ-900 Town",
      "exam": "AZ-900",
      "questions": [ ... ]
    },
    {
      "id": 2,
      "name": "Administrator City",
      "exam": "AZ-104",
      "questions": [ ... ]
    }
  ]
}
```

---

## ➕ Adding Questions

**Single-answer:**
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

**Multi-select (choose two):**
```json
{
  "id": 102,
  "npc": "Nurse Joy",
  "text": "Which two options are correct? (Choose two)",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answers": [0, 2],
  "explanation": "Options A and C are correct because..."
}
```

---

## 🧑 Adding NPC Sprites

In `game.js`, update the `NPC` object at the top:

```js
const NPC = {
  'Professor Oak': 'oak.png',   // PNG file in repo root
  'Nurse Joy':     'joy.png',
  'Brock':         '🧗',        // emoji fallback still works
};
```

- PNG filenames are relative to the repo root (no path needed)
- Any NPC not in the object falls back to `🧑`

---

## 🔧 Rebranding (CONFIG object)

To create a version for a different exam set, update the `CONFIG` object at the top of `game.js`:

```js
const CONFIG = {
  gameName:   'PokéAzure',
  subject:    'Azure',
  examName:   'AZ-900',
  townName:   'AZ-900 Town',
  saveKey:    'pokeazure_save_v1',
  introLines: [ ... ],
  namePrompt: '...',
};
```

---

## 📱 Mobile Tips

- Add to Home Screen on iOS/Android for a full-screen app-like experience
- The game uses `100dvh` and `env(safe-area-inset-*)` for notched phones
- Tap anywhere on the result screen to continue (no need to find the CONTINUE button)
- Rotate to landscape for a wider game view with side-panel controls
