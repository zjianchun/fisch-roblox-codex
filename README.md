# 🐟 Fisch Roblox Open Codex & Dataset

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Companion: GameIndex](https://img.shields.io/badge/Companion-GameIndex%20Wiki-0891b2)](https://gameindex.wiki/games/fisch/)
[![Data: Verified](https://img.shields.io/badge/Data-Verified%20Patch%20Stats-emerald)](https://gameindex.wiki/games/fisch/)

An open, verified database and parameter compendium for **Roblox Fisch** (developed by WoozyNate / Fisching). This repository hosts clean, structured JSON datasets for all fishing rods, mutation value multipliers, bestiary records, and money farming routes.

---

## 🌐 Official Web Companion

For an ad-free, interactive browsing experience with real-time stat filters and gear calculators, visit the live web companion:

👉 **[GameIndex Fisch Companion & Database](https://gameindex.wiki/games/fisch/)**

### Key Strategy & Progression Guides
- **[Fisch Fishing Rod Tier List & Stats Database](https://gameindex.wiki/games/fisch/guides/fisch-rod-tier-list/)** — Verified stats across all 18 rods (Lure Speed, Luck, Resilience, Control, and Max Weight).
- **[All Mutations & Sell Value Multipliers Guide](https://gameindex.wiki/games/fisch/guides/fisch-mutations-guide/)** — Complete mutation formulas, appraisal mechanics, and pricing multipliers.
- **[Best Money Farming Locations & Routes](https://gameindex.wiki/games/fisch/guides/fisch-money-farming-locations-guide/)** — Optimal C$/hr farming spots from Moosewood starter waters to the Sunken Depths.
- **[Whale Shark Hunts & Migration Tracking](https://gameindex.wiki/games/fisch/guides/fisch-whale-shark-hunts-guide/)** — Spawn timers, bait requirements, and catch mechanics for apex sea events.
- **[Bestiary Completion & Weather Requirements](https://gameindex.wiki/games/fisch/guides/fisch-bestiary-completion-guide/)** — Weather, day/night cycles, bait preferences, and zone checklists for 100% completion.

---

## 📊 Fishing Rod Parameter Compendium

Below is the verified core stat matrix for primary progression rods in *Fisch*:

| Rod Name | Tier | Price (C$) | Lure Speed | Luck | Resilience | Max Weight | Unlock Location |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **Flimsy Rod** | F | Free | 0% | 0% | 0% | 10.4 kg | Moosewood (Marc's starter shop) |
| **Training Rod** | D | 300 | +10% | +5% | +5% | 20.0 kg | Moosewood Village |
| **Plastic Rod** | D | 900 | +15% | +10% | +5% | 50.0 kg | Moosewood Dock |
| **Carbon Rod** | B | 2,000 | +15% | +25% | +10% | 600.0 kg | Moosewood Village Merchant |
| **Fast Rod** | C | 4,500 | +55% | -10% | +5% | 120.0 kg | Roslit Bay |
| **Lucky Rod** | C | 5,250 | -30% | +60% | +10% | 180.0 kg | Roslit Bay |
| **Steady Rod** | B | 7,000 | +20% | +35% | +40% | 10,000.0 kg | Roslit Volcano / Merchant |
| **Fortune Rod** | A | 12,500 | +30% | +110% | +15% | 750.0 kg | Roslit Bay Hidden Cave |
| **Rapid Rod** | B | 14,000 | +80% | +15% | +10% | 500.0 kg | Sunstone Island |
| **Magnet Rod** | B | 15,000 | +25% | +20% | +25% | 1,200.0 kg | Terrapin Island |
| **Nocturnal Rod** | A | 11,000 | +35% | +50% | +20% | 2,000.0 kg | Vertigo Pit (Night bonus) |
| **Magma Rod** | A | Quest | +30% | +45% | +30% | 1,500.0 kg | Roslit Volcano (Catches in lava) |
| **Fungal Rod** | A | Quest | +40% | +45% | +20% | 150.0 kg | Mushgrove Swamp Alligator Quest |
| **Destiny Rod** | S | 190,000 | +45% | +250% | +30% | 7,000.0 kg | Caleia / The Arch |
| **Rod of the Depths** | S | Hexed Quest | +65% | +130% | +45% | Infinity | The Depths (Endgame) |

---

## 🧬 Mutation Value Multipliers

Mutations multiply the base selling price of any caught fish when appraised or sold to merchants:

| Mutation Archetype | Price Multiplier | Visual Effect | Optimal Gear Synergy |
| :--- | :---: | :--- | :--- |
| **Shiny** | **1.85x** | Sparkling glitter particle aura | Carbon Rod / Fortune Rod |
| **Sparkling** | **1.90x** | Continuous starburst sparks | Fortune Rod |
| **Albino** | **2.10x** | Pure white skin overlay | Lucky Rod / Fortune Rod |
| **Electric** | **2.40x** | Blue/yellow lightning arcing | Stormy weather + Magnet Rod |
| **Dark / Abyssal** | **2.80x** | Pitch black void aura with shadowy trail | Nocturnal Rod / Depths Rod |
| **Mythical** | **4.50x** | Chromatic iridescent particle wave | Destiny Rod |
| **Translucent** | **5.00x** | Glass-like refraction shader | Aurora Bobber + Destiny Rod |
| **Fungal** | **4.00x** | Spore cloud emitter | Fungal Rod passive (+30% proc) |

---

## 📦 Dataset Structure

The raw, structured JSON dataset is available under [`data/items.json`](data/items.json):

```typescript
interface FischItem {
  id: string;
  name: string;
  category: "Fishing Rods" | "Fish" | "Baits" | "Bobbers";
  tier: "F" | "D" | "C" | "B" | "A" | "S";
  price_c: number;
  lure_speed_pct: number;
  luck_pct: number;
  control: number;
  resilience_pct: number;
  max_weight_kg: number;
  location: string;
  stats: Record<string, string>;
  description: string;
}
```

### Usage Example (Node.js / Python)

```javascript
import fs from 'node:fs';

const items = JSON.parse(fs.readFileSync('./data/items.json', 'utf-8'));
const topTierRods = items.filter(item => item.tier === 'S' || item.tier === 'A');
console.log(`Loaded ${topTierRods.length} high-tier rods`);
```

```python
import json

with open("data/items.json", "r", encoding="utf-8") as f:
    items = json.load(f)

for item in items:
    if "Rod" in item.get("name", ""):
        print(f"{item['name']}: {item.get('price_c', 0)} C$")
```

---

## 🤝 Contributing

Contributions, stat balance reports, and new patch verifications are welcome! Please open an issue or pull request, or check the [GameIndex Fisch Wiki](https://gameindex.wiki/games/fisch/) for the latest live updates.

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.
