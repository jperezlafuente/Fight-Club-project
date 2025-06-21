# 🧠 FightClub Project — Detecting and Analyzing Teamfights in Pro LoL

📄 **Detailed Article** → [Read the the full documentation here](https://jperezlafuente.github.io/FightClub-project/)

The goal of this project is to automatically identify and reconstruct LOL teamfights using structured in-game data — and extract insights that help teams **understand and improve** their fight execution.

## 🎯 Goal

Build a full pipeline to:

1. 🔍 **Detect fighting windows** using damage, deaths, and ability usage  
2. 🧠 **Expand and reconstruct the fight context** by including all players and relevant moments  
3. ⚔️ **Classify and filter** to focus only on real teamfights (not pokes or trades)  
4. 📊 **Analyze performance** across fights: win rate, decision-making, summoner usage, focus fire, positioning and more  

## 🧠 Methodology

- Use combat spikes to **detect fights**  
- Expand each fight window to **include setup and cleanup** time  
- Define teamfights as events with ≥4 players involved per team  
- Perform **statistical and contextual analysis** of each teamfight instance  

## 💾 Data

This project uses second-by-second structured data from GRID for pro LoL matches. The dataset includes:

- Player positions and movement  
- Damage dealt and taken  
- Ability and summoner usage  
- Kills, assists, deaths  
- Gold, XP, levels and more

## 🧾 Available Resources

- [**teamfights_data_pre.csv**](../data/teamfights_data_pre.csv) → GRID data in a second per second basis
- [**teamfights_data_post.csv**](../data/teamfights_data_post.csv) → Dataset including final fights identified

## 📬 Feedback & Collaboration

If you’ve got ideas, improvements, or questions, feel free to:  
- 📬 Email: [jperezlafuente@hotmail.com](mailto:jperezlafuente@hotmail.com)  
- 🐦 Twitter: [@jperezlafuente](https://twitter.com/jperezlafuente)
