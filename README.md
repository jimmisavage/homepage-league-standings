# ⚽ Football Standings Viewer

This is a lightweight HTML+JavaScript widget that displays the current League Standings with interactive popups for each team — designed specifically to integrate beautifully with [Homepage](https://gethomepage.dev/) dashboards or any self-hosted portal via iFrame.
This is a personal project that fits to my needs. It's a 'set and forget' which would follow your team though relegations and promotions and will update logos and input without any tinkering.

Default view:
![Screenshot](https://github.com/jimmisavage/homepage-league-standings/raw/main/screenshots/newdefault.JPG)
Popup view:
![Screenshot](https://github.com/jimmisavage/homepage-league-standings/raw/main/screenshots/newpopup.JPG)

# Features
Clean, scrollable league table
Clickable rows with popups for each team
Fast-loading, zero dependencies
Designed for Homepage or iframe embeds

# Popup Details
When you click a team:
Team logo + name
Table position, matches played, W/D/L, goals, goal difference, and points
Recent form (color-coded)
Next fixture
Last season’s league + final rank (e.g. 8th in Championship)

# How to use
1. clone the repo
2. Sign up to https://rapidapi.com/ with the free tier. Add an app (Apps in the top right) for api-football and get your API key.
3. In your github repo go to settings > Secrets and variables > Actions > New repository secret > name: RAPIDAPI_KEY > Key: your api key from step 2.
4. In your github repo go to settings > Pages > Choose you main branch and deploy/save the page. Your page URL will appear at the top of this page (you might need to refresh a couple of times).
5. Back in your repo files go to assets > teamid.txt and edit it to your teams ID. You can find ID's here: https://dashboard.api-football.com/soccer/ids/teams (seperate account/sign in required but it is free).
6. Run actions. Actions > Update Renkings > Rub workflow (wait for the run to finish). Repeat Actions > Update Standings > Rub workflow (wait for the run to finish)
7. In your homepage config file (I have 4 colums) use the following iFrame config:
    - League Table:
         icon: https://github.com/you/homepage-league-standings/blob/main/league-icon.png?raw=true
         widget:
           type: iframe
           name: myIframe
           src: the URL from your Github pages (https://you.github.io/homepage-league-standings)
           classes: h-35

1. Clone this repo

2. Sign up at RapidAPI
   Subscribe to the api-football API (free tier is fine)

3. Add your API key to GitHub secrets
   Go to your repo → Settings → Secrets and variables → Actions
   Add a new secret:
   Name: RAPIDAPI_KEY
   Value: your API key from RapidAPI

4. Enable GitHub Pages
   Go to Settings → Pages, choose your branch (e.g., main) and save
   GitHub will provide a URL (refresh if it doesn’t show right away)

5. Set your team
   Edit assets/teamid.txt and enter your team’s ID from api-football
   (You can find this ID at https://dashboard.api-football.com/soccer/ids/teams)

6. Run the GitHub Actions
   Go to Actions → Update Rankings → Run workflow
   Then do the same for Update Standings
   Wait for each one to finish before running the next

7. Embed in Homepage (example with 4-column layout):
<pre>
  - League Table:
      icon: https://github.com/YOU/homepage-league-standings/blob/main/league-icon.png?raw=true
      widget:
        type: iframe
        name: myIframe
        src: https://YOU.github.io/homepage-league-standings
        classes: h-35
</pre>
*Replace YOU with your GitHub username.

# Notes
Built for speed, simplicity, and a touch of style.
Designed to be low maintenance: just set your team and let it ride.
API rate limits are respected by default — so it won’t burn through your quota.

# Added calendar .iso for team fixtures
I've also added an calendar .iso so you can list your teams fixtures in a calendar view
You can use this in homepage or google calendar (i've not tested other apps but they should work)
Fixtures.ics can be found in public/cal/fixtures.ics. To access from external apps use https://<yourusername>.github.io/homepage-league-standings/public/cal/fixtures.ics

An example homepage services.yml
<pre>
  - League Table:
    - Cardiff City:
        icon: https://upload.wikimedia.org/wikipedia/en/thumb/3/3c/Cardiff_City_crest.svg/1200px-Cardiff_City_crest.svg.png
        widget:
          type: calendar
          view: agenda
          maxEvents: 6 
          showTime: true 
          previousDays: 10 
          integrations: 
            - type: ical 
              url: https://YOU.github.io/homepage-league-standings/public/cal/fixtures.ics
              color: blue
              params: 
                showName: false
</pre>
*Replace YOU with your GitHub username.
