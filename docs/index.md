# 🔎 Detecting and Analyzing Teamfights in League of Legends

## 📌 Project Overview

Since teamfights often decide the outcome of games, understanding **how**, **when**, and **why** we win or lose them is crucial. This project aims to **automatically identify teamfights** in professional League of Legends matches using GRID data, and **extract actionable insights** to help teams **improve how they fight**. 

Full project repo: XXXXXX
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

Not all fights are created equal.

Once we identify all combat windows, we need to **classify them**:

| Type         | Description                             |
|--------------|-----------------------------------------|
| 🔫 Poke       | Short-range damage before a fight       |
| ⚔️ Skirmish   | 2v2s, 3v3s, etc. (not full teamfights)  |
| 🔄 Trades     | Lane trades or jungle duels             |
| 🧨 Teamfights | 4v4, 5v5 or more, with clear objectives |

For this project, we filter out everything except **true teamfights**, as these are the ones that reveal most about **team coordination, execution, and decision-making**.

## 📊 4. Delivered Analysis

Once we’ve got our teamfights, we can start digging into questions like:

- 🥇 **Are we winning or losing fights overall?**
- 🧭 **How well do we set up beforehand?**
- 🧨 **Who’s engaging and how?**
- 🧯 **How do we use key abilities and summoners?**
- 🎯 **Are we focusing the right targets?**
- ⏱️ **Are we fighting at good timings (tempo, respawn windows)?**

These insights can help coaches and analysts **turn chaotic fights into structured decisions** — with real impact on team performance.

## 📬 5. Feedback & Next Steps

This is just the first iteration — we’d love to hear your ideas!

- What kind of **visualizations or dashboards** would help most?
- Should we analyze **individual roles**, or focus on **team-level patterns**?
- Would you want to compare across **teams or regions**?

👂 Any suggestions or questions? **Reach out or open an issue!** This is an ongoing project, and your input makes it better.

## 🏁 Closing

Teamfights are some of the **most exciting and decisive** moments in League of Legends.

This project aims to make them **measurable, understandable, and improvable** — not just for fans, but for those working to compete at the highest level.

---
