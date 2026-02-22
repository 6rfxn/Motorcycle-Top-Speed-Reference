# 🏍️ EXRGarage — Motorcycle Top Speed Reference

Interactive tools and reference guides for the EXRGarage motorcycle chassis on Roblox.

🔗 **Live Site:** [https://6rfxn.github.io/The-Ride-Tools/](https://6rfxn.github.io/The-Ride-Tools/)

---

## What's Inside

### Tools
| Tool | Description |
|---|---|
| [Gear Ratio Calculator](https://6rfxn.github.io/The-Ride-Tools/tools/gear-ratio-calculator.html) | Generate smooth gear ratios with adjustable bias, preview spacing visually, and copy Lua output directly into your Tune script. |

### Guides
| Guide | Description |
|---|---|
| [Top Speed Reference](https://6rfxn.github.io/The-Ride-Tools/guides/top-speed-reference.html) | Real-world speed, power, and acceleration data for 250cc, 600cc, and 1000cc motorcycles. Interactive tables with bar charts. |
| [Tuning Guide](https://6rfxn.github.io/The-Ride-Tools/guides/tuning-guide.html) | How to configure the Tune script — engine, gearing, suspension, brakes, steering, and driving aids. |
| [Customization Guide](https://6rfxn.github.io/The-Ride-Tools/guides/customization-guide.html) | How the upgrade system works — lookup tables, defaults, data flow, and step-by-step instructions for adding new stats. |
| [2-Stroke vs 4-Stroke](https://6rfxn.github.io/The-Ride-Tools/guides/2t-vs-4t.html) | Speed, power, and weight differences between 2T and 4T engines across all displacements. Includes tuning tips. |

---

## Quick Reference — Top Speeds

### 250cc
| Type | 4-Stroke | 2-Stroke |
|---|---|---|
| Stock | 150–170 km/h | — |
| Street | 160–180 km/h | 175–195 km/h |
| Racing | 180–200 km/h | 195–220 km/h |
| Endurance | 170–190 km/h | 185–210 km/h |
| Drag | 190–220 km/h | 220–250 km/h |

### 600cc
| Type | 4-Stroke | 2-Stroke |
|---|---|---|
| Stock | 200–220 km/h | — |
| Street | 220–240 km/h | — |
| Racing | 250–270 km/h | 280–310 km/h |
| Endurance | 240–260 km/h | 270–300 km/h |
| Drag | 260–290 km/h | 310–350+ km/h |

### 1000cc
| Type | 4-Stroke | 2-Stroke |
|---|---|---|
| Stock | 230–260 km/h | — |
| Street | 250–280 km/h | — |
| Racing | 300–330 km/h | 320–360 km/h |
| Endurance | 280–310 km/h | — |
| Drag | 310–350+ km/h | 350+ km/h |

---

## File Structure

```
The-Ride-Tools/
├── README.md
└── docs/
    ├── index.html                          ← Landing page
    ├── tools/
    │   └── gear-ratio-calculator.html      ← Gear ratio tool
    └── guides/
        ├── top-speed-reference.html        ← Speed/power data tables
        ├── tuning-guide.html               ← Tune script walkthrough
        ├── customization-guide.html        ← Upgrade system docs
        └── 2t-vs-4t.html                  ← Engine type comparison
```

---

## GitHub Pages Setup

1. Push the `docs/` folder to your `main` branch
2. Go to **Settings → Pages**
3. Set source to branch `main`, folder `/docs`
4. Save — site goes live in ~1 minute

---

## Adding New Pages

1. Create a new `.html` file in `docs/tools/` or `docs/guides/`
2. Add a card link in `docs/index.html` under the appropriate section
3. Push to `main` — auto-deploys

---

## For Developers

The EXRGarage chassis uses two main scripts:

- **Customization Module** — Loads player upgrade data from Attributes, converts levels to values via lookup tables
- **Tune Script** — Central config for all bike physics: weight, tires, suspension, engine, gearing, brakes, driving aids

```lua
-- In the Tune script:
local Module = require(script.Customization)
Module:LoadData()
Tune.Data = Module:GetResolved()

-- Then use resolved values:
Tune.Horsepower = 90 * 2 + Tune.Data.Horsepower
Tune.FTireFriction = Tune.Data.TireGrip
Tune.SpeedLimit = Tune.Data.MaxSpeed
```

See the [Customization Guide](https://6rfxn.github.io/The-Ride-Tools/guides/customization-guide.html) for full documentation on adding new upgrade stats.

---

**Last Updated:** February 22, 2026
