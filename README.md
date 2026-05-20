# 🎮 PokéAzure — Azure you ready?

A Pokémon-style web-browser game for **studying Microsoft Azure certification exams**!
Journey through towns, each covering a different Azure exam. Play on your phone, tablet, or PC — progress saves automatically.

> *"Gotta cert 'em all!"*

**Current towns:**
| Town | Exam | Status |
|---|---|---|
| 🏘️ Fundamentals Town | AZ-900: Azure Fundamentals | ✅ Available |
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
├── index.html      ← Game screens & structure
├── style.css       ← GBA Pokémon aesthetic, fully responsive
├── game.js         ← Game engine, controller, walking, save system
├── questions.json  ← Questions & answers (organised by town/exam)
└── README.md
```

---

## 🕹️ Host on GitHub Pages (free)

1. Create a GitHub repo named **`pokeazure`**
2. Upload all **4 files**: `index.html`, `style.css`, `game.js`, `questions.json`
3. Go to **Settings → Pages → Source: `main` branch, `/ (root)` folder**
4. Hit **Save** — live in ~60 seconds at `https://justinoros.github.io/pokeazure`

No server, no database, no cost.

---

## 🎮 GBA Controller Overlay

On mobile, a semi-transparent Game Boy Advance-style controller overlays the bottom of the screen:

| Control | Action |
|---|---|
| **D-pad** | Walk the player around the map |
| **A button** (red) | Talk to NPC on map · Confirm answer in battle · Advance dialog |
| **B button** (blue) | Talk to NPC on map · Advance dialog |
| **SELECT / START** | Decorative — reserved for future use |

The controller is hidden on desktop (≥900px wide) — use the keyboard instead.

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

- The player sprite walks freely around the overworld map using the D-pad or WASD
- Walking animations change based on direction (left, right, up, down)
- Press **A**, **B**, **E**, or **Enter** at any time to talk to the NPC and start the question
- Tapping the NPC sprite directly also triggers the conversation

---

## 💾 Save System

Progress is stored in the player's browser (`localStorage`) automatically:

- **Auto-saves** after every answered question and on map return — a 💾 icon flashes to confirm
- **Continue screen** appears on next visit showing trainer name, progress %, and score
- **New Game** option always available — prompts confirmation before erasing save
- Save clears automatically on completion so the next run starts fresh

---

## 🎯 Features

| Feature | Detail |
|---|---|
| GBA controller overlay | D-pad + A/B buttons, semi-transparent, mobile only |
| Walking player | Moves freely on map, directional walk animations |
| Mobile-first design | Full-screen on phones with safe-area support, framed on desktop |
| localStorage save | Auto-save with continue screen on return visits |
| Multi-exam structure | Each town covers a different Azure certification exam |
| Single & multi-select | "Choose two" questions require selecting both correct answers before confirming |
| Randomised answer positions | Correct answer shuffled to a random slot — no pattern to exploit |
| Numbered answers | Options labelled 1/2/3/4 (not A/B/C/D) |
| Name entry | On-screen pixel keyboard, just like the real game |
| Typewriter text | Authentic dialog effect, tap/press to skip |
| 22 NPC characters | Professor Oak, Misty, Brock, Giovanni, Lance… |
| Streak bonuses | 3× correct = +150 pts 🔥, 5×+ = +200 pts 🔥 |
| Milestone badges | Earned at Q25, Q50, Q75, Q100 per town |
| Correct answer reveal | Wrong answers show the right answer + full explanation |
| Scanline overlay | Authentic CRT/GBA screen effect |

---

## 📚 AZ-900 Topics Covered (Fundamentals Town)

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

To add a new exam, add a new level object to the `levels` array in `questions.json`:

```json
{
  "levels": [
    {
      "id": 1,
      "name": "Fundamentals Town",
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

**Single-answer question:**
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

**Multi-select question (choose two):**
```json
{
  "id": 102,
  "npc": "Misty",
  "text": "Which two options are correct? (Choose two)",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answers": [0, 2],
  "explanation": "Options A and C are correct because..."
}
```

- `answer` (single integer) = 0-based index of the one correct option
- `answers` (array of two integers) = 0-based indices of both correct options
- The game detects which mode to use automatically and shows a CONFIRM button for multi-select

---

## 🧑 Adding NPCs

In `game.js`, add to the `NPC` object at the top:

```js
const NPC = {
  'Your NPC Name': '🧑',
  ...
};
```

Then reference `"npc": "Your NPC Name"` in `questions.json`.

---

## 📱 Mobile Tips

- Add to Home Screen on iOS/Android for a full-screen app-like experience
- The game uses `100dvh` and `env(safe-area-inset-bottom)` for notched phones (iPhone X+)
- Tap anywhere on the dialog box during the intro to skip the typewriter and advance
- Tap the NPC sprite directly on the map as an alternative to pressing A/B
