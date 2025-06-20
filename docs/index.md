# 🔎 Detecting and Analyzing Teamfights in League of Legends

## 🎯 General Objective

Our goal is simple: **automatically identify teamfights** in professional League of Legends matches using GRID data, and **extract actionable insights** to help teams **improve how they fight**.

Teamfights often decide the outcome of games — understanding **how**, **when**, and **why** we win or lose them is crucial.

---

## 🗂️ Available Data

Thanks to **GRID**, we have **second-by-second** data from all 10 players for every competitive match. That includes:

- 📍 Player positions (X/Y coordinates)
- 💥 Damage dealt and received
- 🧙 Ability and summoner spell usage
- 🛡️ Shields, healing, and CC
- 💀 Kills, deaths, assists
- 💰 Gold, level, and XP

This allows us to reconstruct every moment of the game with high granularity.

---

## 🧩 Main Challenge

The big challenge isn't just detecting fights — it's **representing them properly**.

✅ **Step 1: Detecting fights**
- Look for spikes in damage, deaths, and activity
- Cluster those spikes to find candidate fights

⚠️ **Step 2: Rebuilding the full teamfight**
- Include pre-fight setup and post-fight cleanups
- Expand participation beyond just those who dealt/received damage
- Define consistent start and end points for the fight window

This second part is especially tricky — teamfights are **messy, dynamic, and fluid**. The goal is to capture the full picture.

---

## 🧠 Types of Fights

Not all fights are created equal.

Once we identify all combat windows, we need to **classify them**:

| Type         | Description                             |
|--------------|-----------------------------------------|
| 🔫 Poke       | Short-range damage before a fight       |
| ⚔️ Skirmish   | 2v2s, 3v3s, etc. (not full teamfights)  |
| 🔄 Trades     | Lane trades or jungle duels             |
| 🧨 Teamfights | 4v4, 5v5 or more, with clear objectives |

For this project, we filter out everything except **true teamfights**, as these are the ones that reveal most about **team coordination, execution, and decision-making**.

---

## 📊 Delivered Analysis

Once we’ve got our teamfights, we can start digging into questions like:

- 🥇 **Are we winning or losing fights overall?**
- 🧭 **How well do we set up beforehand?**
- 🧨 **Who’s engaging and how?**
- 🧯 **How do we use key abilities and summoners?**
- 🎯 **Are we focusing the right targets?**
- ⏱️ **Are we fighting at good timings (tempo, respawn windows)?**

These insights can help coaches and analysts **turn chaotic fights into structured decisions** — with real impact on team performance.

---

## 📬 Feedback & Next Steps

This is just the first iteration — we’d love to hear your ideas!

- What kind of **visualizations or dashboards** would help most?
- Should we analyze **individual roles**, or focus on **team-level patterns**?
- Would you want to compare across **teams or regions**?

👂 Any suggestions or questions? **Reach out or open an issue!** This is an ongoing project, and your input makes it better.

---

## 🏁 Closing

Teamfights are some of the **most exciting and decisive** moments in League of Legends.

This project aims to make them **measurable, understandable, and improvable** — not just for fans, but for those working to compete at the highest level.

---
