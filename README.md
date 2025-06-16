# ⚽ Football Standings Viewer

This is a lightweight HTML+JavaScript widget that displays the current League Standings with interactive popups for each team — designed specifically to integrate beautifully with [Homepage](https://gethomepage.dev/) dashboards or any self-hosted portal via iFrame.
This is a personal project that fits to my needs. It's a 'set and forget' which would follow your team though relegations and promotions and will update logos and input without any tinkering.

This relies on an active API - i use the free account from rapidapi.com / api-football (free 100 API calls per day). With the limited API calls i schedule my updates every 30 minutes during match times. Each run uses 2 API calls (with an extra 3 calls each day to cache data). 
Built for speed, simplicity, and a dash of style. This project pulls standings data from a local `standings.json` file and displays:

- A clean scrollable league table

### 📸 Popup Features
When you click a team row, a popup displays:

- 🔵 Team logo + name
- 📊 Position, matches played, W/D/L, goals, GD and points
- 📈 Recent form (colour-coded)
- 🎯 Next fixture
- ⬅️ Last season’s finish in the league (e.g. `8th in Championship`)

# ⚽ How to use

1. clone the repo
2. Sign up to https://rapidapi.com/ with the free tier. Add an app (Apps in the top right) for api-football and get your API key.
3. In your github repo go to settings > Secrets and variables > Actions > New repository secret > name: RAPIDAPI_KEY > Key: your api key from step 2.
4. In your github repo go to settings > Pages > Choose you main branch and deploy/save the page. Your page URL will appear at the top of this page (you might need to refresh a couple of times).
5. Back in your repo files go to assets > teamid.txt and edit it to your teams ID from https://rapidapi.com / api-football.
6. Run actions. Actions > Update Renkings > Rub workflow (wait for the run to finish). Repeat Actions > Update Standings > Rub workflow (wait for the run to finish)
7. In your homepage config file (I have 4 colums) use the following iFrame config:
    - League Table:
         icon: https://github.com/you/homepage-league-standings/blob/main/league-icon.png?raw=true
         widget:
           type: iframe
           name: myIframe
           src: the URL from your Github pages (https://you.github.io/homepage-league-standings)
           classes: h-35

