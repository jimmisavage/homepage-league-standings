# ⚽ Cardiff City Standings Viewer

This is a lightweight HTML+JavaScript widget that displays the current Cardfiff City Standings with interactive popups for each team — designed specifically to integrate beautifully with [Homepage](https://gethomepage.dev/) dashboards or any self-hosted portal via iFrame.
This is a personal project that fits to my needs as a Cardiff City fan. It's a 'set and forget' which would follow Cardiff though relegations and promotions and will update logos and input without any tinkering.

This relies on an active API - i use the free account from rapidapi.com / api-football (free 100 API calls per day). With the limited API calls i schedule my updates at every 30 minutes from 13:00. Each run uses 6 API calls. 
Built for speed, simplicity, and a dash of style. This project pulls standings data from a local `standings.json` file and displays:

- A clean scrollable league table
- Team logos and stats
- Recent form (W/D/L)
- Next fixture
- Last season’s finish

### 📸 Popup Features
When you click a team row, a popup displays:

- 🔵 Team logo + name (all caps for max drama)
- 📊 Position, matches played, W/D/L, goals, GD, points
- 📈 Recent form (colour-coded)
- 🎯 Next fixture
- ⬅️ Last season’s finish in the league (e.g. `8th in Championship`)

### 📁 Files
- `index.html` – main UI file (no external dependencies except fonts)
- `data/standings.json` – your League One standings source (expected structure shown below)
- `assets/logos/` – folder for 35x35px team badge images, named as `{team_id}.png`

### 📊 Expected JSON format
The script expects a structure similar to this:
```json
{
  "response": [
    {
      "league": {
        "standings": [
          [
            {
              "team": {
                "id": 123,
                "name": "Cardiff City"
              },
              "rank": 2,
              "points": 42,
              "all": {
                "played": 20,
                "win": 13,
                "draw": 3,
                "lose": 4,
                "goals": {
                  "for": 30,
                  "against": 18
                }
              },
              "form": "WLWWD",
              "nextUp": "Luton (H)",
              "lastSeasonPosition": 8,
              "lastSeasonLeague": "Championship",
              "highlight": true
            }
          ]
        ]
      }
    }
  ]
}
