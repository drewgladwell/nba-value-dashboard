# 🏀 NBA True Value Dashboard

A single-page analytics dashboard that ranks NBA players by **Box Plus/Minus per $1M of salary** — surfacing who's actually worth their contract.

> Built as a portfolio project for BYU Information Systems

![Dashboard Preview](preview.png)

---

## 🔍 What It Does

Most NBA salary discussions focus on raw stats. This dashboard asks a different question: **how much impact does a player deliver per dollar spent?**

The **Value Score** = `(BPM ÷ Annual Salary in $M) × 10`

A higher score means more on-court impact per dollar. Players on rookie contracts (like Anthony Edwards or Evan Mobley) often top the list precisely because their production far outpaces their pay.

---

## 📊 Features

- **Player search** with live autocomplete
- **Value Score** badge with color-coded grade (Elite → Overpaid)
- **BPM breakdown** — Offensive, Defensive, and Total
- **Progress bars** showing each metric relative to the best in the league
- **Bar chart** per player (Chart.js)
- **Leaderboard** with 4 sortable tabs: Best Value, Off BPM, Def BPM, Total BPM
- **Video background** (drop in your own `background.mp4`)
- Fully responsive — works on mobile

---

## 🚀 Getting Started

No build step required. It's a single HTML file.

```bash
git clone https://github.com/yourusername/nba-value-dashboard.git
cd nba-value-dashboard
open index.html
```

Or just drag `index.html` into your browser.

### Optional: Video Background

Place a video file named `background.mp4` in the root of the project folder. Any basketball highlight reel works well — the video is dimmed to ~18% opacity automatically.

---

## 📁 Project Structure

```
nba-value-dashboard/
├── index.html        # Entire app — HTML, CSS, and JS in one file
├── background.mp4    # (optional) looping background video
├── preview.png       # Screenshot for this README
└── README.md
```

---

## 📦 Dependencies

All loaded via CDN — no `npm install` needed.

| Library | Version | Purpose |
|---|---|---|
| [Chart.js](https://www.chartjs.org/) | 4.4.1 | Bar charts |
| [Barlow / Barlow Condensed](https://fonts.google.com/specimen/Barlow) | — | Typography |
| [DiceBear](https://www.dicebear.com/) | 9.x | Player avatars (seeded by name) |

---

## 📋 Data Sources

| Data | Source | Update frequency |
|---|---|---|
| BPM (Box Plus/Minus) | [Basketball Reference](https://www.basketball-reference.com) | Once per season |
| Salaries | [HoopsHype](https://hoopshype.com/salaries) | Once per season |

Stats reflect the **2024–25 NBA season**. To update for a new season, edit the `PLAYERS` object in `index.html` — it takes about 20 minutes to refresh all values.

---

## 🧮 Methodology

**Box Plus/Minus (BPM)** estimates a player's contribution per 100 possessions relative to a league-average player, using only box score stats. It is not a "catch-all" metric — it doesn't account for minutes played, team context, or injury-shortened seasons.

**Value Score** divides BPM by annual salary (in $M) and scales by 10 for readability. It intentionally favors players on below-market contracts; that's the point.

---

## 🛠️ Customization

Want to tweak the grade thresholds? Edit `getGrade()` in the script:

```js
function getGrade(score) {
  if (score >= 2.0) return { label: 'Elite Value', ... };
  if (score >= 1.2) return { label: 'Great Value', ... };
  if (score >= 0.5) return { label: 'Fair Value',  ... };
  // ...
}
```

Want to add more players? Add an entry to the `PLAYERS` object:

```js
"Player Name": {
  salary: 25.0,        // Annual salary in $M
  team: "Team Name",
  pos: "PG",           // PG | SG | SF | PF | C
  obpm: 3.5,
  dbpm: 0.8,
  bpm:  4.3,
  pts:  22.1,
  ast:  6.0,
  reb:  4.5
},
```

---

## 📝 License

MIT — free to use, modify, and redistribute.

---

*Made with ♥ for BYU IS · Data © Basketball Reference & HoopsHype*
