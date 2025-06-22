# 🔎 Detecting and Analyzing Teamfights in League of Legends

## 📌 Project Overview

Since teamfights often decide the outcome of games, understanding **how**, **when**, and **why** we win or lose them is crucial. This project aims to **automatically identify teamfights** in professional League of Legends matches using GRID data, and **extract actionable insights** to help teams **improve how they fight**. 

Full project repo: [https://github.com/jperezlafuente/FightClub-project](https://github.com/jperezlafuente/FightClub-project)

---

## 🗂️ 1. Available Data

Using the data available at **GRID**, the official League of Legends data provider, we have **second-by-second** data from all 10 players for every competitive match. This includes valuable info from champ stats, game stats, positions, spells usage and much more. As for this project, we will focus on the relevant variables to identify fighting moments, which includes:

- 📍 Player positions (X/Y coordinates)
- 💥 Damage dealt and received
- 🧙 Abilities and summoner spell usage
- 🛡️ Shields, healing, and CC
- 💀 Kills, deaths, assists
- 💰 Gold, level, XP and others

By combining these variables properly we will try to look for the game situations where we could say there is a teamfight.

## 🧩 2. The Challenge: What is a teamfight?

Every League of Legends professional would agree on any game situation being a teamfight or not. It's not even difficult. In fact, it's easier than trying to define it in words. I'll try anyway:

We could define a teamfight as a game moment where an important number of players from both teams are gathered at some point in the map trying to fight for an objective-kills-position, dealing effective damage to the opponents and, generally, leading to some kills. It's not enough to look at gathered players, damage dealt or kills separately. It's a combination from these elements what defines a teamfight.

What is really simple to identify from a video or an image, it's not that easy to do on detailed data like the one we have on GRID. That's why I'm going to divide the task in two steps where I'll look for different data processing:

✅ **Step 1: Detecting and delimiting fighting events**
- Look for spikes in damage, deaths, and activity
- Identify and save the timeframes and map coordinates where those spikes appear

⚠️ **Step 2: Rebuilding the full teamfight**
- Expand player participation beyond just those who dealt/received damage
- Include all relevant timestamps for each participant in the teamfight
- Define consistent start and end points for the fight window
- Cluster fights and cut global fighting moments into unique fighting events

This second part is especially tricky — teamfights are **messy, dynamic, and fluid**. The goal is to capture the full picture.

Summing things up, my approach is to start from easy-to-identify spikes in damage or kill events. Should you stop at this while filtering match data, you would be looking at a very short table where some players didn't even have the opportunity to deal damage during the fight. Also, most importantly, you would be missing every second players where on the fight without hitting enemies (which is the main part of the fight since they will be clicking to move and kite enemy spells or just get closer to them). So, I'm using this just to obtain the timestamps and positions where these events happen (setting some positional and temporal thresholds) and then I look for the larger amount of data surrounding those timestamps and locations in map. Final step is to just cut the resulting data into different fights and assigning ids to them.

## 🧠 3. Types of Fights

From previous step we now have a lot of unique fighting events. All of them are based on timeframes and positions, but we also have things like number of players involved, amount of damage dealt, kills-deaths-assists, gold differences and more. So once we identify all combat windows, we need to use this info to **classify them**. For example, we could find types like:

| Type         | Description                             |
|--------------|-----------------------------------------|
| 🔫 Poke       | Short-range damage before a fight       |
| ⚔️ Skirmish   | 2v2s, 3v3s, etc. (not full teamfights)  |
| 🔄 Trades     | Lane trades or jungle duels             |
| 🧨 Teamfights | 4v4, 5v5 or more, with clear objectives |

For this project, we filter out everything except **true teamfights**, as these are the ones we will focus. Again, we will need to set some thresholds to delimitate them. My decision was to relay mainly on: **minimum number of players involved, damage dealt as a percentage of total health in game** and, also, **kills**. 

## 📊 4. Delivered Analysis

Once we’ve got our teamfights, we can start digging into questions like:

- 🥇 **Are we winning or losing fights overall?**
- 🧭 **Do we perform better/worst teamfights in mid game or in late game?**
- 🛠️ **How well do we set up beforehand?**
- 🎯 **Are we focusing the right targets?**
- ⏱️ **Are we fighting at good timings (tempo, respawn windows)?**

These insights can help coaches and analysts **turn chaotic fights into structured decisions** — with real impact on team performance. Each of them could properly have its own specific post so I won't detail them at the moment. But one thing to note is that **only identifying teamfights is useful enough for coaches and analysts because of the time saving we are delivering**. And this is even more important if you take into account that some of the things you would want to look in teamfights are not really easy to objectively analyse (for example: shotcalling, spell combos and priorities...), so personal analysis should appear at some point anyway. But here we can set some valuable guidelines and shortcuts for them. 

## 📊 Sample Data

In the repository of the project you can find an example from 5 Spanish ERL1 matches so that you can better understand the data available to do this analysis. In addition, I've added the sample result from this approach to identify fights from those matches.

- [**teamfights_data_pre.csv**](https://github.com/jperezlafuente/FightClub-project/tree/main/data) → CSV containing selected GRID data from those matches in a second per second basis.
- [**teamfights_data_post.csv**](https://github.com/jperezlafuente/FightClub-project/tree/main/data) → CSV containing final fights identified according to this process and my temporal/spatial thresholds.

## 📬 Feedback & Next Steps

I invite the community to explore the results and help find new ways to leverage this data. Some possible areas of interest include:
- **Improving any step from the process**, specially setting solid thresholds to determine whether a player is a real part of the fight or not.
- **Determine solid criteria to clasify more fighting types apart from teamfights**
- **Suggest and develop any KPI/insights from this data**

## 📢 Contact & Contributions
This project is shared for analytical and discussion purposes. If you have insights or ideas to expand the analysis, feel free to open a discussion or reach out ([Twitter: @jperezlafuente](https://twitter.com/jperezlafuente), [email](mailto:jperezlafuente@hotmail.com))!

Even though I shared the complete logic detail of the process, I had not shared the exact thresholds and ways of using the variables available to create fighting events for competitive reasons. Nevertheless, I'm open to talk directly to anyone interested in these type of details and help them to recreate this kind of result.

Finally, I would like to thank my actual coaching staff in ZETA, Sangui and Inori, for suggesting this analysis, checking my results and giving me the freedom to explore new things like this.

---
